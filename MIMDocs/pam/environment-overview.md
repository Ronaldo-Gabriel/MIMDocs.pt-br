---
title: "Visão geral do ambiente do PAM | Microsoft Identity Manager"
description: "Localize o número necessário e a configuração de máquinas virtuais para implantar o Privileged Access Management com êxito"
keywords: 
author: kgremban
manager: femila
ms.date: 07/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 479db14c-1bfb-4d7c-a344-cd718a01f328
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae4c40c73dd9d5860f42e00765a7e34e8ca397a9
ms.openlocfilehash: 3057618c609ed251efe1f6cc6b2d3694ac61eafd


---

# Visão geral do ambiente

O Privileged Access Management trabalha com VMs (máquinas virtuais) com unidades separadas conectadas entre si em uma rede compartilhada. Essas máquinas virtuais podem ser hospedadas pelo Windows 8.1, Windows Server 2012 R2 ou outras plataformas de sistema operacional.

![Servidores PAM: relações e plataformas com suporte – diagrama](media/pam-test-lab-architecture.png)

Será necessário um mínimo de três máquinas virtuais.  Se você ainda não tiver um domínio do AD para o PAM gerenciar, precisará de uma VM adicional para atuar como um controlador de domínio CORP.  Se você quiser configurar o software PRIV para alta disponibilidade, também precisará de duas VMs adicionais.

As unidades em que serão armazenadas as imagens de disco de máquina virtual precisam de, pelo menos, 120 GB de espaço livre em disco para manter todas as VMs.  Se você planeja implantar para obter alta disponibilidade, verifique se o subsistema do disco atende aos requisitos de armazenamento compartilhado do SQL.  O armazenamento compartilhado pode estar na forma de discos de cluster do Clustering de Failover do Windows Server, discos em uma rede SAN (Rede de Área de Armazenamento) ou em compartilhamentos de arquivos em um servidor SMB. Observe que eles devem ser dedicados ao ambiente de bastiões; o compartilhamento de armazenamento com outras cargas de trabalho fora do ambiente de bastiões não é recomendada, pois pode prejudicar a integridade do ambiente de bastiões.

> [!NOTE]
> O atual CTP (Customer Technical Preview) do MIM não é compatível com o conteúdo do banco de dados ou diretório do CTP anterior. Se você tiver avaliado anteriormente o MIM para PAM ou outros cenários, faça backup e arquive as máquinas virtuais usadas para esse teste, e inicie a implantação com novas imagens de máquinas virtuais que não tenham sido usadas anteriormente para cenários do MIM.



<!--HONumber=Jul16_HO3-->


