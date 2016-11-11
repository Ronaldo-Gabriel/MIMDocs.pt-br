---
title: "Etapa 6 Configurar a relação de confiança do PAM"
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
ms.openlocfilehash: 5bcf4f4ef201236746ec1bf75c1c8900841a6c79


---

# <a name="step-6-set-up-the-pam-trust"></a>Etapa 6 Configurar a relação de confiança do PAM

>[!div class="step-by-step"]
[«Etapa 5](sp1-step5-configuring-pam.md)
[Etapa 7»](sp1-step7-setup-sidhistory-sidfiltering.md)

**Isso não é necessário para um ambiente somente PRIV** Faça logon no PAMServer com a conta MIMAdmin.

1. Faça logon em PAMServer com a conta MIMAdmin
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. Selecione a Opção 6 do Menu (Configuração de confiança do PAM)

  Quando receber uma solicitação, insira as credenciais para a conta de administrador CORP. Depois de fornecer as credenciais, a relação de confiança será estabelecida e a configuração estará concluída.

>[!div class="step-by-step"]
[«Etapa 5](sp1-step5-configuring-pam.md)
[Etapa 7»](sp1-step7-setup-sidhistory-sidfiltering.md)



<!--HONumber=Nov16_HO2-->


