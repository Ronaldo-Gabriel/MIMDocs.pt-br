---
title: "Definir funções com privilégios para o PAM | Microsoft Identity Manager"
description: "Decida quais funções com privilégios devem ser gerenciadas e defina a política de gerenciamento para cada uma delas."
keywords: 
author: kgremban
manager: femila
ms.date: 07/15/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 1a368e8e-68e1-4f40-a279-916e605581bc
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ae4c40c73dd9d5860f42e00765a7e34e8ca397a9
ms.openlocfilehash: 442b596107d9ade0ca466500440a32b2dd26fa14


---

# Definir funções do Privileged Access Management

Com o Privileged Access Management, é possível atribuir usuários a funções privilegiadas que eles podem ativar conforme necessário para o acesso Just-In-Time. Essas funções são definidas manualmente e estabelecidas no ambiente de bastiões. Este artigo explica o processo de decidir quais funções serão gerenciadas por meio do PAM e como defini-las com restrições e permissões apropriadas.

Uma abordagem simples para a definição de funções para o gerenciamento de acesso privilegiado é compilar todas as informações em uma planilha. Liste as funções nas funções e use as colunas para identificar as permissões e os requisitos de governança.

Os requisitos de governança variam dependendo das políticas de identidade e acesso existentes ou dos requisitos de conformidade. Os parâmetros a serem identificados para cada função podem incluir o proprietário da função, os usuários candidatos que podem estar nessa função e quais controles de autenticação, aprovação ou notificação devem ser associados ao uso da função.

As permissões de função dependerão dos aplicativos que estão sendo gerenciados. Este artigo usa o Active Directory como o aplicativo de exemplo, dividindo as permissões em duas categorias:

- As necessárias para gerenciar o próprio serviço do Active Directory (por exemplo, configurar a topologia de replicação)

- As necessárias para gerenciar os dados mantidos no Active Directory (por exemplo, criar grupos e usuários)

## Identificar as funções

Comece identificando todas as funções que você deseja gerenciar com o PAM. Na planilha, cada função potencial terá sua própria linha.

Para encontrar as funções apropriadas, considere cada aplicativo no escopo de gerenciamento:

- O aplicativo está na camada 0, 1 ou 2?  
- Quais são os privilégios que afetam a confidencialidade, integridade ou disponibilidade do aplicativo?  
- O aplicativo tem dependências em relação a outros componentes do sistema, como bancos de dados, rede ou infraestrutura de segurança, ou à virtualização ou plataforma de hospedagem?

Determine como agrupar essas considerações sobre o aplicativo. Você deseja ter funções que têm limites claros e conceder apenas as permissões suficientes para concluir tarefas administrativas comuns no aplicativo.

Sempre será útil criar funções para a atribuição de privilégios mínimos. Isso pode se basear nas responsabilidades organizacionais atuais (ou planejadas) de usuários e incluiria o privilégio exigido pelas tarefas do usuário. Também pode incluir os privilégios de simplificam as operações, sem criar riscos.

Outras considerações sobre a definição do escopo das permissões para incluir uma função são:

- Como várias pessoas estão trabalhando em uma função específica? Se não houver pelo menos duas, ele poderá ser definido estritamente como sendo útil, ou você definiu as tarefas de uma pessoa específica.

- Quantas funções são aceitas por uma pessoa? Os usuários poderão selecionar a função correta para sua tarefa?

- A população de usuários e o modo de interação entre eles com os aplicativos seriam compatíveis com o gerenciamento de acesso privilegiado?

- É possível separar a administração e a auditoria, para que um usuário em uma função administrativa não possa apagar os registros de auditoria de suas ações?

## Estabelecer requisitos de governança de função

Conforme você identificar as funções de candidato, comece a preencher a planilha. Crie colunas para os requisitos que são relevantes para sua organização. Alguns requisitos a serem considerados incluem:

- Quem é o proprietário da função que seria responsável por outra definição de função, por escolher permissões e manter as configurações de governança da função?

- Quem são os detentores de função (usuários) que realizarão as tarefas da função?

- Que método de acesso (discutido na próxima seção) do método seria apropriado para os detentores de função?

- A aprovação manual de um proprietário de função é necessária quando um usuário ativa sua função?

- É necessária a notificação quando um usuário ativa sua função?

- O uso dessa função deve gerar um alerta ou uma notificação em um sistema SIEM, para fins de acompanhamento?

