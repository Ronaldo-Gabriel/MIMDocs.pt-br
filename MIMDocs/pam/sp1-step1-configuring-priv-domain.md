---
title: "Etapa 1 Configurando o domínio Priv"
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
ms.openlocfilehash: 8c1127b81676dfa40dc9bca515b4c3c6d66a1298


---
# <a name="step-1-configuring-the-priv-domain"></a>Etapa 1 Configurando o domínio Priv

>[!div class="step-by-step"]
[Etapa 2 »](sp1-step2-configuring-corp-domain.md)

1. Faça logon no PRIVDC como administrador
  * Se este for um ambiente somente PRIV, faça logon no CORPDC
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. .\PAMDeployment.ps1
5. Selecione a Opção 1 do Menu (Configuração de Floresta PRIV)


As Contas de Serviço necessárias ao gerenciamento de SQL/SharePoint & MIM são criadas automaticamente se ainda não estiverem presentes no domínio. Você precisará inserir as senhas para a criação dessas contas de serviço durante a execução do script.
Se o domínio PRIV for do Windows Server 2016, com o Nível Funcional definido como Windows Server 2016 Technical Preview 5, o script solicitará a habilitação da opção 'Recurso de Gerenciamento de Acesso Privilegiado' do Active Directory exigida pelo PAM. Escolha ‘Sim’ para continuar.
Para níveis funcionais abaixo do Windows Server 2016, ignore o aviso que outras configurações não serão executadas. Você precisará executar novamente a PAMDeployment.ps1 e a Configuração da Floresta de PAM, depois que o administrador elevar o nível funcional para o Windows Server 2016.

>[!NOTE]
>As etapas a seguir não são necessárias para configurações PRIVOnly

Copie o SIDs.txt que é gerado no $env:SYSTEMDRIVE\PAM para a pasta semelhante no CORPDC. Isso é exigido pelo CORPDC para configurar as permissões para usuários PRIV para ler as propriedades de usuário CORP.
Quando o script for concluído, ele solicitará a reinicialização do computador para que as alterações entrem em vigor.

>[!div class="step-by-step"]
[Etapa 2 »](sp1-step2-configuring-corp-domain.md)



<!--HONumber=Nov16_HO2-->


