---
title: Notas de versão AEM 3D
seo-title: Notas de versão AEM 3D
description: Notas de versão específicas para conteúdo 3D no Adobe Experience Manager Assets.
seo-description: Notas de versão específicas para conteúdo 3D no Adobe Experience Manager Assets.
uuid: 6675951f-86f0-4ec5-97e4-d247f6faf913
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
content-type: reference
topic-tags: 3D
discoiquuid: 9789d031-fb7e-415a-a9c3-8b8fde978238
translation-type: tm+mt
source-git-commit: a172fc329a2f73b563690624dc361aefdcb5397e
workflow-type: tm+mt
source-wordcount: '1983'
ht-degree: 0%

---


# Notas de versão AEM 3D {#aem-d-release-notes}

>[!IMPORTANT]
>
>O pacote de recursos 3D AEM no AEM 6.4 não é mais suportado. O Adobe recomenda que você use o recurso de ativos 3D em [AEM como um Cloud Service](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/assets/dynamicmedia/assets-3d.html) ou [AEM 6.5.3 ou superior.](https://docs.adobe.com/content/help/en/experience-manager-65/assets/dynamic/assets-3d.html)

AEM-6.4-DynamicMedia-3D versão 3.1.0 (10 de outubro de 2018)

O pacote de recursos 3D AEM permite suporte para conteúdo 3D no AEM Assets. Ele fornece recursos para carregar, gerenciar, pré-visualização e renderizar ativos 3D. O suporte para exibição e renderização é otimizado para objetos individuais (em vez de cenas complexas com vários objetos).

AEM 3D suporta os tipos de ativos Adobe Dimension (Dn) e glTF. A implementação para esses tipos de ativos é substancialmente diferente da dos tipos 3D tradicionais descritos nesta documentação. Consulte [Trabalhar com ativos](/help/assets/working-dimension-assets.md)da Adobe Dimension.

Também estão incluídas as integrações do lado do servidor com o Autodesk® Maya® (somente Windows). Quando você instala e configura o Maya no mesmo servidor AEM, ativa o suporte para formatos de arquivos Maya nativos, incluindo renderização de alta qualidade com o plug-in NVIDIA® mental ray® Standalone para Maya. A instalação e configuração de 3ds Max no servidor habilita o suporte para o formato de arquivo nativo .max.

Consulte [Integração com a Autodesk Maya](/help/assets/integrate-maya-with-3d.md).

Consulte também [Instalação e configuração AEM ativos](/help/assets/install-config-3d.md) 3D e configurações [](/help/assets/advanced-config-3d.md)avançadas.

Consulte também [Trabalhar com ativos](/help/assets/assets-3d.md)3D.

## Requisitos do sistema {#system-requirements}

**Pré-requisitos**

* AEM 6.4.2 (AEM 6.4 com Service Pack 2)
* Autodesk® FBX® SDK 2016.1.2

**Sistemas operacionais suportados**

* Microsoft Windows 2012 Server ou posterior
* Apple OS X El Capitan 10.6 ou posterior
* RedHat Enterprise Linux 7.3

**Navegadores da Web compatíveis com AEM Assets**

* Google Chrome 53 ou posterior (recomendado).
* Apple Safari 9.1 ou posterior.
* Firefox 48 ou posterior.
* Microsoft Edge 25.10586 ou posterior.

Outros navegadores podem não suportar a visualização interativa de conteúdo 3D no AEM. Somente o Google Chrome suporta sombras projetadas na Pré-visualização.

**Requisitos e recomendações de hardware**

* CPU - Processamento e renderização 3D é muito exigente na CPU do computador. Assim, um servidor contemporâneo com no mínimo oito núcleos de CPU é recomendado.
* Memória - recomenda-se um mínimo de 32 GB.
* Armazenamento em massa - É recomendado o armazenamento SSD de alta largura de banda.

   Durante o upload, os ativos 3D são convertidos em um formato proprietário para visualização rápida e interativa. Dependendo do tipo de ativo 3D, é necessário um espaço de armazenamento de 2 a 3 vezes o tamanho do ativo 3D carregado.

Consulte também [Trabalhar com ativos](/help/assets/assets-3d.md)3D.

## Instalação e configuração AEM 3D {#installing-and-configuring-aem-d}

See [Installing and configuring AEM 3D](/help/assets/install-config-3d.md).

Consulte também [Integração AEM 3D com o Autodesk Maya](/help/assets/integrate-maya-with-3d.md) e [Integração AEM 3D com o Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md).

## Formatos de arquivo 3D suportados {#supported-d-file-formats}

| Formato | Descrição | Plataformas | Notas |
|--- |--- |--- |--- |
| DN | Adobe Dimension | Todos os pacotes | Requer acesso a um serviço de conversão baseado em nuvem. |
| GLTZ | gITF compactado | Todos os pacotes |  |
| GLB | gITF binário | Todos os pacotes | Somente download (as renderizações GLB são criadas para ativos de DN). |
| OBJ | Wavefront OBJ 3D | Todos os pacotes |  |
| FBX | Autodesk FBX (Kaydara Filmbox) | Todos os pacotes | O SDK do Autodesk FBX deve ser instalado no nó Autor. |
| MA, MB | Autodesk Maya | Somente Windows | O Autodesk Maya é necessário no nó Autor para ativar esses formatos de arquivo. Consulte [Integração AEM 3D com o Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| JT | Siemens PLM Open CAD | Somente Windows | O Autodesk Maya é necessário no nó Autor para ativar esses formatos de arquivo. Consulte [Integração AEM 3D com o Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| * | Formatos de entrada 3D adicionais suportados pelo Autodesk Maya podem ser ativados. Consulte [Ativação de formatos adicionais suportados pelo Maya](/help/assets/integrate-maya-with-3d.md#enabling-additional-formats-supported-by-maya). | Somente Windows | O Autodesk Maya é necessário no nó Autor para ativar esses formatos de arquivo. Consulte [Integração AEM 3D com o Autodesk Maya](/help/assets/integrate-maya-with-3d.md). |
| MAX | Máx. de Autodesk 3ds Nativo | Somente Windows | O Autodesk 3ds Max é necessário no nó do autor para ativar esse formato de arquivo. Consulte [Integrar AEM 3D com o Autodesk 3ds Max](/help/assets/integrating-aem-3d-with-autodesk-3ds-max.md). |

## Aprimoramentos e novos recursos {#enhancements-and-new-features}

Versão 3.0

* Suporte para o formato de arquivo nativo Máximo de 3ds do Autodesk.
* Várias alterações e correções de erros para melhorar a estabilidade, a qualidade e a experiência do usuário.
* Configurações movidas para `/libs/settings/dam/v3d/`

Versão 3.1

* Suporte limitado para o formato de arquivo nativo Adobe Dimension (.dn).
* Um novo visualizador 3D para ativos glTF.
* Uma nova interface para um serviço de conversão baseado em nuvem e gerenciado por Adobe hospedado no Amazon AWS. Inicialmente, esse serviço só converte de formatos Dn para glTF.

## Restrições e problemas conhecidos {#restrictions-and-known-issues}

### Suporte Adobe Dimension {#adobe-dimension-support}

* Esta versão do AEM3D tem suporte limitado para arquivos .dn criados com o Adobe Dimension.
* Durante o processamento de upload, AEM aproveita um serviço de conversão baseado em nuvem e hospedado em Adobe para criar uma execução glTF do arquivo .dn nativo. É necessário acessar o serviço de conversão e selecionar pontos de extremidade Amazon AWS.
* Um novo visualizador glTF é fornecido com suporte à visualização de ativos Dn no AEM Assets e em Sites/telas. Ainda não há suporte para os Estágios no visualizador.
* Os modelos Dn podem incorporar luzes IBL e fundos que são exibidos, se presentes. Como alternativa, o visualizador aplica iluminação padrão, uma cor de plano de fundo padrão ou ambos.
* A renderização de alta qualidade para ativos Dn ainda não está disponível.
* Dependências como mapas de textura são incorporadas em ativos Dn e não podem ser gerenciadas explicitamente em AEM.

### Compatibilidade {#compatibility}

* **Não há suporte para a execução como um serviço do Windows (somente Windows)** - isso pode funcionar, mas não foi testado.
* **Dynamic Media** ( `dynamicmedia-scene7` modo) - A compatibilidade do AEM3D com a nova solução Dynamic Media lançada com o AEM 6.4 ainda não foi totalmente verificada. Se o Dynamic Media e o AEM3D estiverem implantados juntos, é recomendável colocar os ativos 3D e suas dependências somente em uma área do repositório AEM Assets que não esteja atribuída ao Dynamic Media. Essa recomendação é especialmente importante para arquivos TIFF de 32 bits que são necessários para estágios 3D, mas não são suportados pelo Dynamic Media.

### Geral {#general}

* **Atalho** Resolver dependências - esse atalho está disponível na Visualização de cartão em ativos 3D. Os cartões de ativos na Visualização de cartão mostram o banner &quot;Dependências não resolvidas&quot;. O atalho abre a guia Propriedades **** básicas em vez da guia **Dependências** . Solução: navegue manualmente até a guia Dependências.

* **Seletor de palco não disponível** - os ativos 3D que incluem luzes são marcados automaticamente por AEM como estágios 3D. Nenhum seletor de Estágios está disponível para estágios na visualização Detalhe. Para marcar um ativo 3D como um objeto 3D, navegue até Propriedades **** básicas, altere Classe **** de ativo para Objeto **** 3D e clique em **Salvar**.

* **Download de ativos 3D com dependentes e execuções** - Ao baixar ativos 3D de AEM com **Dependências** e Representação( **Representações)** marcadas, o download inclui não apenas as representações do ativo 3D principal, mas também as representações de todos os dependentes.

* **Integração** Max de 3ds do Autodesk - A renderização com Max de 3ds não é compatível no momento.

### Restrições de tipo de arquivo {#file-type-restrictions}

* **Arquivos** Mathematica (.ma) - os arquivos Mathematica usam o mesmo sufixo de arquivo que os arquivos Maya nativos. Quando o Feature Pack é instalado e o formato de arquivo .ma do Maya é ativado, a tentativa da AEM3D de assimilar arquivos Mathematica falha. Esses ativos exibem um banner de erro na visualização de cartão.

* **Arquivos** de imagem Targa (.tga) - Arquivos de modelo 3D mais antigos podem incluir referências a arquivos TGA. Este formato não é suportado pelo AEM. O Adobe recomenda converter esses arquivos em um formato diferente antes de fazer upload dos ativos 3D para AEM.
* **Imagens** HDR - as imagens HDR são usadas para estágios com iluminação baseada em imagens (IBL). Atualmente, apenas imagens TIFF de 32 bits são suportadas para essa finalidade.
* **Imagens** TIFF de 32 bits - Imagens TIFF de 32 bits são usadas para estágios com iluminação baseada em imagem. AEM não suporta a criação de execuções para esses ativos, resultando em miniaturas em branco, e a pré-visualização não é possível. O ativo ainda funciona corretamente quando usado com uma etapa IBL.
* **Arquivos** Max (.max) do Autodesk 3ds - se o Autodesk 3ds Max estiver instalado e configurado nos nós do Autor, AEM oferece suporte à ingestão e conversão de arquivos .max. O uso de arquivos .max como estágios não é suportado no momento.

### Resolução automática de dependência {#automatic-dependency-resolution}

* **Dependências de arquivos não resolvidas após o upload** - quando os ativos 3D e seus dependentes são carregados com a mesma operação de upload, é possível que alguns dependentes não sejam resolvidos automaticamente. Esse problema é mais provável de ocorrer se os arquivos dependentes forem grandes. Para corrigir esse problema, acesse a página **Propriedades/Dependências** do ativo que mostra os dependentes não resolvidos após o upload. Os dependentes não resolvidos anteriormente agora devem ser exibidos. Clique em **Salvar** para finalizar o ativo. Para evitar esse problema no futuro, você pode fazer upload de todos os dependentes em uma transação separada antes de fazer upload dos objetos 3D.

* **Diferenciação entre maiúsculas e minúsculas** - A resolução automática de dependência tenta corresponder nomes de arquivos de forma diferenciada entre maiúsculas e minúsculas. Por exemplo, se a dependência original encontrada no ativo 3D for `image.jpg`, a dependência será resolvida para um ativo chamado `Image.jpg`, `image.JPG`ou qualquer outra variação de caso.

### estágios 3D {#d-stages}

* **Miniaturas para estágios** - As miniaturas geradas automaticamente para estágios podem não representar o estágio com precisão.
* **Geometria de palco para estágios** não IBL - O renderizador de Refinamento Rápido não renderiza a geometria de estágios com iluminação não IBL, incluindo planos de fundo e planos de solo. Essa geometria ainda é exibida razoavelmente na visualização Detalhes do ativo (pré-visualização 3D).

* **FBX estágios com iluminação** IBL - é possível fazer upload de estágios FBX com iluminação IBL. No entanto, o formato FBX não tem provisões para transferir o nome da imagem IBL. Dessa forma, a resolução de dependência de arquivos falha. A imagem IBL deve ser atribuída manualmente ao palco após o upload. Você pode atribuir a mesma imagem TIFF de 32 bits às três dependências que são Imagem **de Ambiente de iluminação** difusa, Imagem **de Ambiente de** reflexão e Imagem **de Ambiente de** fundo, ou imagens diferentes podem ser atribuídas.

* **Imagem de plano de fundo de estágios** IBL - Para algumas cenas IBL, a imagem de plano de fundo pode ter qualidade ruim, como ser muito brilhante ou muito indefinida. Para maximizar a qualidade visual do plano de fundo da imagem dos estágios IBL, o Adobe recomenda que você prepare uma imagem JPEG de 8 bits de alta resolução separada e a anexe ao estágio IBL como a Imagem **do Ambiente de** fundo.

* **Imagem preta ao renderizar com o Maya usando um estágio** IBL - Esse problema provavelmente é causado por o Maya não encontrar a dependência de imagem IBL porque a imagem IBL original referenciada pelo palco foi substituída por uma imagem com um nome diferente. Para evitar esse problema, verifique se pelo menos uma das três dependências referenciadas pela etapa do IBL do Maya tem o mesmo nome que a referência do arquivo IBL original no arquivo do Maya.
* **Imagem de plano de fundo revertida para estágio** IBL - As imagens para estágios IBL são intencionalmente giradas horizontalmente para corresponder ao comportamento do renderizador de raio mental NVIDIA fornecido com a Autodesk Maya. Solução: Vire as imagens usadas para estágios IBL no Photoshop antes de carregá-las.
* **Brilho dos estágios** do IBL - A análise automática da imagem IBL pode resultar em uma cena que é muito escura ou muito brilhante. Para ajustar o brilho da iluminação dos estágios IBL, navegue até Propriedades **** básicas e ajuste o valor **brilhante** da iluminação **do** Ambiente, conforme necessário.

### Componente AEM Sites 3D {#aem-sites-d-component}

* **Um componente 3D por página** - No momento, somente uma instância do componente 3D é permitida em cada página da Web. Se mais de um componente 3D for adicionado à mesma página, nenhum dos componentes 3D funcionarão corretamente.
* **visualização 3D ausente ao visualizar em Sites** - ao usar a **Pré-visualização** em Sites, a página deve ser recarregada no navegador para inicializar completamente o visualizador 3D. Esse não é um problema quando você visualização a página da Web diretamente (ou seja, quando `edit.html` é removida do caminho) nos nós Autor ou Publicar.

* **Modo de tela cheia não disponível em dispositivos** iOS - o botão de tela cheia não está disponível em dispositivos iOS, independentemente do navegador usado.

### Publicar conteúdo 3D {#publishing-d-content}

* **Configuração** do componente 3D - você deve instalar o 3D Feature Pack em todos os nós do Publish ativos e cada nó deve ser configurado com **CRXDE Lite** para as mesmas opções de configuração em `/libs/settings/dam/v3D/WebGLSites`.

* **Texturas ausentes, plano de fundo ou iluminação após a publicação** - O mecanismo **Publicar** no AEM Sites publica automaticamente as dependências primárias da página, incluindo o modelo 3D e a etapa 3D referenciada pelo componente 3D. Os estágios 3D e os modelos 3D normalmente dependem de ativos secundários para imagens IBL e mapas de textura, que o mecanismo de publicação de sites não publica automaticamente. Solução: publicar todos os ativos 3D dos Ativos antes de publicar a página da Web dos Sites. Isso garante que todas as dependências para ativos 3D estejam disponíveis nos nós Publicar.
