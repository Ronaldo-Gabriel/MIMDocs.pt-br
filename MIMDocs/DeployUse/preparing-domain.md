---
# required metadata

title: Configuração de um domínio | Microsoft Identity Manager
description: Crie um controlador de domínio do Active Directory antes de instalar o MIM 2016
keywords:
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 50345fda-56d7-4b6e-a861-f49ff90a8376

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mwahl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure um nome de domínio

>[!div class="step-by-step"]  
[Windows Server 2012 R2 »](prepare-server-ws2012r2.md)

## Crie contas de usuários e grupos

O MIM requer que o Active Directory já esteja instalado. Verifique se que você tem um controlador de domínio em seu ambiente para um domínio que você possa administrar.

> [!NOTE]
> Em todos os exemplos a seguir, **mimservername** representa o nome do controlador de domínio, **contoso** representa o nome do domínio e **Pass@word1** representa uma senha de exemplo.

1. Entre no controlador de domínio como o Administrator do domínio com a senha (*e. g. Contoso\Administrador*).

2. Crie as seguintes contas de usuário para serviços do MIM. Inicie o PowerShell e digite o script a seguir para atualizar o domínio.

        ```
        import-module activedirectory
        $sp = ConvertTo-SecureString "Pass@word1" –asplaintext –force
        New-ADUser –SamAccountName MIMMA –name MIMMA
        Set-ADAccountPassword –identity MIMMA –NewPassword $sp
        Set-ADUser –identity MIMMA –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMSync –name MIMSync
        Set-ADAccountPassword –identity MIMSync –NewPassword $sp
        Set-ADUser –identity MIMSync –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMService –name MIMService
        Set-ADAccountPassword –identity MIMService –NewPassword $sp
        Set-ADUser –identity MIMService –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName MIMSSPR –name MIMSSPR
        Set-ADAccountPassword –identity MIMSSPR –NewPassword $sp
        Set-ADUser –identity MIMSSPR –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName SharePoint –name SharePoint
        Set-ADAccountPassword –identity SharePoint –NewPassword $sp
        Set-ADUser –identity SharePoint –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName SqlServer –name SqlServer
        Set-ADAccountPassword –identity SqlServer –NewPassword $sp
        Set-ADUser –identity SqlServer –Enabled 1 –PasswordNeverExpires 1
        New-ADUser –SamAccountName BackupAdmin –name BackupAdmin
        Set-ADAccountPassword –identity BackupAdmin –NewPassword $sp
        Set-ADUser –identity BackupAdmin –Enabled 1 -PasswordNeverExpires 1
        ```

2.  Crie grupos de segurança para todos os grupos.

    ```
    New-ADGroup –name MIMSyncAdmins –GroupCategory Security –GroupScope Global      –SamAccountName MIMSyncAdmins
    New-ADGroup –name MIMSyncOperators –GroupCategory Security –GroupScope Global       –SamAccountName MIMSyncOperators
    New-ADGroup –name MIMSyncJoiners –GroupCategory Security –GroupScope Global         –SamAccountName MIMSyncJoiners
    New-ADGroup –name MIMSyncBrowse –GroupCategory Security –GroupScope Global      –SamAccountName MIMSyncBrowse
    New-ADGroup –name MIMSyncPasswordReset –GroupCategory Security –GroupScope Global          –SamAccountName MIMSyncPasswordReset
    Add-ADGroupMember -identity MIMSyncAdmins -Members Administrator
    Add-ADGroupmember -identity MIMSyncAdmins -Members MIMService
    ```

3.  Adicione os SPNs (Nomes da Entidade de Serviço) para habilitar a autenticação Kerberos para contas de serviço

    ```
    setspn -S http/mimservername.contoso.local Contoso\SharePoint
    setspn -S http/mimservername Contoso\SharePoint
    setspn -S MIMService/mimservername.contoso.local Contoso\MIMService
    setspn -S MIMSync/mimservername.contoso.local Contoso\MIMSync
    ```

>[!div class="step-by-step"]  
[Windows Server 2012 R2 »](prepare-server-ws2012r2.md)


<!--HONumber=Apr16_HO2-->


