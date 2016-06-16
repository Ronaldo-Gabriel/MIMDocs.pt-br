---
# required metadata

title: Instalação do MIM 2016 & #58; Sincronização do Active Directory e do Serviço do MIM | Microsoft Identity Manager
description: Use agentes de gerenciamento e o Serviço de Sincronização do MIM para sincronizar os bancos de dados do Active Directory e do MIM.
keywords:
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 5e532b67-64a6-4af6-a806-980a6c11a82d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mwahl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Instalação do MIM 2016: Sincronização do Active Directory e do Serviço do MIM

>[!div class="step-by-step"] [« Serviço e Portal do MIM](install-mim-service-portal.md)

> [!NOTE]
> Este passo a passo usa nomes e valores de exemplo de uma empresa chamada Contoso. Substitua-os pelos seus próprios valores. Por exemplo:
> - Nome do controlador de domínio - **mimservername**
> - Nome do domínio - **contoso**
> - Senha - **Pass@word1**

Por padrão, o Servido de Sincronização (Sync) do MIM não tem nenhum conector configurado.  Uma primeira etapa comum é usar a sincronização do MIM para preencher o banco de dados do Serviço do MIM com contas existentes do Active Directory. Para isso, você usará o aplicativo de serviço de sincronização do MIM.

## Criação do agente de gerenciamento do MIM
O MIM MA (Agente de gerenciamento) é um conector para a sincronização do MIM com o Serviço do MIM. Para criar esse conector, use o assistente para Criar agente de gerenciamento.

Quando você configura um MIM MA, precisa especificar uma conta de usuário. Este documento usa **MIMMA** como nome para essa conta.

> [!NOTE] A conta usada para o agente de gerenciamento do MIM deve ser a mesma conta que foi especificada durante a instalação do Serviço do MIM.

###Para criar o MIM MA

1.  Abra o Gerenciador de serviço de sincronização.

2.  Para abrir o assistente Criar Agente de Gerenciamento, no menu **Ações**, clique em **Criar**.

3.  Na página **Criar Agente de Gerenciamento**, forneça as seguintes configurações e clique em **Avançar**.

    -   Agente de gerenciamento para: Agente de gerenciamento de Serviço do MIM

    -   Nome: MIMMA

4.  Na página **Conectar ao Banco de Dados**, forneça as seguintes configurações e clique em **Avançar**

    -   Servidor: localhost

    -   Banco de dados: MIMService

    -   Endereço básico do Serviço do MIM: http://localhost:5725

    -   Modo de autenticação: Autenticação integrada do Windows

    -   Nome de usuário: mimma

    -   Contrasenha: Pass@word

    -   Domínio: contoso

5.  Na página **Tipos de Objeto Selecionados**, verifique se os tipos de objeto listados abaixo estão selecionados e clique em **Avançar**

    -   ExpectedRuleEntry

    -   DetectedRuleEntry

    -   SynchronizationRule

    -   Person

    -   Grupo

6.  Na página **Atributos Selecionados**, verifique se todos os atributos listados estão selecionados e, em seguida, clique em **Avançar**.

7.  Na página **Configurar Filtro do Conector**, clique em **Avançar**.

8.  Na página **Configurar Mapeamentos de Tipo de Objeto**, adicione o seguinte mapeamento e clique em **Avançar**

    - Selecione **Pessoa** na listas **Tipo de Objeto de Fonte de Dados**.
    - Clique em **Adicionar Mapeamento** para abrir a caixa de diálogo Mapeamento.
    - Selecione **pessoa** na lista **Tipo de objeto metaverso**.
    - Clique em **OK** para fechar a caixa de diálogo Mapeamento.

9.  Na página **Configurar o Fluxo de Atributos**, aplique os seguintes mapeamentos de fluxo de atributo e, em seguida, clique em **Avançar**

    | **Atributo de fonte de dados** | **Direção do fluxo** | **Atributo metaverso** |
    |-|-|-|
    | AccountName | Exportar | accountName |
    | DisplayName | Exportar | displayName |
    | Domain | Exportar | domain |
    | EmployeeID | Exportar | employeeID |
    | EmployeeTipo | Exportar | employeeTipo |
    | Email | Exportar | mail |
    | Primeiro nome | Exportar | firstName |
    | Sobrenome | Exportar | lastName |
    | ObjectSID | Exportar | objectSid |

