---
title: Configurações avançadas
seo-title: Configurações avançadas
description: Saiba mais sobre as configurações avançadas que se aplicam à integração do AEM 3D para implantações do Maya e não do Maya.
seo-description: Saiba mais sobre as configurações avançadas que se aplicam à integração do AEM 3D para implantações do Maya e não do Maya.
uuid: 016e7745-e3c3-4d77-b95a-c0e671d719e2
contentOwner: Rick Brough
topic-tags: 3D
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
discoiquuid: e43fd002-2954-4ef1-ac2b-e8d45afa75be
exl-id: fdc82bca-e676-4052-b3e9-a198c685df96
feature: Ativos 3D
role: Administrator,Business Practitioner
translation-type: tm+mt
source-git-commit: 13eb1d64677f6940332a2eeb4d3aba2915ac7bba
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 1%

---

# Configurações avançadas {#advanced-configuration-settings}

Embora as configurações padrão sejam apropriadas para casos de uso típicos, algumas situações podem exigir que você faça alterações.

As seguintes configurações avançadas se aplicam à integração do AEM 3D para implantações do Maya e não Maya.

Todas as configurações são acessadas usando **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**).

>[!NOTE]
>
>Se você reinstalar o pacote, ele redefinirá todas as configurações para seus valores padrão.

>[!CAUTION]
>
>Editar qualquer configuração que não esteja listada na tabela abaixo pode resultar em um comportamento de programa inesperado ou indesejado.

## Configuração de tipos de ativos {#asset-types-configuration}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

| Caminho | Descrição |
|---|---|
| `/libs/settings/dam/v3D/assetTypes/*/Conversion` | Especifica o tipo de arquivo para o formato 3D intermediário criado durante a assimilação. Deve estar vazio para os formatos de arquivo &#39;fbx&#39; e &#39;obj&#39; ou &#39;fbx&#39; para formatos ativados pelo Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/Enabled` | Defina como true ou false para ativar ou desativar essa entrada na lista **[!UICONTROL assetTypes]**. |
| `/libs/settings/dam/v3D/assetTypes/*/Extension` | Especifique um ou mais sufixos de arquivo separados por vírgulas ou extensões de arquivo que devem ser associadas a esse tipo de ativo. |
| `/libs/settings/dam/v3D/assetTypes/*/IngestRegime` | Deve ser `native` para formatos de arquivo FBX e OBJ e `maya` para formatos habilitados pelo Maya. |
| `/libs/settings/dam/v3D/assetTypes/*/MimeType` | Especifica o tipo MIME para este tipo de ativo. Para formatos ativados pelo Maya, é recomendável usar `application/x-ext`, onde `ext` é a string especificada como o valor `Extension`. |

## Configuração de assimilação {#ingestion-configuration}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