- É necessário restringir os usuários a ativar a função para apenas fazer logon em computadores em que o acesso é necessário para executar as tarefas da função e em que haja verificação suficiente do host de que ele poderá proteger os privilégios e as credenciais contra o uso indevido?

- É necessário fornecer uma estação de trabalho de administrador dedicada aos detentores de função?

- Quais permissões de aplicativo (veja a lista de exemplo para o AD abaixo) estão associadas a essa função?

## Selecionar um método de acesso

Pode haver várias funções em um sistema de gerenciamento de acesso privilegiado com as mesmas permissões atribuídas a elas, se diferentes comunidades de usuários tiverem requisitos de controle de acesso distintos. Por exemplo, uma organização pode aplicar políticas diferentes para seus funcionários em tempo integral quando comparado aos funcionários de TI terceirizados de outra organização.

Em alguns casos, um usuário pode ser atribuído permanentemente a uma função e, portanto, não precisa solicitar ou ativar uma atribuição de função. Entre os exemplos de cenários de atribuição permanente estão:

- Uma conta de serviço gerenciado na floresta existente

- Uma conta de usuário na floresta existente, com uma credencial gerenciada fora do PAM (por exemplo, uma conta de vigilância, em que uma função como “Domínio/manutenção de DC” necessária para corrigir problemas de confiança e integridade de DC é permanentemente atribuída à conta, com uma senha fisicamente protegida)

- Uma conta de usuário na floresta administrativa que é autenticada com uma senha (por exemplo, um usuário que precisa de permissões administrativas 24x7 permanentes e que faz logon de um dispositivo que não dá suporte à autenticação forte)

- Uma conta de usuário na floresta administrativa, com um cartão inteligente ou um cartão inteligente virtual (por exemplo, uma conta com um cartão inteligente offline, necessária para tarefas de manutenção raras)

Para as organizações preocupadas com a possibilidade de roubo ou uso indevido de credenciais, o guia [Using Azure MFA for activation](use-azure-mfa-for-activation.md) (Usando o Azure MFA para ativação) inclui instruções sobre como configurar o MIM para exigir uma verificação adicional fora de banda no momento da ativação de função.

## Delegar permissões do Active Directory

O Windows Server cria automaticamente grupos padrão, como “Administradores de Domínio”, quando novos domínios são criados. Esses grupos simplificam a introdução e podem ser adequados para organizações menores. No entanto, organizações maiores, ou aquelas que exigem mais isolamento de privilégios administrativos, devem deixar em branco grupos como Administradores de Domínio e substituí-los por grupos que fornecem permissões refinadas.

Uma limitação do grupo Administradores de Domínio é que ele não pode ter membros de um domínio externo. Outra limitação é que ele concede permissões para três funções separadas:  
- Gerenciando o próprio serviço do Active Directory  
- Gerenciando os dados mantidos no Active Directory  
- Habilitando o logon remoto em computadores ingressados em domínio.

Em vez de grupos como Administradores de Domínio, crie novos grupos de segurança que fornecem apenas as permissões necessárias e use o MIM para fornecer dinamicamente contas de administrador com essas associações a um grupo.

### Permissões de gerenciamento de serviços

A tabela a seguir fornece exemplos de permissões que seriam relevantes para incluir funções para gerenciar o AD.

| Função | Descrição |
| ---- | ---- |
| Manutenção de domínio/DC | A associação no grupo de Domínio\Administradores que permite a solução de problemas e alteração do sistema operacional do controlador de domínio, promovendo um novo controlador de domínio em um domínio existente na floresta e a delegação de função do AD.
|Gerenciar DCs virtuais | Gerencie as VMs (máquinas virtuais) do DC (controlador de domínio) usando o software de gerenciamento de virtualização. Este privilégio pode ser concedido por meio do controle total de todas as máquinas virtuais na ferramenta de gerenciamento ou do uso da funcionalidade RBAC (controle de acesso baseado em função). |
| Estender o esquema | Gerenciar o esquema incluindo adicionar novas definições de objeto, alterar permissões a objetos de esquema e alterar permissões do padrão de esquema para tipos de objeto |
| Banco de dados de backup do Active Directory | Faça uma cópia backup do Banco de Dados do Active Directory em sua totalidade, incluindo todos os segredos confiados ao DC e ao Domínio. |
| Gerenciar relações de confiança e níveis funcionais | Crie e exclua relações de confiança com domínios e florestas externas. |
| Gerenciar sites, sub-redes e replicação | Gerenciar objetos de topologia de replicação do Active Directory, incluindo a modificação de sites, sub-redes e objetos de link de site e início das operações de replicação |
| Gerenciar GPOs | Criar, excluir e modificar Objetos de Política de Grupo em todo o domínio |
| Gerenciar zonas | Criar, excluir e modificar Zonas DNS e objetos no Active Directory |
| Modificar UOs da Camada 0 | Modificar UOs da Camada 0 e objetos contidos no Active Directory |

