---
title: Adendo
description: "Prepare o domínio CORP com identidades novas ou existentes para serem gerenciadas pelo Privileged Identity Manager usando scripts"
keywords: 
author: barclayn
manager: MBaldwin
ms.date: 09/27/2016
ms.topic: article
ms.prod: microsoft-identity-manager
ms.service: microsoft-identity-manager
ms.technology: active-directory-domain-services
ms.assetid: 4b524ae7-6610-40a0-8127-de5a08988a8a
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bc56b57a06592527bab13aad879ca13466e968b3
ms.openlocfilehash: cdd859ceb13d187af3303235c0fe1e496f2bfb6e


---
# Adendo dos scripts de implantação do PAM:

## Adendo 1 Configuração do domínio PRIV

Depois de descompactar o arquivo compactado na pasta $env:SYSTEMDRIVE\PAM, edite PAMDeploymentConfig.xml para fornecer detalhes da floresta PRIV. Atualize o DNSName, o NetbiosName, o nome do controlador de domínio, o Caminho do Banco de Dados/Log e o Caminho Sysvol. Atualize também o domínio e o ForestMode. Se você estiver testando o Windows Server Technical Preview 5, defina o DomainMode & ForestMode como WinThreshold.

1. Faça logon no DC do domínio PRIV como Administrador
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. import-module .\PAMDeployment.ps1
5. Selecione a opção 9 do menu (Configuração de Floresta Priv)


O controlador de domínio será reinicializado automaticamente após a conclusão. A senha de administrador do DSRM (Modo de Restauração dos Serviços de Diretório) deve corresponder aos critérios a seguir:

  * O comprimento da senha deve ter no mínimo 15 caracteres
  * A senha contém pelo menos um caractere minúsculo
  * A senha contém pelo menos um caractere MAIÚSCULO
  * A senha contém pelo menos um digito ou caractere especial

## Adendo 2 Configuração do domínio CORP

Se você estiver apenas começando a usar o PAM e quiser configurar um ambiente de teste, o script também permitirá a configuração de um Domínio CORP. Depois de descompactar o arquivo compactado na pasta $env:SYSTEMDRIVE\PAM, edite PAMDeploymentConfig.xml adicionando detalhes da floresta CORP. Atualize DNSName, NetbiosName, nome do controlador de domínio, Caminho do banco de dados/Log e Caminho Sysvol. O nível funcional deve ser pelo menos Windows Server 2012 R2.

1. Faça logon no controlador de domínio do domínio CORP como Administrador
2. Execute o PowerShell como administrador
3. cd $env:SYSTEMDRIVE\PAM
4. import-module .\PAMDeployment.ps1
5. Selecione a opção 10 do menu (Configuração de Floresta CORP)

O controlador de domínio reiniciará automaticamente após a conclusão

## Adendo 3 Configurar um cliente CORP para fazer a validação

O ClientBinaryLocation no arquivo de configuração deve apontar para o local onde setup.exe está localizado.
Faça logon no cliente como administrador local e execute os seguintes comandos em uma janela elevada do PowerShell:

1. cd $env:SYSTEMDRIVE\PAM
2. Import-module .\PAMDeployment.ps1
3. Selecione a opção 7 do menu (Configuração do Cliente PAM do MIM)


Se o computador não estiver ingressado no domínio, ele solicitará credenciais de administrador CORP para realizar o ingresso no domínio. O computador deve ser reinicializado após o ingresso no domínio. Faça logon novamente no cliente como administrador local e execute os seguintes comandos em uma janela elevada do PowerShell:

1. cd $env:SYSTEMDRIVE\PAM
2. Import-module .\PAMDeployment.ps1
3. Selecione a opção 7 do menu (Configuração do Cliente PAM do MIM)

Vá para a Etapa 8 fornecida acima.

## Adendo 4 Se algo der errado

Todos os logs de script foram salvos em % AppData%\MIMPAMInstall. Compacte a pasta em um arquivo Zip e a envie por email para [mim2016@microsoft.com](mailto:mim2016@microsoft.com), juntamente com detalhes da operação e do erro.



<!--HONumber=Oct16_HO1-->


