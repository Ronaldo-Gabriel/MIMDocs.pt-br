---
title: "Instalar o Serviço de Sincronização do MIM | Microsoft Identity Manager"
description: "Comece a usar os componentes do MIM 2016 instalando e configurando o Serviço de Sincronização."
keywords: 
author: kgremban
manager: femila
ms.date: 07/21/2016
ms.topic: get-started-article
ms.prod: identity-manager-2015
ms.service: microsoft-identity-manager
ms.technology: security
ms.assetid: 2585e9c5-ce34-46c7-bdcf-8c08773901dc
ms.reviewer: mwahl
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b3ab1b9376c9b613739d87c812f4b16a4e17e6de
ms.openlocfilehash: 2dfc89d32ef3b615201f1eb57ed3b8f5daed513e


---

# Instalação do MIM 2016: Serviço de Sincronização do MIM

>[!div class="step-by-step"]
[« Exchange Server](prepare-server-exchange.md)
[Serviço MIM e Portal »](install-mim-service-portal.md)

> [!NOTE]
> Este passo a passo usa nomes e valores de exemplo de uma empresa chamada Contoso. Substitua-os pelos seus próprios valores. Por exemplo:
> - Nome do controlador de domínio - **mimservername**
> - Nome do domínio - **contoso**
> - Senha - **Pass@word1**

Para instalar os componentes do Microsoft Identity Manager 2016, primeiramente configure o pacote de instalação.

1. Entre como *contoso\Administrador* no servidor que você está usando para o gerenciamento de identidades.

2. Descompacte o pacote de instalação do MIM ou monte o DVD de imagem do MIM.

## Instalar o serviço de sincronização MIM 2016

1. Na pasta de instalação descompactada do MIM, navegue até a pasta **Serviço de Sincronização** .

2. Execute o **Instalador do Serviço de Sincronização do MIM**. Siga as diretrizes do instalador e conclua a instalação.

3. Na tela de boas-vindas, clique em **Avançar**.

    ![Imagem de boas-vindas do assistente do instalador do MIM](media/MIM-Install1.png)

4. Leia os termos de licença e clique em **Avançar** para aceitá-los.

5. Na tela **Instalação Personalizada** clique em **Avançar**.

    ![Imagem de configuração personalizada](media/MIM-Install2.png)

6.  Na tela de configuração do banco de dados de sincronização, selecione:

    1.  O SQL Server está localizado em: **Este computador**.

    2.  A instância do SQL Server é: **A instância padrão**.

    ![Imagem de conexão de banco de dados](media/MIM-Install3.png)

7.  Configure a conta de serviço de sincronização de acordo com a conta criada anteriormente:

    1.  Conta de serviço: *MIMSync*

    2.  Contrasenha: *Pass@word1*

    3.  Domínio da conta de serviço ou nome do computador local: *contoso*

    ![Imagem de conta de serviço](media/MIM-Install4.png)

8.  Fornece ao instalador de sincronização do MIM os grupos de segurança relevantes:

    1. Administrador = *contoso\MIMSyncAdmins*

    2. Operador= *contoso\MIMSyncOperators*

    3. Ligação = *contoso\MIMSyncJoiners*

    4. Navegador do conector = *contoso\MIMSyncBrowse*

    5. Gerenciamento de senha do WMI = *contoso\MIMSyncPasswordReset*

    ![Imagem de grupos de segurança](media/MIM-Install5.png)

9. Na tela de configurações de segurança, marque **Habilitar regras de firewall para Comunicações RPC de entrada** e clique em **Avançar**.

10. Clique em **Instalar** para iniciar a instalação de Sincronização do MIM.

    1. Um aviso sobre a conta de serviço de sincronização do MIM pode aparecer – clique em **OK**.

    2. A Sincronização do MIM será instalada.

    3. Um aviso sobre a criação de um backup da chave de criptografia é exibido. Clique em **OK** e selecione uma pasta para armazenar o backup da chave de criptografia.

        ![Imagem da chave de criptografia de backup de Sync do MIM](media/MIM-Install7.png)

    4. Quando o instalador concluir com sucesso a instalação, clique em **Concluir**.

    5. Você precisa sair e entrar para que as alterações de associação de grupo entrem em vigor. Clique em **Sim** Sair.

>[!div class="step-by-step"]  
[« Exchange Server](prepare-server-exchange.md)
[Serviço MIM e Portal »](install-mim-service-portal.md)



<!--HONumber=Jul16_HO3-->