10.  Selecione **Pessoa** como o tipo de objeto de fonte de dados.

    -   Selecione **Pessoa** como o tipo de objeto de Metaverso.

    -   Selecione **Direto** como o Tipo de Mapeamento.

    -   Para cada linha na tabela anterior, conclua as seguintes etapas:

        -   Selecione a **Direção do fluxo** exibida para aquela linha na tabela.

        -   Selecione o **Atributo de Fonte de dados** exibido para aquela linha na tabela.

        -   Selecione o **Atributo de metaverso** exibido para aquela linha na tabela.

        -   Para aplicar o mapeamento de fluxo, clique em **Novo**.

    -   Selecione o **Grupo** como o tipo de fonte de dados e o tipo de objeto do metaverso.

    -   Selecione **Direto** como o Tipo de Mapeamento.

    -   Para cada linha na tabela a seguir, conclua as seguintes etapas:

        -   Selecione a **Direção do fluxo** exibida para aquela linha na tabela.

        -   Selecione o **Atributo de Fonte de dados** exibido para aquela linha na tabela.

        -   Selecione o **Atributo de metaverso** exibido para aquela linha na tabela.

        -   Para aplicar o mapeamento de fluxo, clique em **Novo**.

    | **Atributo de fonte de dados** | **Direção do fluxo** | **Atributo metaverso** |
    |-|-|-|
    | AccountName | Exportar | accountName |
    | DisplayName | Exportar | displayName |
    | Domain | Exportar | domain |
    | Email | Exportar | mail |
    | MailNickName | Exportar | mailNickName |
    | Membro | Exportar | membro |
    | ObjectSID | Exportar | objectSid |
    | Escopo | Exportar | scope |
    | Tipo | Exportar | tipo |
    | MembroshipAddWorkflow | Exportar | membershipAddWorkflow |
    | MembroshipLocked | Exportar | membershipLocked |
    | DisplayName | Importar | displayName |
    | Escopo | Importar | scope |
    | Tipo | Importar | tipo |
    | Membro | Importar | membro |
    | AccountName | Importar | accountName |
    | DisplayedOwner | Importar | displayedOwner |
    | MailNickName | Importar | mailNickName |


11.  Na página **Configurar Desprovisionamento**, clique em **Avançar**

12.  Para criar o agente de gerenciamento, na página **Configurar Extensões**, clique em **Concluir**.

## Criação do agente de gerenciamento do AD
O agente de gerenciamento do Active Directory é um conector para serviços de domínio do AD. Para criar esse conector, use o assistente para Criar agente de gerenciamento.

1. Para abrir o assistente Criar Agente de Gerenciamento, no menu **Ações**, clique em **Criar**.

2. Na página **Criar Agente de Gerenciamento**, forneça as seguintes configurações e clique em **Avançar**:

    - Agente de gerenciamento para: Serviços de Domínio do Active Directory
    - Nome: ADMA

3. Na página **Conectar à Floresta do Active Directory**, forneça as seguintes configurações e clique em **Avançar**:

    - Nome da floresta: contoso.local
    - Nome de usuário: administrador
    - Senha: &lt;a senha da conta&gt;
    - Domínio: contoso

4. Na página **Configurar Partições de Diretório**, forneça as seguintes configurações e, em seguida, clique em **Avançar**:

    - Na lista **Selecionar partições de diretório**, selecione **DC=CONTOSO, DC=local**.

    - Para abrir a caixa de diálogo Selecionar Contêineres, clique em **Contêineres**.

    - Se você quiser alterar o contêiner para que apenas o MIM gerencie objetos em um contêiner específico, clique no nó **DC=CONTOSO, DC=local** e, em seguida, clique no nó do contêiner de interesse.

    - Para fechar a caixa de diálogo Selecionar Contêineres, clique em **OK**.

5. Na página **Configurar Hierarquia de Provisionamento**, clique em **Avançar**.

6. Na página **Selecionar Tipos de Objeto**, forneça as seguintes configurações e, em seguida, clique em **Avançar**:

    - Na lista **Tipos de objeto**, selecione o **usuário** e o **grupo**.

7. Na página **Selecionar Atributos**, forneça as seguintes configurações e, em seguida, clique em **Avançar**:

    - Selecione **Mostrar Tudo**.

8. Na lista **Atributos**, selecione os seguintes atributos:

    -   empresa
    -   displayName
    -   employeeID
    -   employeeTipo
    -   givenName
    -   groupType
    -   gerenciador
    -   managedBy
    -   membro
    -   objectSid
    -   sAMAccountName
    -   sAMAccountTipo
    -   sn
    -   unicodePwd
    -   userAccountControl

9. Na página **Configurar Filtro do Conector**, clique em **Avançar**.

10. Na página **Configurar Regras de Ingresso e Projeção**, clique em **Avançar**.

11. Na página **Configurar Fluxo de Atributos**, clique em **Avançar**.

