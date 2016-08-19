---
title: Configurar o Windows Server | Microsoft Identity Manager
description: "Obtenha as etapas e os requisitos mínimos para preparar o Windows Server 2012 RS para trabalhar com o MIM 2016."
keywords: 
author: kgremban
manager: femila
ms.date: 07/21/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 51507d0a-2aeb-4cfd-a642-7c71e666d6cd
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b3ab1b9376c9b613739d87c812f4b16a4e17e6de
ms.openlocfilehash: e1d69eb7946f9adfdfa7c55cecd3fa1d799a2cd3


---

# Configure um servidor de gerenciamento de identidade: Windows Server 2012 R2

>[!div class="step-by-step"]
[« Preparando um domínio](preparing-domain.md)
[SQL Server 2014 »](prepare-server-sql2014.md)

> [!NOTE]
> Este passo a passo usa nomes e valores de exemplo de uma empresa chamada Contoso. Substitua-os pelos seus próprios valores. Por exemplo:
> - Nome do controlador de domínio - **mimservername**
> - Nome do domínio - **contoso**
> - Senha - **Pass@word1**

## Adicione o Windows Server 2012 R2 ao domínio

Comece com um computador Windows Server 2012 R2 com um mínimo de 8 GB de RAM. Ao instalar, especifique a edição "Windows Server 2012 R2 Standard (servidor com GUI) x64".

1. Faça logon no novo computador como administrador.

2. Usando o painel de controle, dê ao computador um endereço IP estático em uma rede. Configure essa interface de rede para enviar consultas DNS para o endereço IP do controlador de domínio na etapa anterior e defina o nome do computador para **CORPIDM**.  Isso exigirá reinicializar o servidor.

3. Abra o painel de controle e ingresse o computador no domínio que você configurou na última etapa, *contoso.local*.  Isso inclui fornecer o nome de usuário e s credenciais de um administrador de domínio, tal como *Contoso\Administrador*.  Depois que a mensagem de boas-vindas for exibida, feche a caixa de diálogo e reinicie o servidor novamente.

4. Entre no computador *CorpIDM* como um administrador de domínio, tal como *Contoso\Administrador*.

5. Inicie uma janela do PowerShell como administrador e digite o seguinte comando para atualizar o computador com as configurações da política de grupo.

    ```
    gpupdate /force /target:computer
    ```

    Após não mais que minuto, será concluído com a mensagem "A atualização da política do computador foi concluída com sucesso".

6. Adicione as funções **Servidor Web (IIS)** e **Servidor de Aplicativos**, os recursos **.NET Framework** 3.5, 4.0 e 4.5 e o módulo **Active Directory** para o Windows PowerShell.

    ![Imagem de recursos do PowerShell](media/MIM-DeployWS2.png)

7. No PowerShell, digite os comandos a seguir. Observe que talvez seja necessário especificar um local diferente para os arquivos de origem para os recursos do **.NET Framework** 3.5. Normalmente, esses recursos não estão presentes no momento da instalação do Windows Server, mas estão disponíveis na pasta SxS (lado a lado) na pasta de origens do disco de instalação do sistema operacional, por exemplo, “*d:\Sources\SxS\*”.

    ```
    import-module ServerManager
    Install-WindowsFeature Web-WebServer, Net-Framework-Features,rsat-ad-powershell,Web-Mgmt-Tools,Application-Server,Windows-Identity-Foundation,Server-Media-Foundation,Xps-Viewer –includeallsubfeature -restart -source d:\sources\SxS
    ```

## Configurar a política de segurança do servidor

Configure a política de segurança do servidor para permitir que as contas criadas recentemente sejam executadas como serviço.

1. Inicie o programa de Política de Segurança Local

2. Navegue até **Políticas Locais > Atribuição de Direitos do Usuário**.

3. No painel de detalhes, clique com o botão direito do mouse em **Fazer logon como um serviço**e selecione **Propriedades**.

    ![Imagem de política de segurança local](media/MIM-DeployWS3.png)

4. Clique em **Adicionar Usuário ou Grupo** e na caixa de texto digite `contoso\mimsync; contoso\mimma; contoso\MIMService; contoso\SharePoint; contoso\SqlServer; contoso\mimsspr`, clique em **Verificar Nomes** e clique em **OK**.

5. Clique em **OK** para fechar a janela **Propriedades de Logon como um serviço**.

6.  No painel de detalhes, clique com o botão direito do mouse em **Negar acesso a este computador pela rede**e selecione **Propriedades**.

7. Clique em **Adicionar Usuário ou Grupo** e na caixa de texto digite `contoso\MIMSync; contoso\MIMService` e clique em **OK**.

8. Clique em **OK** para fechar a janela **Negar acesso a este computador das Propriedades de rede**.

9. No painel de detalhes, clique com o botão direito do mouse em **Negar logon localmente** e selecione **Propriedades**.

10. Clique em **Adicionar Usuário ou Grupo** e na caixa de texto digite `contoso\MIMSync; contoso\MIMService` e clique em **OK**.

11. Clique em **OK** para fechar a janela **Negar logon em Propriedades locais**.

12. Feche a janela de Política de Segurança Local.


## Altere o Modo de autenticação do Windows do IIS

1.  Abra uma janela do PowerShell.

2.  Pare o IIS com o comando *iisreset /STOP*

    ```
    iisreset /STOP
    C:\Windows\System32\inetsrv\appcmd.exe unlock config /section:windowsAuthentication -commit:apphost
    iisreset /START
    ```

>[!div class="step-by-step"]  
[« Preparando um domínio](preparing-domain.md)
[SQL Server 2014 »](prepare-server-sql2014.md)



<!--HONumber=Jul16_HO3-->


