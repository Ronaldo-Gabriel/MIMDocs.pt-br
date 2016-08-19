---
title: Requisitos de software do PAM | Microsoft Identity Manager
description: "Encontre os requisitos de hardware e software para uma implantação bem-sucedida do Privileged Access Management"
keywords: 
author: kgremban
manager: femila
ms.date: 07/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 82a9085c-9667-4b3b-8079-657eab1d1e58
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae4c40c73dd9d5860f42e00765a7e34e8ca397a9
ms.openlocfilehash: 75a748f7035cfb10e833e4fdbfdc208b5245d3ea


---

# Requisitos de hardware e software

O Privileged Access Management não tem nenhum requisito de hardware além daqueles das plataformas de software subjacentes. Apenas certifique-se de ter memória ou espaço em disco suficiente e conectividade de rede.

Este artigo fornece os requisitos mínimos para uma implantação básica. Não se destina a demonstrar o desempenho, a escalabilidade ou a alta disponibilidade e não representa uma topologia de implantação recomendada para empresas de grande porte ou ambientes de produção.

## Instalando por meio de pacotes de software

O software a seguir pode ser baixado do Centro de Avaliação TechNet ou MSDN:  
- Microsoft Identity Manager 2016
  - Serviço e portal: contém o instalador para o serviço do MIM e o portal do MIM e para o cenário do PAM
  - Suplementos e extensões: contém o instalador para os cmdlets do PowerShell do solicitante

O software a seguir pode ser baixado do GitHub:  
- PAMSamplePortal: contém o aplicativo Web de exemplo para a API REST

## Software exigido

- Windows Server 2012 R2  
- Windows 8.1 Enterprise ou Windows 10 Enterprise  
- SQL Server 2012 Service Pack 1 ou SQL Server 2014  

## Software de avaliação

Se você não tiver licenças do Windows, SQL Server ou Windows Server, baixe versões de avaliação.

### Centro de Avaliação TechNet

- [Windows Server 2012 R2](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012-r2)  
- [Windows 8,1 Enterprise](https://www.microsoft.com/evalcenter/evaluate-windows-8-1-enterprise)  
- [Windows 10 Enterprise](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)  

### Centro de Download da Microsoft

- [SQL Server](https://www.microsoft.com/download/details.aspx?id=29066)  
- [SharePoint Foundation 2013 SP1 e seus pré-requisitos](https://www.microsoft.com/download/details.aspx?id=42039)

## Requisitos de hardware

Para cada componente do PAM, consulte os requisitos do sistema referentes aos produtos de software.

Para CORPDC:  
- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx) ou anterior

Para CORPWKSTN:  
- [Windows 8.1](http://windows.microsoft.com/windows-8/system-requirements)

Para PRIVDC:  
- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx)

Para PAMSRV:
- [Windows Server 2012 R2](https://technet.microsoft.com/library/dn303418.aspx)  
- [SQL Server 2012](https://msdn.microsoft.com/library/ms143506(sql.110).aspx) ou [SQL Server 2014](https://msdn.microsoft.com/en-us/library/ms143506(v=sql.120).aspx)



<!--HONumber=Jul16_HO3-->


