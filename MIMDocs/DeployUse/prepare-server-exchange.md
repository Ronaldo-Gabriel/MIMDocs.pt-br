---
# required metadata

title: Configuração de um servidor de gerenciamento de identidade& #58; Exchange | Microsoft Identity Manager
description: Como uma etapa opcional, implante o Exchange Server para habilitar o MIM 2016 para enviar emails e criar caixas de correio. 
keywords:
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 34a8c16e-3bed-4e16-939b-b9fe17dd834b

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mwahl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure um servidor de gerenciamento de identidade: Exchange

>[!div class="step-by-step"]
[« SharePoint](prepare-server-sharepoint.md)
[Serviço de Sincronização do MIM »](install-mim-sync.md)

> [!NOTE]
> Em todos os exemplos a seguir, **mimservername** representa o nome do controlador de domínio, **contoso** representa o nome do domínio e **Pass@word1** representa uma senha de exemplo.

## Implantar o Microsoft Exchange Server
Se você quiser configurar o MIM para enviar e receber email ou provisionar caixas de correio, é necessário ter o Exchange presente no ambiente. Se você ainda não tiver o Exchange implantado, pode instalar uma versão de avaliação para fins de avaliação.

1. Baixe e instale o Microsoft Office 2010 Filter Packs – versão 2.0 + pacotes de filtro do Microsoft Office 2010 – versão 2.0 SP1

    - [MS Office10 FP2.0](http://www.microsoft.com/en-us/download/details.aspx?id=17062)

    - [MS Office10 FP2.0 SP1](http://www.microsoft.com/en-us/download/details.aspx?id=26604)

2. Baixe e instale a [Microsoft Unified Communications Managed API 4.0, Core Runtime 64 bits](http://www.microsoft.com/en-us/download/details.aspx?id=34992)

3. Baixe e instale a [versão de avaliação de 180 dias do MS Exchange Server 2013](http://www.microsoft.com/en-us/evalcenter/evaluate-exchange-server-2013)

>[!div class="step-by-step"]  
[« SharePoint](prepare-server-sharepoint.md)
[Serviço de Sincronização do MIM »](install-mim-sync.md)


<!--HONumber=Apr16_HO2-->