12. Na página **Configurar Desprovisionamento**, clique em **Avançar**.

13. Na página **Configurar Extensões**, clique em **Concluir**.


## Criar perfis de execução

Crie perfis de execução para os conectores MIMMA e ADMA.

### Criar perfis de execução para o conector ADMA

Esta tabela mostra que os cinco perfis de execução que você criará para o conector ADMA:

| Nome | Tipo |
| ---- | ---- |
| Profile1 | Importação completa (somente estágio) |
| Profile2 | Sincronização completa |
| Profile3 | Importação delta (somente estágio) |
| Profile4 | Sincronização Delta |
| Profile5 | Exportar |

Para criar perfis de execução para o conector ADMA:

1. Abra o Synchronization Service Manager e, no menu **Ferramentas**, clique em **Agentes de Gerenciamento**.

2. Na lista **Agentes de Gerenciamento**, selecione **ADMA**.

3. Para abrir Configurar Perfis de Execução da caixa de diálogo, no menu **Ações**, clique em **Configurar Perfis de Execução**.

4. Para cada perfil de execução na tabela, conclua as seguintes etapas:

    - Para abrir o assistente Configurar Perfil de Execução, clique em **Novo Perfil**.

    - Na caixa **Nome**, digite o nome do perfil da tabela e clique em **Avançar**.

    - Na lista **Tipo**, selecione o tipo de etapa da tabela e, em seguida, clique em **Avançar**.

    - Clique em **Concluir** para criar o perfil de execução.

5. Para fechar a caixa de diálogo Configurar Perfis de Execução, clique em **OK**.

### Criar perfis de execução para o conector MIMMA

Esta tabela mostra os cinco perfis de execução correspondentes para o conector MIMMA:

| Nome | Tipo |
| -------- | -------- |
| Profile1 | Importação completa (somente estágio) |
| Profile2 | Sincronização completa |
| Profile3 | Importação delta (somente estágio) |
| Profile4 | Sincronização Delta |
| Profile5 | Exportar |

Para criar perfis de execução para o conector MIMMA:

1. Abra o Synchronization Service Manager e, no menu **Ferramentas**, clique em **Agentes de Gerenciamento**.

2. Na lista **Agentes de Gerenciamento**, selecione **MIMMA**.

3. Para abrir Configurar Perfis de Execução da caixa de diálogo, no menu **Ações**, clique em **Configurar Perfis de Execução**.

4. Para cada perfil de execução na tabela, conclua as seguintes etapas:

    - Para abrir o assistente Configurar Perfil de Execução, clique em **Novo Perfil**.

    - Na caixa **Nome**, digite o nome do perfil da tabela e clique em **Avançar**.

    - Na lista **Tipo**, selecione o tipo de etapa da tabela e, em seguida, clique em **Avançar**.

    - Clique em **Concluir** para criar o perfil de execução.

5. Para fechar a caixa de diálogo Configurar Perfis de Execução, clique em **OK**.

## Configurar o Serviço do MIM

Usando o Portal do MIM, você criará a regra de sincronização de entrada do usuário do AD para o Serviço do MIM.

Para criar a regra de sincronização de entrada do usuário do AD:

1. Na página inicial do Portal do MIM, na barra de navegação, clique em **Administração**.

2. Para abrir a página Regras de Sincronização, clique em **Regras de Sincronização**.

3. Para abrir o assistente Criar Regra de Sincronização, na barra de ferramentas, clique em **Novo**.

4. Na guia **Geral**, especifique as seguintes informações e, em seguida, clique em **Avançar**:

    -   Nome de exibição: Regra de sincronização de entrada de usuário do AD
    -   Direção do fluxo de dados: Entrada

5. Na guia **Escopo**, forneça as seguintes informações e, em seguida, clique em **Avançar**:

    -   Tipo de recurso do metaverso: pessoa
    -   Sistema externo: ADMA
    -   Tipo de recurso do sistema externo: pessoa

6. Na guia **Relacionamento**, forneça as seguintes informações e, em seguida, clique em **Avançar**:

    -   Para configurar os critérios de relação, selecione **ObjectSID** na lista MetaverseObject:person(Attribute) e na lista ConnectedSystemObject:person(Attribute).

    -   Selecione **Criar Recurso no MIM**.

