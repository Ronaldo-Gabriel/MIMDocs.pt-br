---
title: Configurando o Ambiente do MIM para o Privileged Access Management | Microsoft Identity Manager
description: 
keywords: 
author: kgremban
manager: femila
ms.date: 06/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: c4ca5b58-ad0c-48af-a9eb-b71b22d0c67c
ms.reviewer: mwahl
ms.suite: ems
ms.sourcegitcommit: 9cf126d898c93faf89d7119136cce4e4963bb63d
ms.openlocfilehash: c9f2cf2ba1f42ea1513ae38d8089839d85ae5553


---

# Configurando o Ambiente de MIM para Gerenciamento de Acesso Privilegiado
Há sete etapas a concluir ao configurar o ambiente para o acesso entre florestas, instalar e configurar o Active Directory e o Microsoft Identity Manager e demonstrar uma solicitação de acesso just-in-time.

Essas etapas são delineadas para que você possa começar do zero e criar um ambiente de teste. Se você estiver aplicando o PAM em um ambiente existente, poderá usar seus próprios controladores de domínio ou contas de usuário em vez de criar novos para serem correspondentes aos exemplos.

1.  Prepare o servidor *CORPDC* como um controlador de domínio e *CORPWKSTN* como uma estação de trabalho do membro.

2.  Prepare o servidor *PRIVDC* como um controlador de domínio.

3.  Prepare o servidor *PAMSRV* na floresta *PRIV* .

4.  Instale os componentes MIM em *PAMSRV* e os cmdlets em uma estação de trabalho do membro da floresta *CONTOSO* e prepare-os para o gerenciamento de acesso privilegiado.

5.  Estabeleça confiança entre as florestas *PRIV* e *CONTOSO* .

6.  Preparando grupos de segurança com privilégios com acesso a recursos protegidos e contas de membro para gerenciamento de acesso com privilégios just-in-time.

7.  Demonstre a solicitação, o recebimento e o uso de acesso com privilégios elevados a um recurso protegido.

>[!div class="step-by-step"]
[[!div class="step-by-step"] [Iniciar »](step-1-prepare-corp-domain.md)](step-1-prepare-corp-domain.md)



<!--HONumber=Jul16_HO2-->


