---
# required metadata

title: Guia de planejamento de capacidade | Microsoft Identity Manager
description: Use este guia para entender as variáveis que devem ser consideradas antes de implantar o MIM 2016, incluindo níveis de carga e decisões de política.
keywords:
author: kgremban
manager: stevenpo
ms.date: 04/28/2016
ms.topic: article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 3ac5b990-1678-4996-996d-cbd84b8426b4

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mwahl
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Guia de planejamento de capacidade

Este guia foi criado para ajudar no planejamento de cliente, mas não deve ser usado apenas para determinar os servidores apropriados, hardware ou topologias que são necessários para uma implantação do MIM (Microsoft Identity Manager). As organizações são incentivadas e espera-se que configurem seus próprios ambientes de teste para estimar com maior precisão a capacidade e o desempenho. A Microsoft não assegura que as organizações terão a mesma capacidade ou características de desempenho, mesmo se os componentes do MIM 2016 forem implantados e configurados de forma idêntica para os componentes descritos neste guia.

Para se preparar adequadamente para sua implantação do MIM, simule seu ambiente de produção antecipadamente em um laboratório e teste-o. Você pode decidir testar diferentes topologias executadas em diferentes tipos de hardware e, em seguida, executar diferentes escalas e carregar testes de cenário que podem ajudar a melhor a estimativa do que pode acontecer ao implantar o MIM 2016 em seu ambiente.


## Visão geral
Há várias variáveis que podem afetar o desempenho e a capacidade total da sua implantação do Microsoft Identity Manager. As maneiras nas quais você implanta fisicamente os componentes do MIM (topologia), bem como o hardware no qual os componentes são executados, são fatores importantes na determinação do desempenho e da capacidade que você pode esperar da implantação do MIM. O número e a complexidade dos objetos de configuração da política do MIM podem ser menos óbvios, mas eles ainda são fatores significativos a serem considerados no planejamento de capacidade. Finalmente, a escala esperada da implantação, bem como a carga que deve ser colocada nela, são geralmente fatores mais óbvios que afetam o desempenho e a capacidade.

Os principais fatores que afetam a capacidade e o desempenho que podem ser esperados de uma implantação de MIM 2016 são descritos na tabela a seguir.

| Fator de design | Considerações |
| ------------- | -------------- |
| Topologia | A distribuição dos serviços do MIM entre computadores na rede. Por exemplo, o serviço de sincronização do MIM 2016 será hospedado no mesmo computador que hospeda seu banco de dados? |
| Hardware | O hardware físico e quaisquer especificações de hardware virtualizadas que você está executando para cada componente do MIM. Isso inclui a CPU, a memória, o adaptador de rede e a configuração do disco rígido. |
| Objetos de configuração de política do MIM | O número e tipo dos objetos de configuração de política do MIM, que inclui os conjuntos, as MPRs (regras de política de gerenciamento) e os fluxos de trabalho. Por exemplo, quantos fluxos de trabalho são disparados para operações? Quantas definições de conjunto existem e qual é a complexidade relativa de cada uma? |
| Escala | O número de usuários, grupos, grupos calculados e tipos de objetos personalizados, como computadores a serem gerenciados pelo MIM 2016. Além disso, considere a complexidade de grupos dinâmicos e certifique-se de considerar o aninhamento de grupos. |
| Carregamento | Frequência de uso antecipado. Por exemplo, o número de vezes que você espera que grupos ou usuários novos sejam criados, senhas sejam redefinidas ou o portal seja visitado em um determinado período de tempo. Observe que a carga pode variar durante o curso de uma hora, dias, semanas ou anos. Dependendo do componente, você terá que criar o pico de carga ou a carga média.


## Componentes de hospedagem do Microsoft Identity Manager
O Microsoft Identity Manager tem muitos componentes diferentes. Em muitos casos, esses componentes não estão localizados no mesmo computador. Quando você pensa da perspectiva da capacidade de planejamento do MIM, os componentes e os computadores físicos (e, possivelmente, máquinas virtuais) nos quais os componentes são hospedados são considerações importantes. Muitos fatores potenciais podem afetar o desempenho do ambiente do MIM, por exemplo, a configuração do disco físico do computador que executa o banco de dados SQL do serviço do MIM 2016. O número de eixos que compõem a configuração de disco ou a distribuição de arquivos de dados e log pode afetar significativamente o desempenho do sistema. Além disso, considere os fatores externos em sua configuração. Se você estiver usando uma SAN como a configuração do banco de dados de serviço do MIM 2016, quais os outros aplicativos que estão compartilhando a SAN? Como esses aplicativos afetam o desempenho do banco de dados e como eles competem por recursos de disco compartilhados na SAN? Vários aplicativos disputando os mesmos recursos de disco pode resultar em afunilamentos e desempenho de disco irregular.