### permissões de gerenciamento de dados

A tabela a seguir fornece exemplos de permissões que seriam relevantes para incluir funções para gerenciar o AD ou usar os dados mantidos no AD.

| Função | Descrição |
| ---- | ---- |
| Modificar UO de Administrador da Camada 1                 | Modificar UOs que contêm objetos de Administrador da Camada 1 no Active Directory |
| Modificar UO de Administrador da Camada 2                 | Modificar UOs que contêm objetos de Administrador da Camada 2 no Active Directory |
| Gerenciamento de contas: criar/excluir/mover | Modificar contas de usuário padrão                                      |
| Gerenciamento de contas: redefinir desbloqueio       | Redefinir senhas e desbloquear contas                                  |
| Grupo de segurança: criar e modificar          | Criar e modificar grupos de segurança no Active Directory              |
| Grupo de segurança: excluir                 | Excluir grupos de segurança no Active Directory                         |
| Gerenciamento de GPO                         | Gerenciar todos os GPOs no domínio ou na floresta que não afetam os servidores da Camada 0             |
| Ingressar PC/Administrador local                    | Direitos administrativos locais para todas as estações de trabalho                               |
| Ingressar Servidor/Administrador local                   | Direitos administrativos locais para todos os servidores                                    |

## Exemplo de definições de função

A escolha das definições de função dependerá da camada de servidores que estão sendo gerenciados pelas contas com privilégios. Ela também depende da escolha dos aplicativos gerenciados, já que os aplicativos, como o Exchange, ou produtos corporativos de terceiros, como SAP, em geral, trarão suas próprias definições de função para a administração delegada.

As seções a seguir fornecem exemplos para cenários corporativos típicos.

### Camada 0 - Floresta administrativa

Funções adequadas para as contas no ambiente de bastiões podem incluir:

- Acesso de emergência à floresta administrativa
- Administradores “Cartão Vermelho”: usuários que são administradores da floresta administrativa
- Usuários que são administradores da floresta de produção
- Usuários que receberam direitos administrativos limitados aos aplicativos na floresta de produção

### Camada 0 - Floresta de produção corporativa

Funções adequadas para gerenciar as contas e os recursos da floresta de produção da camada 0 podem incluir:

- Acesso de emergência à floresta de produção
- Administradores de Política de Grupo
- Administradores do DNS
- Administradores de PKI
- Administradores de replicação e topologia do AD
- Administradores de virtualização de servidores da Camada 0
- Administradores de armazenamento
- Administradores de antimalware para servidores da Camada 0
- Administradores do SCCM da Camada 0
- Administradores do SCOM da Camada 0
- Administradores de backup para a Camada 0
- Usuários dos controladores de gerenciamento BMC e fora de banda (para gerenciamento KVM ou noturno) conectados aos hosts da Camada 0

### Camada 1

As funções de gerenciamento e backup de servidores na Camada 1 podem incluir:

- Manutenção do servidor
- Administradores de virtualização de servidores da Camada 1
- Conta do verificador de segurança
- Administradores de antimalware para servidores da Camada 1
- Administradores do SCCM da Camada 1
- Administradores do SCOM da Camada 1
- Administradores de backup para servidores da Camada 1
- Usuários dos controladores de gerenciamento BMC e fora de banda (para gerenciamento KVM ou noturno) aos hosts da Camada 1

Além disso, as funções para gerenciar aplicativos empresariais na Camada 1 podem incluir:

- Administradores do DHCP
- Administradores do Exchange
- Administradores do Skype for Business
- Administradores de farm do SharePoint
- Administradores de um serviço de nuvem, por exemplo, um Site da empresa ou DNS público
- Administradores de sistemas de HCM, Financeiro ou Legal

### Camada 2

As funções de gerenciamento de computador e usuário não administrativo podem incluir:

- Administradores de contas
- Suporte técnico
- Administradores do grupo de segurança
- Suporte à estação de trabalho em mesa



<!--HONumber=Jul16_HO3-->


