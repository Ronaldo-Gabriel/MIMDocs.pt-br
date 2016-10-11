---
title: Etapa 5 Instalar/configurar o PAM
description: "Prepare o domínio CORP com identidades novas ou existentes para serem gerenciadas pelo Privileged Identity Manager usando scripts"
keywords: 
author: barclayn
manager: MBaldwin
ms.date: 09/26/2016
ms.topic: article
ms.prod: microsoft-identity-manager
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 689c2ef0e4e4a681a398ba7e94fb3def525937ea
ms.openlocfilehash: a5d86991f1579f292d7d303148422cef746d008a


---
# Etapa 5 Instalar/configurar o PAM

Para um PAMServer ingressado no domínio, faça logon como MIMAdmin, caso contrário, faça logon como um administrador local.
1. Execute o PowerShell como administrador
2. cd $env:SYSTEMDRIVE\PAM
3. .\PAMDeploymnet.ps1
4. Selecione a opção 5 do menu (Configuração do PAM do MIM)

>[!NOTE] Se o computador ainda não estiver ingressado em domínio no PRIV, ele solicitará as credenciais. Depois de ingressar no domínio, o computador será reinicializado.

Após a reinicialização do PAMServer, faça logon novamente no computador com a conta MIMAdmin.

1. Execute o PowerShell como administrador
2. cd $env:SYSTEMDRIVE\PAM
3. .\PAMDeployment.ps1
4. Selecione a opção 5 do menu (Configuração do PAM do MIM)

  Quando receber a solicitação, digite a senha da Conta de Monitor do MIM, da Conta do Componente do MIM, da Conta de MA do MIM, da Conta de Serviço de MIM, da Conta de Administrador do MIM e da Conta do SharePoint.
  Após a conclusão da instalação, o computador será reiniciado.



<!--HONumber=Sep16_HO4-->


