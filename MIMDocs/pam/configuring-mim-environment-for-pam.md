---
title: Implantar e configurar o PAM | Microsoft Identity Manager
description: "O roteiro para instalação do MIM e configuração dele para o Privileged Access Management."
keywords: 
author: kgremban
manager: femila
ms.date: 07/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: c4ca5b58-ad0c-48af-a9eb-b71b22d0c67c
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae4c40c73dd9d5860f42e00765a7e34e8ca397a9
ms.openlocfilehash: 4b4953089cb676baae97988f380debbfefcd1083


---

# Configure o ambiente do MIM para o Privileged Access Management
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
[Iniciar »](step-1-prepare-corp-domain.md)



<!--HONumber=Jul16_HO3-->


