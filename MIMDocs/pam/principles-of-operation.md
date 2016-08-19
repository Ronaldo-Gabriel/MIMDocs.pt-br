---
title: Entenda os componentes do PAM | Microsoft Identity Manager
description: "O Privileged Access Management compartilha alguns componentes com o MIM e tem alguns próprios. Saiba como eles funcionam juntos."
keywords: 
author: kgremban
manager: femila
ms.date: 07/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 6498f68f-36d3-448c-8fe6-649ad5a7f97d
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae4c40c73dd9d5860f42e00765a7e34e8ca397a9
ms.openlocfilehash: d17feb5d78b864bef8f0b96bfbf92a18c3c91694


---

# Noções básicas dos componentes do PAM

O Privileged Access Management mantém acesso administrativo separado das contas de usuário diárias. Essa solução se baseia em florestas paralelas:

- *CORP*: sua floresta corporativa de uso geral que inclui um ou mais domínios. Embora você possa ter várias florestas CORP, para simplificar, os exemplos apresentados neste artigo presumem uma única floresta com um único domínio.  
- *PRIV*: uma floresta dedicada criada especialmente para esse cenário de PAM. Esta floresta inclui um domínio para acomodar grupos privilegiados e contas sombreadas por meio de um ou mais domínios CORP.

A solução MIM conforme configurada para o PAM inclui os seguintes componentes:  

- **Serviço MIM**: implementa a lógica de negócios para realizar operações de gerenciamento de identidade e acesso, incluindo gerenciamento de conta privilegiada e tratamento de solicitações de elevação.   
- **Portal do MIM**: um portal baseado no SharePoint, hospedado pelo SharePoint 2013, que fornece ao administrador uma interface do usuário de gerenciamento e configuração.
- **Banco de Dados do Serviço MIM**: armazenado no SQL Server 2012 ou 2014, mantém os dados e os metadados de identidade necessários para o Serviço MIM.
- **Serviço de Monitoramento do PAM** e **Serviço de Componente do PAM**: dois serviços que gerenciam o ciclo de vida de contas privilegiadas e que auxiliam o AD PRIV no ciclo de vida da associação a um grupo.
- **Cmdlets do PowerShell**: para popular, no Serviço MIM e no AD PRIV, usuários e grupos correspondentes aos usuários e grupos na floresta CORP para administradores do PAM, bem como para usuários finais que solicitam o uso JIT (Just-In-Time) de privilégios em uma conta administrativa.
- **API REST do PAM e portal de exemplo**: para desenvolvedores que integram o MIM no cenário de PAM com clientes personalizados para elevação, sem a necessidade de usar o PowerShell ou SOAP. O uso da API REST é demonstrado com um aplicativo Web de exemplo.

Depois de instalado e configurado, cada grupo criado pelo procedimento de migração na floresta PRIV é um grupo de segurança baseado no SIDHistory de sombra (ou, em uma atualização posterior com o Windows Server vNext, um grupo principal externo) espelhando o grupo do SID na floresta CORP original. Além disso, quando o serviço do MIM adiciona membros a esses grupos na floresta de privilégios, essas associações serão por tempo limitado.

Como resultado, quando um usuário solicita elevação usando os cmdlets do PowerShell e a solicitação é aprovada, o serviço do MIM adiciona sua conta na floresta PRIV a um grupo na floresta PRIV. Quando o usuário se conectar com suas contas privilegiadas, seu token Kerberos conterá um identificador SID (segurança) idêntico ao SID do grupo na floresta CORP. Como a floresta CORP é configurada para confiar na floresta PRIV, a conta elevada que está sendo usada para acessar um recurso na floresta CORP é exibida para um recurso de verificação de associações de grupo do Kerberos ser um membro dos grupos de segurança daquele recurso. Isso é fornecido através da autenticação entre florestas do Kerberos.

Além disso, essas associações são por tempo limitado, assim, depois de um intervalo pré-configurado, a conta do usuário administrativo não será mais parte do grupo na floresta PRIV. Como resultado, essa conta não poderá ser usada para acessar recursos adicionais.



<!--HONumber=Jul16_HO3-->


