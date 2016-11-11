---
title: Etapa 3 Configurar o SQL
description: "Prepare o domínio CORP com identidades novas ou existentes para serem gerenciadas pelo Privileged Identity Manager usando scripts"
keywords: 
author: barclayn
ms.author: barclayn
manager: MBaldwin
ms.date: 10/25/2016
ms.topic: article
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 365989693f844f117f76ee2b69db85df82f06f35
ms.openlocfilehash: 375a34e5255c90559fc0ffb3a80fc7c92ebd27a2


---
# <a name="step-3-configuring-sql"></a>Etapa 3 Configurar o SQL

>[!div class="step-by-step"]
[« Etapa 2](sp1-step2-configuring-corp-domain.md)
[Etapa 4 »](sp1-step4-configuring-sharepoint.md)

Antes de você prosseguir com as próximas etapas, certifique-se de que esteja usando o SQL Server 2012 SP1 ou posterior, ou o SQL server 2014. Para servidores ingressados em um domínio, faça logon usando a conta MIMAdmin, caso contrário, faça logon como administrador local
1. Execute o PowerShell como administrador
2. cd $env:SYSTEMDRIVE\PAM
3. .\PAMDeployment.ps1
4. Selecione a opção 3 do Menu (Configuração do SQL Server)

  Se o servidor ainda não estiver ingressado no domínio PRIV, ele solicitará as credenciais e ingressará o servidor no domínio.
  Depois de ingressar no domínio, o computador será reinicializado. Após a reinicialização, faça logon no servidor com a conta MIMAdmin.

1. Execute o PowerShell como administrador
2. cd $env:SYSTEMDRIVE\PAM
3. .\PAMDeployment.ps1
4. Selecione a opção 3 do Menu (Configuração do SQL Server)

Quando solicitado, forneça a senha para a conta de serviço MIMAdmin e permita que a instalação continue. Após a conclusão, vá para a etapa 4.

>[!div class="step-by-step"]
[« Etapa 2](sp1-step2-configuring-corp-domain.md)
[Etapa 4 »](sp1-step4-configuring-sharepoint.md)



<!--HONumber=Nov16_HO2-->


