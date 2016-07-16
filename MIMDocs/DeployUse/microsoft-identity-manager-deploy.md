---
title: "Implantação do MIM 2016 | Microsoft Identity Manager"
description: "Obtenha a lista completa das etapas envolvidas na implantação do Microsoft Identity Manager 2016, da preparação do ambiente à configuração dos portais."
keywords: 
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: fa0af422-b5e9-4599-9d9b-cb6c18ea07f9
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca7fdef81eb8a68aff46df528e1989f019f5d2a4
ms.openlocfilehash: a56ead9777f1dad1aa0d214a506cf1242f51e167


---

# Implantação do MIM 2016
Os artigos nesta seção fornecem instruções passo a passo para implantar o MIM (Microsoft Identity Manager) 2016 para cenários de autoatendimento de usuário final em um servidor novo que não tenha o FIM ou o MIM implantado anteriormente.

> [!NOTE]
> A topologia de implantação descrita nesta seção destina-se apenas à introdução e ao aprendizado sobre o MIM.  O [guia de planejamento de capacidade](/microsoft-identity-manager/plan-design/capacity-planning-guide) fornece mais informações sobre topologias para implantações de produção.  Recomendamos revisar essa documentação antes de implantar o MIM para a escala de produção ou uso.

<!---
Comment: Restore after PAM content is included

The privileged access management scenario is deployed differently than other MIM scenarios, as it requires a dedicated bastion forest environment.  If you want to learn more about deploying MIM for Privileged Identity Management, see [Getting Started with Privileged Access Management](privileged-access-management-get-started.md).
--->

## Primeiro: Preparação de um domínio
O MIM funciona com o AD (Active Directory), portanto, siga estas etapas para configurar seu controlador de domínio do AD.
- [Configuração de domínio](preparing-domain.md)

## Próximo: Configuração de um servidor de gerenciamento de identidade
Depois que o domínio está em vigor e configurado, prepare seu servidor de gerenciamento de identidade corporativa. Isso inclui configurar:
- [Windows Server 2012 R2](prepare-server-ws2012r2.md)
- [SQL Server 2014](prepare-server-sql2014.md)
- [SharePoint](prepare-server-sharepoint.md)
- [Exchange Server](prepare-server-exchange.md) (opcional)

## Por último: Instalação do Microsoft Identity Manager 2016
Depois que você configurar o domínio e o servidor, estará pronto para instalar os componentes do MIM e configurá-los para sincronizar com o AD.
- [Serviço de Sincronização do MIM](install-mim-sync.md)
- [Serviço e Portal do MIM](install-mim-service-portal.md)
- [Sincronizar bancos de dados do Serviço do MIM e do Active Directory](install-mim-sync-ad-service.md)



<!--HONumber=Jun16_HO4-->


