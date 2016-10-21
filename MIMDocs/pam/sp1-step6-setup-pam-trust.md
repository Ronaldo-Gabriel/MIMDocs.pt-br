---
title: "Etapa 6 Configurar a relação de confiança do PAM"
description: "Prepare o domínio CORP com identidades novas ou existentes para serem gerenciadas pelo Privileged Identity Manager usando scripts"
keywords: 
author: barclayn
manager: MBaldwin
ms.date: 10/04/2016
ms.topic: article
ms.prod: microsoft-identity-manager
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bc56b57a06592527bab13aad879ca13466e968b3
ms.openlocfilehash: 52226bfa5742e39d834f80dac69317e10b6259c7


---

# Etapa 6 Configurar a relação de confiança do PAM

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



<!--HONumber=Oct16_HO1-->


