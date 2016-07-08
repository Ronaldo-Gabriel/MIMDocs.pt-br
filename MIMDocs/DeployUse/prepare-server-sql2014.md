---
title: "Configuração de um servidor de gerenciamento de identidade&"
description: "Instale o SQL Server 2014 durante a preparação para a instalação do MIM 2016."
keywords: 
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 297df3b3-192e-4ed9-82ed-c95eb5297c84
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c023d147d0fcc1525fefbe866c952e217f7bee6b
ms.openlocfilehash: 2c0ff0bdbba4bcf979def8d5c7aa381947d6cc87


---

# Configure um servidor de gerenciamento de identidade: SQL Server 2014

>[!div class="step-by-step"]
[« Windows Server 2012 R2](prepare-server-ws2012r2.md)
[SharePoint »](prepare-server-sharepoint.md)

> [!NOTE]
> Este passo a passo usa nomes e valores de exemplo de uma empresa chamada Contoso. Substitua-os pelos seus próprios valores. Por exemplo:
> - Nome do controlador de domínio - **mimservername**
> - Nome do domínio - **contoso**
> - Senha - **Pass@word1**

## Instale o **SQL Server 2014 Standard Edition**

1. Inicie o **PowerShell** como um administrador de domínio.

2. Altere para o diretório em que o programa de instalação do SQL Server está localizado.

3. Digite os seguintes comandos.

    ```
    .\setup.exe /Q /IACCEPTSQLSERVERLICENSETERMS /ACTION=install /FEATURES=SQL,SSMS /INSTANCENAME=MSSQLSERVER /SQLSVCACCOUNT="contoso\SqlServer" /SQLSVCPASSWORD="Pass@word1"   /AGTSVCSTARTUPTYPE=Automatic /AGTSVCACCOUNT="NT AUTHORITY\Network Service" /SQLSYSADMINACCOUNTS="contoso\Administrator"
    ```

>[!div class="step-by-step"]  
[« Windows Server 2012 R2](prepare-server-ws2012r2.md)
[SharePoint »](prepare-server-sharepoint.md)



<!--HONumber=Jun16_HO4-->