<table> 
 <tbody> 
  <tr> 
   <td><strong>Caminho</strong></td> 
   <td><strong>Descrição</strong></td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/addGroundPlaneImageOnAssimilar</td> 
   <td>Permite a geração de uma sombra de oclusão de ambiente ao visualizar ou renderizar com um palco IBL. Aplica-se à visualização e renderização com o RapidRefine</td> 
  </tr> 
  <tr> 
   <td><p>/libs/settings/dam/v3D/settings/cleanupRenderWorkDir</p> </td> 
   <td>Defina como <strong>false</strong> para manter arquivos temporários na pasta MayaWork após a conversão e renderização. Pode ser útil ao depurar problemas de conversão e renderização do Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeAnimationOnAssimilar</td> 
   <td><p>Quando ativado, o ImageMagick é instalado no servidor e o magickPath é configurado. O Rapid Refine é usado para criar uma animação simples para objetos 3D, usados como miniatura na Exibição de cartão e em outras exibições.</p> <p>A criação de animações consome recursos significativos da CPU durante o processo de assimilação.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/invokeLightMapsOnAssimilar</td> 
   <td>Permite a criação automática de mapas de luz na assimilação. Defina como <strong>false</strong> para desativar a criação automática de mapa de luz; isso pode reduzir bastante o consumo da CPU ao custo de qualidade reduzida para visualização e renderização com o Rapid Refine. Não afeta a renderização com o Maya.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/gPlaneZero</td> 
   <td><p>Quando definido como <strong>true</strong> (padrão), os objetos são movidos verticalmente, se necessário, para garantir que todas as partes do objeto estejam acima do plano base (y=0).</p> <p>Quando definido como <strong>false</strong> (padrão), os objetos não são reposicionados e podem ser parcialmente ocultos pelo plano base de um palco. (Aplica-se apenas à pré-visualização e renderização com Rapid Refine.) No entanto, não afeta a renderização com o Maya. Quando definido como <strong>true</strong>, a posição vertical dos objetos no Maya pode ser diferente da visualização ou durante a renderização com o Rapid Refine.</p> </td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/Paths/magickPath</td> 
   <td>O caminho e o nome para o utilitário de conversão ImageMagick. Um caminho absoluto é necessário se a criação de miniaturas animadas estiver habilitada.</td> 
  </tr> 
  <tr> 
   <td>/libs/settings/dam/v3D/settings/MaxCpuPercentage</td> 
   <td><p>Especifica quantas CPUs são usadas no máximo para processamento de assimilação de ativos 3D.</p> <p>Valores mais altos aceleram as ingestões, mas podem fazer com que o AEM se torne menos responsivo no geral. Esta configuração é aproximada. Ou seja, a precisão aumenta com o número de núcleos de CPU disponíveis.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Definições de configuração do Cloud Services {#cloud-services-configuration-settings}

Os valores para as seguintes configurações são fornecidos pelo gerente de conta do Adobe, especialista em provisionamento ou representante de suporte.

| **Caminho** | **Descrição** |
|---|---|
| `/libs/settings/dam/v3D/services/aws/accountId` | A ID da conta da conta do Adobe AWS. |
| `/libs/settings/dam/v3D/services/aws/bucketName` | O nome do bucket de transferência S3; normalmente `aem3d`. |
| `/libs/settings/dam/v3D/services/aws/customerId` | A id exclusiva atribuída pelo Adobe à sua organização. Usado como ID de usuário do AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/encryptedPassword` | A senha associada a esta customerId. Usado como senha do AWS Cognito. |
| `/libs/settings/dam/v3D/services/aws/region` | A região AWS onde os serviços de nuvem são implantados. |
| `/libs/settings/dam/v3D/services/aws/userPoolId` | A ID do pool de usuários AWS Cognito aplicável. |
| `/libs/settings/dam/v3D/services/dncr/clientId` | A ID do cliente AWS Cognito para o serviço de conversão dncr. |

## Configurações de processamento comuns {#common-processing-settings}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

| **Caminho** | **Descrição** |
|---|---|
| `/libs/settings/dam/v3D/Paths/mayaWorkPath` | O nome e o local da pasta de trabalho para conversão e renderização do Maya. A pasta é criada automaticamente se não existir. |
| `/libs/settings/dam/v3D/Paths/maxWorkPath` | Nome e local da pasta de trabalho para conversão máx. 3ds. A pasta é criada automaticamente se não existir. |
| `/libs/settings/dam/v3D/settings/debugNative` | Defina como **[!UICONTROL true]** para ativar a criação de informações de depuração durante a conversão de formato e renderização com o renderizador RapidRefine. |

## Configuração do renderizador {#renderer-configuration}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

| **Caminho** | **Descrição** |
|---|---|
| `/libs/settings/dam/v3D/settings/dynamicIBL` | Quando definido como **[!UICONTROL true]** e os mapas de luz pré-gerados não estão disponíveis (ou seja, invokeLightMapsOnIngest=false), o renderizador Rapid Refine cria mapas de luz durante a renderização para melhorar a qualidade da renderização. Essa configuração pode aumentar substancialmente o tempo de renderização. Configurar para **[!UICONTROL false]** minimiza o uso da CPU nessas situações, mas pode resultar em uma qualidade de renderização mais baixa. |
| `/libs/settings/dam/v3D/renderers/*/Enabled` | Defina como **[!UICONTROL true]** ou **[!UICONTROL false]** para ativar ou desativar um renderizador, respectivamente. |
| `/libs/settings/dam/v3D/renderers/*/Display` | Permite alterar a sequência de caracteres exibida para um renderizador ativado no seletor Renderizador no painel Renderizar. |
| `/libs/settings/dam/v3D/renderers/*/MaxCpuPercentage` | Especifica quantas CPUs são usadas no máximo para renderizar cenas 3D. Valores mais altos aceleram a renderização, mas podem fazer com que o AEM se torne geral menos responsivo. Esta configuração é aproximada. Ou seja, a precisão aumenta com o número de núcleos de CPU disponíveis. |

## Configurações de visualização de ativos 3D {#d-asset-preview-settings}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

| Caminho | Descrição |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpin` | Defina como **[!UICONTROL true]** ou **[!UICONTROL false]** para ativar ou desativar o giro automático (órbita automática da câmera) no carregamento da página. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Defina como **[!UICONTROL true]** para reiniciar o giro automático depois que **[!UICONTROL Redefinir]** for pressionado. Ignorado quando a rotação automática está desativada. |
| `/libs/settings/dam/v3D/WebGLSites/autoSpinSpeed` | Especifica a velocidade (rotações por minuto) e a direção do giro automático, com valores negativos para a direita para a esquerda e positivos para rotação da esquerda para a direita. |
| `/libs/settings/dam/v3D/WebGL/continueRotate` | Defina como **[!UICONTROL false]** para desativar a continuação com o esmaecimento gradual das respostas do visualizador para gestos de toque e mouse. |
| `/libs/settings/dam/v3D/WebGL/curtainColor` | Especifica a cor da cortina de carregamento que pode, opcionalmente, cobrir a janela de visualização do ativo 3D durante o carregamento e a inicialização. R,G,B valor, com cada componente de cor no intervalo de 0 a 255. |
| `/libs/settings/dam/v3D/WebGL/fadeCurtains` | Quando definida como **[!UICONTROL true]**, a cortina de carregamento desaparecerá gradualmente durante as últimas partes da inicialização do visualizador. Quando definido como **[!UICONTROL false]**, a cortina permanece opaca até que o carregamento e a inicialização sejam concluídos. |
| `/libs/settings/dam/v3D/WebGL/showCurtains` | Defina como **[!UICONTROL true]** ou **[!UICONTROL false]** para ativar ou desativar a cortina de carregamento para visualização de ativos 3D. |
| `/libs/settings/dam/v3D/WebGL/spinHeight` | Quando a rotação automática está ativada e ativa, a posição vertical da câmera é automaticamente ajustada em relação à altura do objeto 3D. Quando definida como 0,5, a câmera será posicionada verticalmente a 1/2 da altura do objeto, o que resultará no horizonte ser centralizado verticalmente no visor. Valores maiores resultam em que a câmera olha para o objeto e aumenta a altura do horizonte renderizado, valores menores resultam em que a câmera olha para o objeto e diminui o horizonte. |

## Configurações do componente Sites 3D {#d-sites-component-settings}

Em **CRXDE Lite** em AEM (**[!UICONTROL Ferramentas > Geral > CRXDE Lite]**), acesse as seguintes configurações:

| Caminho | Descrição |
|---|---|
| `/libs/settings/dam/v3D/WebGLSites/autoSpinAfterReset` | Defina para **[!UICONTROL true]** para reativar o giro automático (órbita automática da câmera) depois que a página inicial for pressionada. Ignorado quando a rotação automática está desativada. |
| `/libs/settings/dam/v3D/WebGLSites/continueRotate` | Defina como **[!UICONTROL false]** para desativar a continuação com o esmaecimento gradual das respostas do visualizador para gestos de toque e mouse. |
| `/libs/settings/dam/v3D/WebGLSites/curtainColor` | Especifica a cor da cortina de carregamento que pode, opcionalmente, cobrir a janela de visualização do componente Sites 3D durante o carregamento. R,G,B valor, com cada componente de cor no intervalo de 0 a 255. |
| `/libs/settings/dam/v3D/WebGLSites/fadeCurtains` | Quando definida como **[!UICONTROL true]**, a cortina de carga desaparecerá gradualmente durante as últimas partes do carregamento e da inicialização. Quando definido como **[!UICONTROL false]**, a cortina permanece opaca até que o carregamento e a inicialização sejam concluídos. |
| `/libs/settings/dam/v3D/WebGLSites/showCurtains` | Defina como **[!UICONTROL true]** ou **[!UICONTROL false]** para ativar ou desativar a cortina de carregamento para o componente Sites 3D. |
| `/libs/settings/dam/v3D/WebGLSites/spinHeight` | Quando a rotação automática está ativada e ativa, a posição vertical da câmera é automaticamente ajustada em relação à altura do objeto 3D. Quando definida como 0,5, a câmera será posicionada verticalmente a 1/2 da altura do objeto, o que resultará no horizonte ser centralizado verticalmente no visor. Valores maiores resultam em que a câmera olha para o objeto e aumenta a altura do horizonte renderizado, valores menores resultam em que a câmera olha para o objeto e diminui o horizonte. |
