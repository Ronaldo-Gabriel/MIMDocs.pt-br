---
title: "Etapa 2 Configurando o domínio CORP"
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
ms.openlocfilehash: b7acc475c505b29559c510fd3fa350fed1c3157b


---

# <a name="step-2-configuring-the-corp-domain"></a>Etapa 2 Configurando o domínio CORP

>[!div class="step-by-step"]
[« Etapa 1](sp1-step1-configuring-priv-domain.md)
[Etapa 3 »](sp1-step3-installing-configuring-sql.md)

Após o SIDs.txt ser copiado para CORPDC **não é necessário para implantações PRIVOnly**

1. Faça logon em CORPDC como Administrador
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. selecione a Opção 2 do Menu (Configuração de Floresta CORP)

>[!div class="step-by-step"]
[« Etapa 1](sp1-step1-configuring-priv-domain.md)
[Etapa 3 »](sp1-step3-installing-configuring-sql.md)



<!--HONumber=Nov16_HO2-->