## Usuários e grupos
O número de usuários e grupos em seu ambiente é uma consideração típica quando você pensa sobre a escala de uma implantação. No entanto, há várias outras considerações relacionadas que você também deve incluir no planejamento. As outras considerações sobre desempenho de fluxo de trabalho incluem o seguinte:

- Os usuários podem criar grupos? Neste caso, você deve considerar a estimativa de quantos usuários criando grupos afetará o crescimento de grupos em seu ambiente.

- Grupos dinâmicos serão implantados?
  - Que tipos de grupos dinâmicos serão implantados?
  - Quantos grupos dinâmicos têm probabilidade de serem implantados?


## Níveis de carga esperados
Você também deve considerar o tipo de carga que será colocada nos componentes do MIM. Algumas questões relevantes a serem consideradas incluem o seguinte:

- Com que frequência você espera uma solicitação para ingressar ou sair de um grupo?

- Com que frequência você espera que um usuário crie um grupo estático ou dinâmico?

- Você pode obter essas informações de aplicativos existentes em seu ambiente?

- Quanta carga você espera de operações controladas por não usuários, como a sincronização de alterações de sistemas externos? Certifique-se de que você está contando a carga gerada por operações de sincronização de informações de identidade com sistemas externos.

- Que tipo de cenários você planeja implantar? Cenários diferentes contribuirão para padrões de carga diferentes. Por exemplo, computadores cliente que têm o cliente do MIM 2016 instalado validado periodicamente se o registro é necessário ao entrar, o que aumenta a carga do sistema.

- Você espera grandes variações em níveis de carga de normal a pico de carga? Por exemplo, você espera grandes números de redefinições de senha após períodos de férias? Certifique-se de que você trabalha suas agendas de sincronização e manutenção do sistema fora dos picos de uso antecipados. Quando você pensar sobre planejamento de capacidade, certifique-se de considerar os períodos de pico de carga.


## Objetos de configuração de política

Os objetos de configuração de política do Microsoft Identity Manager representam a lógica de negócios para a implantação do MIM. Esta é uma área em que cada implementação do MIM provavelmente será única devido à configuração de política específica para as necessidades de cada implantação. Os objetos de configuração de política do MIM incluem as MPRs, conjuntos, fluxos de trabalho e regras de sincronização de uma determinada implantação. Considerações de desempenho chave relacionadas aos objetos de configuração de política do MIM incluem o seguinte:

- **Conjuntos** Cada operação do sistema deve ser avaliada nas atualizações e associações de conjuntos existentes que causam alterações na associação de conjuntos existentes. Por exemplo, uma alteração simples, como alterar o número de construção do escritório de um indivíduo, pode não ter um grande impacto. No entanto, outras alterações podem ter um impacto em cascata, como a alteração de um gerente, o que pode afetar vários objetos em vários níveis.

- **Regras de política de gerenciamento** As MPRs são usadas para controlar as regras de controle de acesso e disparar fluxos de trabalho. Como você mesmo cria as MPRs, pode achar que é necessário aumentar o número de conjuntos de forma que seja possível capturar vários estados de transição do objeto. Esses conjuntos adicionais podem disparar fluxos de trabalho adicionais, com cada mapeamento de fluxo de trabalho para solicitações únicas no sistema. Isso torna-se então outro item para incluir ao planejar a capacidade.

Enquanto trabalha com objetos de configuração de política do MIM, você também deve considerar o seguinte:

- Princípios de segurança externos serão provisionados por meio de várias florestas do AD DS (Serviços de Domínio do Active Directory)? Isso gerará mais fluxos de trabalho e solicitações, que resulta em uma carga adicional no sistema.

- Você usará o provisionamento sem código? Nesse caso, isso afeta o número de entradas de regras esperadas, bem como solicitações associadas e fluxos de trabalho no sistema.


## Consulte também
- O [Guia de planejamento de capacidade do FIM (Forefront Identity Manager) 2010](http://go.microsoft.com/fwlink/?LinkId=200180) baixável apresenta mais detalhes sobre um build de teste e resultados de teste de desempenho.


<!--HONumber=Apr16_HO2-->