7. Na página **Fluxo de Entrada do Atributo**, forneça as seguintes informações e, em seguida, clique em **Avançar**:

    | Regra de fluxo | Origem | Destination |
    |-|-|-|
    |Regra 1|samAccountName|f|
    |Regra 2|displayName|displayName|
    |Regra 3|EmployeeTipo|EmployeeTipo|
    |Regra 4|givenName|givenName|
    |Regra 5|sn|lastName|
    |Regra 6|Manager|gerenciador|
    |Regra 7|objectSID|ObjectSID|
    |Regra 8|"Contoso"|domain|

    Para cada linha nesta tabela, execute as seguintes etapas:

    - Para abrir a caixa de diálogo Definição de Fluxo, clique em **Novo Fluxo de Atributos**.

    - Na guia **Origem**, selecione o atributo mostrado para aquela linha na tabela.

    - Na guia **Destino**, selecione o atributo mostrado para aquela linha na tabela.

    - Para aplicar a configuração de fluxo de atributo, clique em **OK**.

8. Na guia **Resumo**, clique em **Enviar**.

## Inicializar o ambiente de testes
Há quatro etapas que você precisa seguir antes de testar sua configuração do MIM com dados do AD:

### Habilitação do provisionamento

1. Abra o Gerenciador de serviço de sincronização.

2. Para abrir a caixa de diálogo Opções, no menu **Ferramentas**, clique em **Opções**

3. Selecione **Habilitar Provisionamento da Regra de Sincronização**.

4. Para fechar a caixa de diálogo Opções, clique em **OK**.

### Inicialização do MIMMA

Execute um ciclo completo de sincronização neste conector. O ciclo completo consiste nas execuções dos perfis de execução a seguir:

- Importação completa
- Sincronização completa
- Exportar
- Importação de delta

Siga estas etapas para executar cada um dos quatro perfis de execução.

1. Abra o Synchronization Service Manager e, no menu **Ferramentas**, clique em **Agentes de Gerenciamento**.

2. Na lista **Agentes de Gerenciamento**, selecione **MIMMA**.

3. Para abrir a caixa de diálogo Executar Agente de Gerenciamento, no menu **Ações**, clique em **Executar**.

4. Para cada perfil de execução listado acima, conclua as seguintes etapas:

    - Para abrir a caixa de diálogo Executar Agente de Gerenciamento, no menu **Ações**, clique em **Executar**.

    - Na lista **Perfis de Execução**, selecione o perfil de execução que deseja executar.

    - Para iniciar o perfil de execução, clique em **OK**.

#### Configurar a precedência de fluxo de atributo

Durante a inicialização do conector do MIM, as regras de sincronização configuradas foram levadas para o metaverso.

Ajuste a precedência do fluxo de atributos para os atributos enviados por este conector para garantir que atributos já no AD possam fluir para o metaverso e depois também para o banco de dados do Serviço do MIM.

### Inicializar o ADMA

Para inicializar o conector do Active Directory, você precisa executar uma importação completa e uma sincronização completa nele. A importação completa leva os objetos existentes do AD para o espaço do conector. A sincronização completa atualiza as regras de sincronização para que correspondam às do conector do MIM.

1. Abrir o Synchronization Service Manager e, no menu **Ferramentas**, clicar em **Agentes de Gerenciamento**.

2. Na lista **Agentes de Gerenciamento**, selecione **ADMA**.

3. Para abrir a caixa de diálogo Executar Agente de Gerenciamento, no menu **Ações**, clique em **Executar**.

4. Para cada perfil de execução listado acima, conclua as seguintes etapas:

    - Para abrir a caixa de diálogo Executar Agente de Gerenciamento, no menu **Ações**, clique em **Executar**.

    - Na lista **Perfis de Execução**, selecione o perfil de execução que deseja executar.

    - Para iniciar o perfil de execução, clique em **OK**.

### Popular o banco de dados do Serviço do MIM

Para preencher o banco de dados de Serviço do MIM com os objetos, você precisa executar um ciclo de sincronização no conector do MIMMA. O ciclo consiste em:

- Exportar
- Importação completa
- Sincronização completa

Siga estas etapas para executar cada um dos três perfis de execução.

1. Abra o Synchronization Service Manager e clique em **Agentes de Gerenciamento** no menu **Ferramentas**.

2. Selecione **MIMMA** na lista **Agentes de Gerenciamento**.

3. Clique em **Executar** no menu **Ações** para abrir a caixa de diálogo Executar Agente de Gerenciamento.

4. Para cada perfil de execução listado acima, conclua as seguintes etapas:

    - Clique em **Executar** no menu **Ações** para abrir a caixa de diálogo Executar Agente de Gerenciamento.
    - Selecione o perfil de execução que deseja executar na lista **Perfis de execução**.
    - Clique em **OK** para iniciar o perfil de execução.

>[!div class="step-by-step"] [« Serviço e Portal do MIM](install-mim-service-portal.md)


<!--HONumber=Jun16_HO1-->


