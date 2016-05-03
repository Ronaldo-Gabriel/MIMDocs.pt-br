---
# required metadata

title: Relatório híbrido do Identity Manager no Azure | Microsoft Identity Manager
description: O relatório de híbrido do Azure Active Directory permite criar relatórios personalizados que incluem eventos de nuvem e local.
keywords:
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 7320f014-8b60-4866-92de-cfbd3e6edc48

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mwahl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Relatório Híbrido do Identity Manager no Azure
Se você tiver uma assinatura do Azure, agora pode facilmente criar um relatório de eventos que fique tanto localmente quanto na nuvem. Os relatórios então podem ser exibidos no portal do Azure. Melhor ainda, os relatórios são combinados com as atividades do Active Directory do Azure. Com o Relatório Híbrido do Identity Manager, o portal de gerenciamento do AD do Azure pode exibir relatórios de atividades de gerenciamento de identidade para atividades na nuvem e locais. Essa funcionalidade de relatório fornece o seguinte:

-   Sua experiência é unificada: relatórios unificados para atividades do IAM, tanto para nuvem quanto para local

-   Seu custo é reduzido: eliminando a necessidade da infraestrutura do depósito de dados de relatório local

-   Seus dados são seus: os dados de relatório podem ser facilmente exportados do Identity Manager local ou do Azure AD e podem ser usados para gerar relatórios de exibição personalizados

## O que é o Relatório híbrido do AD do Azure?
Com o relatório híbrido, portal de gerenciamento do AD do Azure pode exibir relatórios de atividades de gerenciamento de identidade unificados. Isso é feito independentemente de onde a atividade foi executada, no Identity Manager ou no AD do Azure. Por exemplo, se você quiser saber quem se registrou para a SSPR (Redefinição de Senha de Autoatendimento) no mês passado, poderá ver tudo isso no portal de gerenciamento do Azure AD. Nesse relatório, você verá os usuários que se registraram para a SSPR tanto no [painel de acesso de aplicativos](https://myapps.microsoft.com) quanto no Identity Manager.

![Imagem de atividade de redefinição de senhas do Azure](media/MIM-Hybrid-passwordreset.jpg)

## Porque usá-lo?
Relatórios híbridos ajudam os profissionais de TI a abordar alguns desafios comuns de relatório gerenciamento de identidade.

1.  Relatar atividades de gerenciamento de identidade que foram executadas em diferentes sistemas: Agora você pode ver relatórios de gerenciamento de identidade de atividades no AD do Azure e Identity Manager no portal de gerenciamento do AD do Azure.

2.  Exportar dados de relatório e criar relatórios personalizados: Além dos relatórios no AD do Azure, com essa nova funcionalidade, adicionamos eventos do Windows que refletem a atividade do Identity Manager. Isso torna muito mais fácil do que antes integrar sistemas SIEM, exibir a atividade do Identity Manager e criar relatórios personalizados.

3.  Minimizar o custo da infraestrutura do sistema relatório: implantar essa nova funcionalidade exigirá alguns minutos do seu tempo. Tudo o que você precisa fazer é instalar um agente de relatório no servidor do Gerenciador de identidade.

O agente de geração de relatórios é baixado do portal de gerenciamento do AD do Azure na tela de configuração do diretório:

![Imagem do download do agente de relatório híbrido do MIM](media/MIM-Hybrid-downloadReportAgent.jpg)

## Como isso funciona?
Após a instalação do agente de relatório, os dados de atividade do 	Identity Manager são enviados para o log de eventos do Windows. O agente de relatório processa os eventos e os carrega para o Azure. No Azure, os dados da atividade são armazenados, atualmente por um mês. Ao recuperar o relatório, os eventos de atividade são analisados e filtrados para os relatórios necessários. Por fim, o portal de gerenciamento do Azure recupera os dados de relatório e os renderiza como o relatório de atividades.

![Diagrama de relatório híbrido](media/MIM-Hybrid-howitworks.png)


<!--HONumber=Apr16_HO2-->


