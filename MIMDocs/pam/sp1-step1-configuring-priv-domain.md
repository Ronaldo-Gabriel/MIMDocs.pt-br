---
title: "Etapa 1 Configurando o domínio Priv"
description: "Prepare o domínio CORP com identidades novas ou existentes para serem gerenciadas pelo Privileged Identity Manager usando scripts"
keywords: 
author: barclayn
manager: MBaldwin
ms.date: 09/26/2016
ms.topic: article
ms.prod: microsoft-identity-manager
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7c5266f3d1c51e933855031f4128cbcb967d6e2
ms.openlocfilehash: 37ac600701ed9d90790e557d2f282be45eed43b4


---
# Etapa 1 Configurando o domínio Priv

1. Faça logon no PRIVDC como administrador
  * Se este for um ambiente somente PRIV, faça logon no CORPDC
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. Selecione a Opção 1 do Menu (Configuração de Floresta PRIV)


As Contas de Serviço necessárias ao gerenciamento de SQL/SharePoint & MIM são criadas automaticamente se ainda não estiverem presentes no domínio. Você precisará inserir as senhas para a criação dessas contas de serviço durante a execução do script.
Se o domínio PRIV for do Windows Server 2016, com o Nível Funcional definido como Windows Server 2016 Technical Preview 5, o script solicitará a habilitação da opção 'Recurso de Gerenciamento de Acesso Privilegiado' do Active Directory exigida pelo PAM. Escolha ‘Sim’ para continuar.
Para níveis funcionais abaixo do Windows Server 2016, ignore o aviso que outras configurações não serão executadas. Você precisará executar novamente a PAMDeployment.ps1 e a Configuração da Floresta de PAM, depois que o administrador elevar o nível funcional para o Windows Server 2016.

>[!Note] As etapas a seguir não são necessárias para configurações PRIVOnly

Copie o SIDs.txt que é gerado no $env:SYSTEMDRIVE\PAM para a pasta semelhante no CORPDC. Isso é exigido pelo CORPDC para configurar as permissões para usuários PRIV para ler as propriedades de usuário CORP.
Quando o script for concluído, ele solicitará a reinicialização do computador para que as alterações entrem em vigor.



<!--HONumber=Sep16_HO4-->


