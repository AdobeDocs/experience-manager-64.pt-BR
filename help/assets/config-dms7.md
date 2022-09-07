---
title: Configuração do modo Dynamic Media - Scene7
description: Saiba como configurar o Dynamic Media - Modo Scene7.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: b0f0c6e4-77c8-40db-a9f4-699d1a633571
feature: Configuration,Scene7 Mode
role: Admin,User,Developer
source-git-commit: 4fdb290ddd7493a7ddbe399ebb76189718cff989
workflow-type: tm+mt
source-wordcount: '5614'
ht-degree: 3%

---

# Configuração do modo Dynamic Media - Scene7 {#configuring-dynamic-media-scene-mode}

Se você usar o Adobe Experience Manager configurado para ambientes diferentes, como desenvolvimento, armazenamento temporário e produção ao vivo, será necessário configurar o Dynamic Media Cloud Services para cada ambiente.

## Diagrama de arquitetura do Dynamic Media - Modo Scene7 {#architecture-diagram-of-dynamic-media-scene-mode}

O diagrama de arquitetura a seguir descreve como o modo Dynamic Media - Scene7 funciona.

Com a nova arquitetura, o Experience Manager é responsável pelos principais ativos e sincronizações com o Dynamic Media para processamento e publicação de ativos:

1. Quando o ativo principal é carregado no Experience Manager, ele é replicado para o Dynamic Media. Nesse momento, o Dynamic Media lida com todo o processamento de ativos e a geração de representação, como a codificação de vídeo e as variantes dinâmicas de uma imagem.
1. Depois que as renderizações são geradas, o Experience Manager pode acessar com segurança e visualizar as renderizações remotas do Dynamic Media (nenhum binário é enviado de volta para a instância do Experience Manager).
1. Depois que o conteúdo estiver pronto para ser publicado e aprovado, ele aciona o serviço da Dynamic Media para enviar o conteúdo para os servidores de entrega e armazená-lo em cache no CDN.

![chlimage_1](assets/chlimage_1.png)

## Ativação do Dynamic Media no modo Scene7 {#enabling-dynamic-media-in-scene-mode}

[As mídias dinâmicas são desativadas por padrão. ](https://www.adobe.com/marketing-cloud/enterprise-content-management/dynamic-media.html) Para aproveitar os recursos do Dynamic Media, você deve habilitá-lo.

>[!WARNING]
>
>Dynamic Media - O modo Scene7 é para o *Somente instância Experience Manager Author*. Dessa forma, configure `runmode=dynamicmedia_scene7`na instância Experience Manager Author, *not* a instância Experience Manager Publish .

Para ativar o Dynamic Media, você deve iniciar o Experience Manager usando o `dynamicmedia_scene7` execute o modo a partir da linha de comando inserindo o seguinte em uma janela de terminal (por exemplo, a porta usada é 4502):

```shell
java -Xms4096m -Xmx4096m -Doak.queryLimitInMemory=500000 -Doak.queryLimitReads=500000 -jar cq-quickstart-6.4.0.jar -gui -r author,dynamicmedia_scene7 -p 4502
```

## (Opcional) Migração de predefinições e configurações do Dynamic Media da versão 6.3 para a 6.4 do Zero Down {#optional-migrating-dynamic-media-presets-and-configurations-from-to-zero-downtime}

Se você atualizar o Experience Manager Dynamic Media de 6.3 para 6.4 (que inclui a capacidade de implantações de tempo de inatividade zero), execute o seguinte comando curl para migrar todas as suas predefinições e configurações de `/etc` para `/conf` em CRXDE Lite.

>[!NOTE]
>
>Se você executar a instância do Experience Manager no modo de compatibilidade, ou seja, você tem o pacote de compatibilidade instalado, não é necessário executar esses comandos.

Para migrar as predefinições e configurações personalizadas do `/etc` para `/conf`, execute o seguinte comando curl do Linux®:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets.migratedmcontent.json`

Para todas as atualizações, com ou sem o pacote de compatibilidade, você pode copiar as predefinições do visualizador prontas para uso executando o seguinte comando:

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

## (Opcional) Instalando o feature pack 18912 para a migração de ativos em massa {#installing-feature-pack}

O Feature pack 18912 permite assimilar ativos em massa por meio de FTP ou migrar ativos do Dynamic Media - Modo híbrido ou Dynamic Media Classic para o Dynamic Media - modo Scene7 no Experience Manager. Ele está disponível na Adobe Professional Services.

Consulte [Instalando o feature pack 18912 para a migração de ativos em massa](bulk-ingest-migrate.md) para obter mais informações.

## Configuração do Dynamic Media Cloud Services {#configuring-dynamic-media-cloud-services}

Altere a senha antes de configurar o Dynamic Media Cloud Services. Depois de receber seu email de provisionamento com credenciais do Dynamic Media, você deve [fazer logon](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/intro/dynamic-media-classic-desktop-app.html#system-requirements-dmc-app) para o aplicativo de desktop do Dynamic Media Classic para alterar a senha. A senha fornecida no email de provisionamento é gerada pelo sistema e deve ser apenas uma senha temporária. É importante atualizar a senha para que o Dynamic Media Cloud Service seja configurado com as credenciais corretas.

>[!NOTE]
>
>Por padrão, o caminho de configuração para Cloud Services é `/content/dam`. Nenhum outro caminho de configuração é compatível com o modo Dynamic Media - Scene7.

**Para configurar o Dynamic Media Cloud Services:**

1. Na instância Autor do Experience Manager, toque no logotipo do Experience Manager para acessar o console de navegação global e toque no ícone Ferramentas e, em seguida, toque em **[!UICONTROL Cloud Services]** > **[!UICONTROL Configuração do Dynamic Media]**.
1. Na página Navegador de configuração do Dynamic Media, no painel esquerdo, toque em **[!UICONTROL global]** e tocar **[!UICONTROL Criar]**. Não toque ou selecione o ícone de pasta à esquerda de [!UICONTROL global].
1. No [!UICONTROL Criar configuração do Dynamic Media] digite um título, o endereço de email da conta do Dynamic Media e a senha. Selecione sua região. Essas informações são fornecidas pelo Adobe no email de provisionamento. Entre em contato com o Suporte ao cliente do Adobe se não tiver recebido o email.

   Toque **[!UICONTROL Conectar-se ao Dynamic Media]**.

   >[!NOTE]
   >
   >Depois de receber seu email de provisionamento com credenciais do Dynamic Media, abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon na conta da empresa para alterar a senha. A senha fornecida no email de provisionamento é gerada pelo sistema e deve ser apenas uma senha temporária. É importante atualizar a senha para que o Cloud Service Dynamic Media seja configurado com as credenciais corretas.

1. Se a conexão for bem-sucedida, você também poderá definir o seguinte:

   * **[!UICONTROL Empresa]** - o nome da conta do Dynamic Media.

      >[!IMPORTANT]
      >
      >Somente uma configuração Dynamic Media no Cloud Services é compatível em uma instância do Experience Manager; não adicione mais de uma configuração. Várias configurações do Dynamic Media em uma instância do Experience Manager são _not_ suportado ou recomendado pelo Adobe.<!-- CQDOC-19579 and CQDOC-19612 -->
   * **[!UICONTROL Caminho da pasta raiz da empresa]**
   * **[!UICONTROL Publicar ativos]** - a opção **[!UICONTROL Imediatamente]** significa que, quando os ativos são carregados, o sistema assimila os ativos e fornece o URL/Incorporado instantaneamente. Não há necessidade de intervenção do usuário para publicar ativos. A opção **[!UICONTROL Após ativação]** significa que você deve publicar explicitamente o ativo primeiro antes de um link URL/Incorporar ser fornecido.
   * **[!UICONTROL Servidor de visualização segura]** - permite especificar o caminho do URL para o servidor de visualização de representações seguras. Ou seja, depois que as renderizações são geradas, o Experience Manager pode acessar com segurança e visualizar as renderizações remotas do Dynamic Media (nenhum binário é enviado de volta à instância do Experience Manager).

      A menos que você tenha uma disposição especial para usar o servidor da sua empresa ou um servidor especial, o Adobe recomenda usar a configuração padrão.
   >[!NOTE]
   >
   >Não há suporte para o controle de versão no DMS7. Além disso, a ativação atrasada se aplica somente se **[!UICONTROL Publicar ativos]** na página Editar configuração do Dynamic Media estiver definida como **[!UICONTROL Na ativação]** e, em seguida, somente até a primeira vez que o ativo for ativado.
   >
   >Depois que um ativo é ativado, todas as atualizações são publicadas imediatamente no S7 Delivery.

   ![dynamicmediaconfiguration2atualizado](assets/dynamicmediaconfiguration2updated.png)

1. Toque **[!UICONTROL Salvar]**.
1. Para visualizar com segurança o conteúdo do Dynamic Media antes de ele ser publicado, é necessário &quot;lista de permissões&quot; a instância do autor do Experience Manager para se conectar ao Dynamic Media:

   * Abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta. Suas credenciais e detalhes de logon foram fornecidos pelo Adobe no momento do provisionamento. Caso não tenha essas informações, entre em contato com o Suporte Técnico.
   * Na barra de navegação próxima à parte superior direita da página, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Configuração de publicação]** > **[!UICONTROL Servidor de imagem]**.
   * Na página Publicação do servidor de imagens, na lista suspensa Publicar contexto , selecione **[!UICONTROL Testar o fornecimento de imagem]**.
   * Para o Filtro de endereço do cliente, toque em **[!UICONTROL Adicionar]**.
   * Para ativar (ativar) o endereço, marque a caixa de seleção . Insira o endereço IP da instância Experience Manager Author (não o IP do Dispatcher).
   * Toque **[!UICONTROL Salvar]**.

Agora você terminou com a configuração básica; você está pronto para usar o modo Dynamic Media - Scene7.

Se você quiser personalizar ainda mais sua configuração, poderá, opcionalmente, concluir qualquer uma das tarefas em [(Opcional) Definição das configurações avançadas no Dynamic Media - Modo Scene7](#optional-configuring-advanced-settings-in-dynamic-media-scene-mode).

## (Opcional) Definição das configurações avançadas no Dynamic Media - Modo Scene7 {#optional-configuring-advanced-settings-in-dynamic-media-scene-mode}

Se você quiser personalizar ainda mais a configuração e configuração do Dynamic Media - modo Scene7 ou otimizar seu desempenho, poderá concluir uma ou mais das seguintes tarefas opcionais:

* [(Opcional) Configuração e configuração do Dynamic Media - Configurações do modo Scene7](#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p)

* [(Opcional) Ajuste do desempenho do Dynamic Media - Modo Scene7](#optional-tuning-the-performance-of-dynamic-media-scene-mode)
* [(Opcional) Filtrar ativos para replicação](#optional-filtering-assets-for-replication)

### (Opcional) Configuração e configuração do Dynamic Media - Configurações do modo Scene7</p> {#optional-setup-and-configuration-of-dynamic-media-scene-mode-settings-p}

Quando você estiver em **dynamicmedia_scene7** no modo de execução, use a interface do usuário do Dynamic Media Classic para alterar as configurações do Dynamic Media.

Algumas das tarefas acima exigem que você abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta.

As tarefas de configuração e configuração são:

* [Configuração de publicação para o servidor de imagem](#publishing-setup-for-image-server)
* [Definição das configurações gerais do aplicativo](#configuring-application-general-settings)
* [Configuração do gerenciamento de cores](#configuring-color-management)
* [Edição de tipos MIME para formatos compatíveis](#editing-mime-types-for-supported-formats)
* [Adição de tipos MIME para formatos não suportados](#adding-mime-types-for-unsupported-formats)
* [Criando predefinições de conjuntos de lotes para gerar automaticamente Conjuntos de imagens e Conjuntos de rotação](#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets)

#### Configuração de publicação para o servidor de imagem {#publishing-setup-for-image-server}

As configurações de Configuração de publicação determinam como os ativos são entregues por padrão no Dynamic Media. Se nenhuma configuração for especificada, o Dynamic Media fornece um ativo de acordo com as configurações padrão definidas na Configuração de publicação. Por exemplo, uma solicitação para fornecer uma imagem que não inclua um atributo de resolução gera uma imagem com a configuração Resolução de objeto padrão .

Para configurar a Configuração de publicação: no Dynamic Media Classic, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Configuração de publicação]** > **[!UICONTROL Servidor de imagem]**.

A tela Servidor de imagens estabelece as configurações padrão para entrega de imagens. Consulte a interface do usuário para obter uma descrição de cada configuração.

* **[!UICONTROL Atributos da solicitação]** - Essas configurações impõem limites para imagens que podem ser entregues a partir do servidor.
* **[!UICONTROL Atributos de solicitação padrão]** - Essas configurações pertencem à aparência padrão das imagens.
* **[!UICONTROL Atributos de miniatura comuns]** - Essas configurações pertencem à aparência padrão de miniaturas de imagens.
* **[!UICONTROL Padrões para campos de catálogo]** - Essas configurações pertencem à resolução e ao tipo de miniatura padrão de imagens.
* **[!UICONTROL Atributos do gerenciamento de cores]** - Essas configurações determinam quais perfis de cores ICC serão usados.
* **[!UICONTROL Atributos de compatibilidade]** - Essa configuração permite que os parágrafos anteriores e posteriores em camadas de texto sejam tratados como na versão 3.6 para compatibilidade com versões anteriores.
* **[!UICONTROL Suporte à localização]** - Essas configurações permitem gerenciar vários atributos de localidade. Ela também permite especificar uma sequência de mapa de localidade para que você possa definir quais idiomas deseja suportar para as várias dicas de ferramentas em Visualizadores. Para obter mais informações sobre como configurar o Suporte de localização, consulte [Considerações importantes ao implementar o suporte de localização](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/publish-setup.html#image-server).

#### Definição das configurações gerais do aplicativo {#configuring-application-general-settings}

Para abrir o [!UICONTROL Configurações gerais do aplicativo] na barra Navegação global do Dynamic Media Classic, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Configurações gerais]**.

**[!UICONTROL Servidores]** - Em provisionamento de conta, a Dynamic Media fornece automaticamente os servidores atribuídos para sua empresa. Esses servidores são usados para criar strings de URL para seu site e aplicativos. Essas chamadas de URL são específicas da sua conta do . Não altere nenhum nome de servidor a menos que seja explicitamente instruído a fazê-lo pelo suporte ao Experience Manager.

**[!UICONTROL Substituir imagens]** - O Dynamic Media não permite que dois arquivos tenham o mesmo nome. A ID de URL de cada item (o nome do arquivo menos a extensão) deve ser exclusiva. Essas opções especificam como os ativos de substituição são carregados: se substituem o original ou se tornam duplicatas. Os ativos duplicados são renomeados com um &quot;-1&quot; (por exemplo, chair.tif é renomeado chair-1.tif). Essas opções afetam ativos carregados em uma pasta diferente do original ou ativos com uma extensão de nome de arquivo diferente do original (como JPG, TIF ou PNG).

* **[!UICONTROL Substituir na pasta atual, mesmo nome/extensão de imagem base]** - Essa opção é a regra mais estrita para substituição. Ela requer que você carregue a imagem de substituição na mesma pasta do original e que a imagem de substituição tenha a mesma extensão de nome de arquivo do original. Se esses requisitos não forem cumpridos, será criada uma duplicata.

>[!NOTE]
>
>Para manter a consistência com o Experience Manager, selecione **[!UICONTROL Substituir na pasta atual, mesmo nome/extensão de imagem base]**.

* **[!UICONTROL Substituir em qualquer pasta, mesmo nome/extensão do ativo base]** - Requer que a imagem de substituição tenha a mesma extensão de nome de arquivo que a imagem original (por exemplo, `chair.jpg` replace `chair.jpg` e não `chair.tif`). No entanto, é possível fazer upload da imagem de substituição para uma pasta diferente da original. A imagem atualizada reside na nova pasta; o arquivo não pode mais ser encontrado em seu local original.
* **[!UICONTROL Substituir em qualquer pasta, o mesmo nome do ativo base, independentemente da extensão]** - Essa é a regra de substituição mais inclusiva. Você pode fazer upload de uma imagem de substituição para uma pasta diferente do original, fazer upload de um arquivo com uma extensão de nome de arquivo diferente e substituir o arquivo original. Se o arquivo original estiver em uma pasta diferente, a imagem de substituição residirá na nova pasta para a qual foi carregada.

**[!UICONTROL Perfis de cores padrão]** - Consulte [Configuração do gerenciamento de cores](#configuring-color-management) para obter mais informações.

>[!NOTE]
>
>Por padrão, o sistema mostra 15 execuções ao selecionar **[!UICONTROL Representações]** e 15 predefinições do visualizador ao selecionar **[!UICONTROL Visualizadores]** na exibição detalhada do ativo. Você pode aumentar esse limite. Consulte [Aumento do número de predefinições de imagens exibidas](managing-image-presets.md#increasing-or-decreasing-the-number-of-image-presets-that-display) ou [Aumentar o número de predefinições do visualizador exibidas](managing-viewer-presets.md#increasing-the-number-of-viewer-presets-that-display).

#### Configuração do gerenciamento de cores {#configuring-color-management}

O gerenciamento dinâmico de cores da mídia permite que você corrija os ativos. Com a correção de cores, os ativos assimilados retêm seu espaço de cores (RGB, CMYK, Cinza) e o perfil de cores incorporado. Quando você solicita uma representação dinâmica, a cor da imagem é corrigida no espaço de cores de destino usando CMYK, RGB ou saída Cinza. Consulte [Configuração de predefinições de imagens](managing-image-presets.md).

**Para configurar as propriedades de cores padrão para ativar a correção de cores ao solicitar imagens:**

1. Abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta usando as credenciais fornecidas durante o provisionamento. Navegar para **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]**.
1. Expanda a área **[!UICONTROL Publicar configuração]** e selecione **[!UICONTROL Servidor de imagens]**. Defina **[!UICONTROL Publicar contexto]** como **[!UICONTROL Serviço de imagem]** ao definir padrões para instâncias de publicação.
1. Role até a propriedade que você deve alterar. Por exemplo, uma propriedade no **[!UICONTROL Atributos do gerenciamento de cores]** área.

   Você pode definir as seguintes propriedades de correção de cores:

   * [!UICONTROL Espaço de cores padrão CMYK] - Nome do perfil de cores CMYK padrão
   * [!UICONTROL Espaço de cor padrão de escala de cinza] - Nome do perfil de cor cinza padrão
   * [!UICONTROL Espaço de cores padrão do RGB] - Nome do perfil de cor do RGB padrão
   * [!UICONTROL Propósito de renderização da conversão de cores] - Especifica o propósito de renderização. Os valores aceitáveis são `perceptual`, `relative` `colometric`, `saturation`e `absolute colometric`. Adobe recomenda `relative` como padrão.

1. Toque **[!UICONTROL Salvar]**.

Por exemplo, você pode definir o **[!UICONTROL Espaço de cor padrão RGB]** como `sRGB` e o **[!UICONTROL Espaço de cor padrão CMYK]** como `WebCoated`.

Isso faria o seguinte:

* Habilita a correção de cores para imagens RGB e CMYK.
* Pressupõe-se que as imagens RGB que não têm um perfil de cor estejam na `sRGB` espaço de cores.
* Pressupõe-se que as imagens CMYK que não têm um perfil de cor estejam em `WebCoated` espaço de cores.
* As renderizações dinâmicas que retornam a saída do RGB, a retornam no `sRGB` espaço de cores.
* As renderizações dinâmicas que retornam saída CMYK, retornam no `WebCoated` espaço de cores.

#### Edição de tipos MIME para formatos compatíveis {#editing-mime-types-for-supported-formats}

Você pode definir quais tipos de ativos são processados pelo Dynamic Media e personalizar parâmetros avançados de processamento de ativos. Por exemplo, você pode especificar parâmetros de processamento de ativos para fazer o seguinte:

* Converter um Adobe PDF em um ativo de eCatalog.
* Converta um documento do Adobe Photoshop (.PSD) em um ativo de modelo de banner para personalização.
* Rasterize um arquivo Adobe Illustrator (.AI) ou um arquivo Adobe Photoshop Encapsulated PostScript® (.EPS).
* [Perfis de vídeo](/help/assets/video-profiles.md) e [Perfis de imagem](/help/assets/image-profiles.md) pode ser usada para definir o processamento de vídeos e imagens, respectivamente.

Consulte [Upload de ativos](managing-assets-touch-ui.md#uploading-assets).

**Para editar tipos MIME para formatos compatíveis:**

1. No Experience Manager, toque no logotipo do Experience Manager para acessar o console de navegação global e, em seguida, toque no **[!UICONTROL Ferramentas]** ícone (martelo) e navegue até **[!UICONTROL Geral]** > **[!UICONTROL CRXDE Lite]**.
1. No painel à esquerda, navegue até o seguinte:

   `/conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

   ![mimetypes](assets/mimetypes.png)

1. Em `mimeTypes` selecione um tipo MIME.
1. No lado direito da página CRXDE Lite, na parte inferior:

   * clique duas vezes no **[!UICONTROL ativado]** campo. Por padrão, todos os tipos de ativos mime estão ativados (definido como **[!UICONTROL true]**), o que significa que os ativos são sincronizados com a Dynamic Media para processamento. Se desejar excluir esse tipo de ativo MIME do processamento, altere essa configuração para **[!UICONTROL false]**.
   * clique duas vezes **[!UICONTROL jobParam]** para abrir o campo de texto associado. Consulte [Tipos Mime Suportados](assets-formats.md#supported-mime-types) para obter uma lista de valores de parâmetros de processamento permitidos que você pode usar para um determinado tipo MIME.

1. Siga uma das seguintes opções:

   * Repita as etapas 3 a 4 para editar mais tipos MIME.
   * Na barra de menu da página do CRXDE Lite, toque em **[!UICONTROL Salvar tudo]**.

1. No canto superior esquerdo da página, toque em **[!UICONTROL CRXDE Lite]** para voltar ao Experience Manager.

#### Adição de tipos MIME personalizados para formatos não compatíveis {#adding-custom-mime-types-for-unsupported-formats}

Você pode adicionar tipos MIME personalizados para formatos não compatíveis no Experience Manager Assets. Para garantir que qualquer novo nó adicionado no CRXDE Lite não seja excluído pelo Experience Manager, mova o tipo MIME antes de **[!UICONTROL image_]** e seu valor ativado é definido como **[!UICONTROL false]**.

**Para adicionar tipos MIME personalizados para formatos não suportados:**

1. No Experience Manager, clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Operações]** > **[!UICONTROL Console da Web]**.

   ![Console da Web](assets/2019-08-02_16-13-14.png)

1. Uma nova guia do navegador é aberta para o **[!UICONTROL Configuração do Console da Web do Adobe Experience Manager]** página.

   ![Configuração do console da Web do Experience Manager](assets/2019-08-02_16-17-29.png)

1. Na página , role para baixo até o nome **[!UICONTROL Serviço do tipo MIME do Adobe CQ Scene7 Asset]**. À direita do nome, toque em **[!UICONTROL Editar os valores de configuração]** (ícone de lápis).

   ![Editar os valores de configuração](assets/2019-08-02_16-44-56.png)

1. No **[!UICONTROL Serviço do tipo MIME do Adobe CQ Scene7 Asset]** clique em qualquer ícone de sinal de mais `+`. O local na tabela onde você clica no sinal de mais para adicionar o novo tipo MIME é trivial.

   ![Ícone de sinal de adição](assets/2019-08-02_16-27-27.png)

1. Tipo `DWG=image/vnd.dwg` no campo de texto vazio que você acabou de adicionar.

   O exemplo `DWG=image/vnd.dwg` é somente para fins de demonstração. O tipo MIME adicionado aqui pode ser qualquer outro formato não suportado.

   ![Exemplo de adição de tipo MIME](assets/2019-08-02_16-36-36.png)

1. No canto inferior direito da página, clique em **[!UICONTROL Salvar]**.

   Nesse ponto, você pode fechar a guia do navegador que tem a página de Configuração do Console da Web do Adobe Experience Manager aberta.

1. Retorne à guia do navegador que tem seu console de Experience Manager aberto.

1. No Experience Manager, clique em **[!UICONTROL Ferramentas]** > **[!UICONTROL Geral]** > **[!UICONTROL CRXDE Lite]**.

   ![CRXDE Lite page](assets/2019-08-02_16-55-41.png)

1. No painel à esquerda, navegue até o seguinte:

   `conf/global/settings/cloudconfigs/dmscene7/jcr:content/mimeTypes`

1. Arraste o tipo mime `image_vnd.dwg` e solte-o diretamente acima `image_` na árvore.

   ![Arrastar tipo mime](assets/CRXDELite_CQDOC-14627.png)

1. Com o tipo mime `image_vnd.dwg` ainda selecionado na árvore, da **[!UICONTROL Propriedades]** na guia , no **[!UICONTROL ativado]** , abaixo da **[!UICONTROL Valor]** no cabeçalho da coluna, clique duas vezes no valor para abrir a **[!UICONTROL Valor]** lista suspensa.

1. Tipo `false` no campo (ou selecione `false` na lista suspensa).

   ![Valor falso](assets/2019-08-02_16_60_30.png)

1. Próximo ao canto superior esquerdo da página do CRXDE Lite, clique em **[!UICONTROL Salvar tudo]**.

#### Criando predefinições de conjuntos de lotes para gerar automaticamente Conjuntos de imagens e Conjuntos de rotação {#creating-batch-set-presets-to-auto-generate-image-sets-and-spin-sets}

Use predefinições de conjuntos em lotes para automatizar a criação de conjuntos de imagens ou conjuntos de rotação enquanto os ativos são carregados no Dynamic Media.

Primeiro, defina a convenção de nomenclatura de como os ativos são agrupados em um conjunto. Em seguida, é possível criar uma predefinição de conjunto de lotes, que é um conjunto de instruções autocontido e nomeado exclusivamente, que define como construir o conjunto usando imagens que correspondam às convenções de nomenclatura definidas na receita predefinida.

Ao carregar arquivos, o Dynamic Media cria automaticamente um conjunto com todos os arquivos que correspondem à convenção de nomenclatura definida nas predefinições ativas.

**Configuração da nomenclatura padrão**

Crie uma convenção de nomenclatura padrão que seja usada em qualquer fórmula predefinida de conjunto de lotes. A convenção de nomenclatura padrão selecionada na definição predefinida do conjunto de lotes provavelmente é tudo que sua empresa precisa para gerar conjuntos de lotes. Uma predefinição de conjunto de lotes é criada para usar a convenção de nomenclatura padrão que você define. Você pode criar quantas predefinições do Conjunto de Lotes tiverem as convenções de nomenclatura alternativas e personalizadas necessárias para um conjunto específico de conteúdo, em casos em que há uma exceção na nomenclatura padrão definida pela empresa.

Embora a configuração de uma convenção de nomenclatura padrão não seja necessária para usar a funcionalidade predefinida do conjunto de lotes, você pode usá-la para definir quantos elementos da convenção de nomenclatura você deseja agrupar em um conjunto. Isso ajuda a simplificar a criação de conjuntos em lotes.

Como alternativa, você pode usar **[!UICONTROL Exibir código]** sem campos de formulário disponíveis. Nesta visualização, você cria suas definições de convenção de nomenclatura totalmente usando expressões regulares.

Dois elementos estão disponíveis para definição, **[!UICONTROL Corresponder]** e **[!UICONTROL Nome básico]**. Esses campos permitem definir todos os elementos de uma convenção de nomenclatura e identificar a parte da convenção usada para nomear o conjunto no qual eles estão contidos. A convenção de nomenclatura individual de uma empresa pode usar uma ou mais linhas de definição para cada um desses elementos. Use quantas linhas sua definição exclusiva for usada e as agrupe em elementos distintos. Por exemplo, Imagem principal, Elemento de cor, Elemento de exibição alternativo e Elemento de amostra.

**Para configurar a nomenclatura padrão:**

1. Abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta.

   Suas credenciais e detalhes de logon foram fornecidos pelo Adobe no momento do provisionamento. Caso não tenha essas informações, entre em contato com o Suporte Técnico.

1. Na barra de navegação próxima à parte superior da página, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Predefinições do conjunto de lotes]** > **[!UICONTROL Nomenclatura padrão]**.
1. Selecione **[!UICONTROL Exibir formulário]** ou **[!UICONTROL Exibir código]** para especificar como deseja exibir e inserir informações sobre cada elemento.

   Você pode selecionar a variável **[!UICONTROL Exibir código]** para exibir a criação do valor da expressão regular ao lado das seleções de formulário. É possível inserir ou alterar esses valores para ajudar a definir os elementos da convenção de nomenclatura, se a exibição do formulário limitar você por qualquer motivo. Se os valores não puderem ser analisados na visualização do formulário, os campos do formulário ficarão inativos.

   >[!NOTE]
   >
   >Campos de formulário desativados não executam nenhuma validação para confirmar se as expressões regulares estão corretas. Você verá os resultados da expressão regular que está sendo criada para cada elemento após a linha Resultado. A expressão regular completa é visível na parte inferior da página.

1. Expanda cada elemento conforme necessário e insira as convenções de nomenclatura que deseja usar.
1. Conforme necessário, execute um dos seguintes procedimentos:

   * Toque **[!UICONTROL Adicionar]** para adicionar outra convenção de nomenclatura para um elemento.
   * Toque **[!UICONTROL Remover]** para excluir uma convenção de nomenclatura para um elemento.

1. Siga uma das seguintes opções:

   * Toque **[!UICONTROL Salvar como]** e digite um nome para a predefinição.
   * Toque **[!UICONTROL Salvar]** se você estiver editando uma predefinição existente.

**Criando uma predefinição de conjunto de lotes**

O Dynamic Media usa predefinições de conjuntos em lotes para organizar ativos em conjuntos de imagens (imagens alternativas, opções de cores, rotação 360) para exibição em visualizadores. As predefinições do conjunto de lotes são executadas automaticamente com os processos de upload de ativos no Dynamic Media.

Você pode criar, editar e gerenciar as predefinições do conjunto de lotes. Existem duas formas de definições predefinidas de conjunto de lotes: um para uma convenção de nomenclatura padrão que você configurou e um para convenções de nomenclatura personalizadas que você cria em tempo real.

Você pode usar o método de campo de formulário para definir uma predefinição de conjunto de lotes ou o método de código, que permite usar expressões regulares. Como em Nomenclatura padrão, você pode escolher [!UICONTROL Exibir código] ao mesmo tempo em que você está definindo na variável [!UICONTROL Exibição do formulário] e usar expressões regulares para criar suas definições. Como alternativa, você pode desmarcar qualquer exibição para usar uma ou a outra exclusivamente.

**Para criar uma predefinição de conjunto de lotes:**

1. Abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta.

   Suas credenciais e detalhes de logon foram fornecidos pelo Adobe no momento do provisionamento. Caso não tenha essas informações, entre em contato com o Suporte Técnico.

1. Na barra de navegação próxima à parte superior da página, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Predefinições do conjunto de lotes]** > **[!UICONTROL Predefinição do conjunto de lotes]**.

   [!UICONTROL Exibir formulário], conforme definido no canto superior direito do [!UICONTROL Detalhes] é a exibição padrão.

1. No painel Lista de predefinições , toque em **[!UICONTROL Adicionar]** para ativar os campos de definição no **[!UICONTROL Detalhes]** no lado direito da tela.
1. No **[!UICONTROL Detalhes]** no painel **[!UICONTROL Nome da predefinição]** digite um nome para a predefinição.
1. No **[!UICONTROL Tipo de Conjunto de Lotes]** selecione um tipo predefinido.
1. Siga uma das seguintes opções:

   * Se estiver usando uma convenção de nomenclatura padrão que você configurou anteriormente em **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Predefinições do conjunto de lotes]** > **[!UICONTROL Nomenclatura padrão]**, expandir **[!UICONTROL Convenções de nomenclatura de ativos]** e, em seguida, no **[!UICONTROL Nomenclatura de arquivo]** lista suspensa, toque em **[!UICONTROL Padrão]**.
   * Para definir uma nova convenção de nomenclatura conforme configura a predefinição, **[!UICONTROL Convenções de nomenclatura de ativos]** e, em seguida, no **[!UICONTROL Nomenclatura de arquivo]** lista suspensa, toque em **[!UICONTROL Personalizado]**.

1. Para [!UICONTROL Ordem da sequência], defina a ordem na qual as imagens são exibidas após o conjunto ser agrupado em Dynamic Media.

   Por padrão, os ativos são classificados alfanumérico. No entanto, é possível usar uma lista separada por vírgulas de expressões regulares para definir a ordem.

1. Para **[!UICONTROL Definir nomenclatura]** e **[!UICONTROL Convenção de Criação]**, especifique o sufixo ou prefixo do nome base definido na variável **[!UICONTROL Convenção de nomenclatura de ativos]**. Além disso, defina onde o conjunto é criado na estrutura de pastas do Dynamic Media.

   Se você definir grandes números de conjuntos, mantenha-os separados das pastas que contêm os próprios ativos. Por exemplo, crie uma pasta Conjuntos de imagens e coloque os conjuntos gerados aqui.

1. No **[!UICONTROL Detalhes]** painel, toque em **[!UICONTROL Salvar]**.
1. Toque **[!UICONTROL Ativo]** ao lado do novo nome predefinido.

   Ativar a predefinição garante que, ao fazer upload de ativos no Dynamic Media, a predefinição do conjunto de lotes seja aplicada para gerar o conjunto.

**Criação de uma predefinição de conjunto de lotes para a geração automática de um conjunto de rotação 2D**

Você pode usar o Tipo de Conjunto de Lotes **[!UICONTROL Conjunto de rotação de vários eixos]** para criar uma receita que automatize a geração de Conjuntos de rotação 2D. O agrupamento de imagens usa expressões regulares de Linha e Coluna para que os ativos de imagem sejam alinhados corretamente no local correspondente na matriz multidimensional. Não há um número mínimo ou máximo de linhas ou colunas que você deve ter em um conjunto de rotação de vários eixos.

Por exemplo, suponha que você queira criar um conjunto de rotação de vários eixos chamado `spin-2dspin`. Você tem um conjunto de imagens de conjunto de rotação que contém três linhas, com 12 imagens por linha. As imagens são nomeadas da seguinte maneira:

```
spin-01-01 
 spin-01-02 
 … 
 spin-01-12 
 spin-02-01 
 … 
 spin-03-12
```

Com essas informações, seu [!UICONTROL Tipo de Conjunto de Lotes] A fórmula pode ser criada da seguinte maneira:

![chlimage_1-1](assets/chlimage_1-1.png)

O agrupamento para a parte do nome do ativo compartilhado do conjunto de rotação é adicionado ao **[!UICONTROL Corresponder]** (como destacado). A parte variável do nome do ativo que contém a linha e a coluna é adicionada aos campos **[!UICONTROL Linha]** e **[!UICONTROL Coluna]**, respectivamente.

Quando o Conjunto de rotação é carregado e publicado, você ativa o nome da fórmula do Conjunto de rotação 2D que está listada em **[!UICONTROL Predefinições do conjunto de lotes]** no **[!UICONTROL Fazer upload de opções de trabalho]** caixa de diálogo.

**Para criar uma predefinição de conjunto de lotes para a geração automática de um conjunto de rotação 2D:**

1. Abra o [Aplicativo de desktop do Dynamic Media Classic](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/getting-started/signing-out.html#getting-started), em seguida, faça logon em sua conta.

   Suas credenciais e detalhes de logon foram fornecidos pelo Adobe no momento do provisionamento. Caso não tenha essas informações, entre em contato com o Suporte Técnico.

1. Na barra de navegação próxima à parte superior da página, toque em **[!UICONTROL Configuração]** > **[!UICONTROL Configuração do aplicativo]** > **[!UICONTROL Predefinições do conjunto de lotes]** > **[!UICONTROL Predefinição do conjunto de lotes]**.

   [!UICONTROL Exibir formulário], conforme definido no canto superior direito do [!UICONTROL Detalhes] é a exibição padrão.

1. No **[!UICONTROL Lista de predefinições]** painel, toque em **[!UICONTROL Adicionar]** para ativar os campos de definição no **[!UICONTROL Detalhes]** no lado direito da tela.
1. No **[!UICONTROL Detalhes]** no painel [!UICONTROL Nome da predefinição] digite um nome para a predefinição.
1. No **[!UICONTROL Tipo de Conjunto de Lotes]** , selecione **[!UICONTROL Conjunto de ativos]**.
1. No **[!UICONTROL Subtipo]** , selecione **[!UICONTROL Conjunto de rotação de vários eixos]**.
1. Expandir **[!UICONTROL Convenções de nomenclatura de ativos]** e, em seguida, no **[!UICONTROL Nomenclatura de arquivo]** lista suspensa, toque em **[!UICONTROL Personalizado]**.
1. Use os atributos **[!UICONTROL Correspondência]** e, opcionalmente, **[!UICONTROL Nome de base]** para definir uma expressão regular para nomear ativos de imagem que compõem o agrupamento.

   Por exemplo, a expressão regular Correspondência literal pode ter a seguinte aparência:

   `(w+)-w+-w+`

1. Expandir **[!UICONTROL Posição da Coluna da Linha]** e, em seguida, defina o formato do nome para a posição do ativo de imagem dentro da matriz de Conjunto de rotação 2D.

   Use os parênteses para abraçar a posição da linha ou da coluna no nome do arquivo.

   Por exemplo, para a expressão regular da linha, pode ser semelhante ao seguinte:

   `\w+-R([0-9]+)-\w+`

   ou

   `\w+-(\d+)-\w+`

   Para a expressão regular da coluna, pode ser semelhante ao seguinte:

   `\w+-\w+-C([0-9]+)`

   ou

   `\w+-\w+-C(\d+)`

   Lembre-se de que essas expressões são exemplos somente para fins de demonstração. Você pode criar sua expressão regular da maneira que quiser, de acordo com suas necessidades.

   >[!NOTE]
   >
   >Se a combinação de expressões regulares de linha e coluna não puder determinar a posição do ativo na matriz do conjunto de rotação multidimensional, esse ativo não será adicionado ao conjunto e um erro será registrado.

1. Para **[!UICONTROL Definir nomenclatura]** e **[!UICONTROL Convenção de Criação]**, especifique o sufixo ou prefixo do nome base definido na variável **[!UICONTROL Convenção de nomenclatura de ativos]**.

   Além disso, defina onde o conjunto de rotação é criado na estrutura de pastas do Dynamic Media Classic.

   Se você definir grandes números de conjuntos, mantenha-os separados das pastas que contêm os próprios ativos. Por exemplo, crie uma pasta Conjuntos de rotação para colocar os conjuntos gerados aqui.

1. No **[!UICONTROL Detalhes]** painel, toque em **[!UICONTROL Salvar]**.
1. Toque **[!UICONTROL Ativo]** ao lado do novo nome predefinido.

   Ativar a predefinição garante que, ao fazer upload de ativos no Dynamic Media, a predefinição do conjunto de lotes seja aplicada para gerar o conjunto.

### (Opcional) Ajuste do desempenho do Dynamic Media - Modo Scene7 {#optional-tuning-the-performance-of-dynamic-media-scene-mode}

Para manter o Dynamic Media - modo Scene7 em execução sem problemas, o Adobe recomenda as seguintes dicas de ajuste de desempenho/escalabilidade de sincronização:

* Atualização dos parâmetros de Trabalho predefinidos para processamento de diferentes formatos de arquivo.
* Atualizar os encadeamentos de trabalho de fila predefinidos do fluxo de trabalho Granite (ativos de vídeo).
* Atualização dos threads de trabalho de fila predefinidos do fluxo de trabalho transitório do Granite (imagens e ativos que não são de vídeo).
* Atualização das conexões máximas de upload para o servidor do Dynamic Media Classic.

#### Atualização dos parâmetros de trabalho predefinidos para o processamento de diferentes formatos de arquivo

Você pode ajustar parâmetros de trabalho para processamento mais rápido ao carregar arquivos. Por exemplo, se você carregar arquivos PSD, mas não quiser processá-los como modelos, poderá definir a extração de camada como false (off). Nesse caso, o parâmetro de trabalho ajustado aparece da seguinte maneira: `process=None&createTemplate=false`.

Caso deseje ativar a criação do modelo, use os seguintes parâmetros: `process=MaintainLayers&layerNaming=AppendName&createTemplate=true`.

<!-- REMOVED BASED ON CQDOC-17657 You can tune job parameters for faster processing when you upload files. For example, if you are uploading PSD files, but do not want to process them as templates, you can set layer extraction to false (off). In such case, the tuned job parameter would appear as `process=None&createTemplate=false`. -->

O Adobe recomenda usar os seguintes parâmetros de trabalho &quot;ajustados&quot; para arquivos PDF, PostScript® e PSD:

<!-- OLD PDF JOB PARAMETERS `pdfprocess=Rasterize&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` -->

<!-- OLD POSTSCRIPT JOB PARAMETERS `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Rasterize&airesolution=150&aicolorspace=Auto&aialpha=false` -->

| Tipo de arquivo | Parâmetros de tarefa recomendados |
| ---| ---|
| PDF | `pdfprocess=Thumbnail&resolution=150&colorspace=Auto&pdfbrochure=false&keywords=false&links=false` |
| PostScript® | `psprocess=Rasterize&psresolution=150&pscolorspace=Auto&psalpha=false&psextractsearchwords=false&aiprocess=Thumbnail&airesolution=150&aicolorspace=Auto&aialpha=false` |
| PSD | `process=None&layerNaming=AppendName&anchor=Center&createTemplate=false&extractText=false&extendLayers=false` |

<!-- CQDOC-17657 for PSD entry in table above -->

Para atualizar qualquer um desses parâmetros, siga as etapas em [Ativar o suporte ao parâmetro de trabalho de upload do Dynamic Media Classic/Ativos baseados em tipo MIME](/help/sites-administering/scene7.md#enabling-mime-type-based-assets-scene-upload-job-parameter-support).

#### Atualização da fila de Fluxo de trabalho transitório do Granite {#updating-the-granite-transient-workflow-queue}

A fila Fluxo de trabalho de trânsito do Granite é usada para **[!UICONTROL Ativo de atualização DAM]** fluxo de trabalho. No Dynamic Media, é usado para assimilação e processamento de imagens.

**Para atualizar a fila de Fluxo de trabalho transitório do Granite:**

1. Navegar para [https://&lt;server>/system/console/configMgr](http://localhost:4502/system/console/configMgr) e procurar **[!UICONTROL Fila: Fila de Fluxo de Trabalho Transitório do Granite]**.

   >[!NOTE]
   >
   >Uma pesquisa de texto é necessária em vez de um URL direto porque o PID do OSGi é gerado dinamicamente.

1. No **[!UICONTROL Máximo de trabalhos paralelos]** altere o número para o valor desejado.

   Você pode aumentar **[!UICONTROL Máximo de trabalhos paralelos]** para suportar adequadamente o upload pesado de arquivos para o Dynamic Media. O valor exato depende da capacidade do hardware. Em determinados cenários, como uma migração inicial ou um upload em massa único, você pode usar um valor grande. Esteja ciente, no entanto, de que o uso de um valor grande (como duas vezes o número de núcleos) pode ter efeitos negativos em outras atividades simultâneas. Dessa forma, teste e ajuste o valor com base no seu caso de uso específico.

<!--    By default, the maximum number of parallel jobs depends on the number of available CPU cores. For example, on a 4-core server, it assigns 2 worker threads. (A value between 0.0 and 1.0 is ratio based, or any numbers greater than 1 will assign the number of worker threads.)

   Adobe recommends that 32 **[!UICONTROL Maximum Parallel Jobs]** be configured to adequately support heavy upload of files to Dynamic Media Classic. -->

![chlimage_1](assets/chlimage_1.jpeg)

1. Toque **[!UICONTROL Salvar]**.

#### Atualização da fila do Fluxo de trabalho do Granite {#updating-the-granite-workflow-queue}

A fila Fluxo de trabalho do Granite é usada para fluxos de trabalho não transitórios. No Dynamic Media, ele processava vídeo com a variável **[!UICONTROL Codificar vídeo no Dynamic Media]** fluxo de trabalho.

**Para atualizar a fila do Fluxo de trabalho do Granite:**

1. Navegar para `https://<server>/system/console/configMgr` e procurar **[!UICONTROL Fila: Fila de Fluxo de Trabalho do Granite]**.

   >[!NOTE]
   >
   >Uma pesquisa de texto é necessária em vez de um URL direto porque o PID do OSGi é gerado dinamicamente.

1. No **[!UICONTROL Máximo de trabalhos paralelos]** altere o número para o valor desejado.

   Por padrão, o número máximo de trabalhos paralelos depende do número de núcleos de CPU disponíveis. Por exemplo, em um servidor de 4 núcleos, atribui dois threads de trabalho. (Um valor entre 0,0 e 1,0 é baseado em relação ou qualquer número maior que um atribui o número de threads de trabalho.)

   Para a maioria dos casos de uso, a configuração padrão 0.5 é suficiente.

   ![chlimage_1-1](assets/chlimage_1-1.jpeg)

1. Toque **[!UICONTROL Salvar]**.

#### Atualização da conexão de upload do Scene7 {#updating-the-scene-upload-connection}

A configuração Scene7 Upload Connection sincroniza o Experience Manager Assets com os servidores da Dynamic Media Classic.

**Para atualizar a conexão de upload do Scene7:**

1. Vá até `https://<server>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl`
1. No [!UICONTROL Número de conexões] e/ou o [!UICONTROL Tempo limite do trabalho ativo] altere o número conforme desejado.

   O **[!UICONTROL Número de conexões]** A configuração controla o número máximo de conexões HTTP permitidas para upload do Experience Manager para o Dynamic Media; normalmente, o valor predefinido de dez conexões é suficiente.

   O **[!UICONTROL Tempo limite do trabalho ativo]** determina o tempo de espera para que os ativos carregados do Dynamic Media sejam publicados no servidor de entrega. Esse valor é de 2100 segundos ou 35 minutos por padrão.

   Para a maioria dos casos de uso, a configuração de 2100 é suficiente.

   ![chlimage_1-2](assets/chlimage_1-2.jpeg)

1. Toque **[!UICONTROL Salvar]**.

### (Opcional) Filtrar ativos para replicação {#optional-filtering-assets-for-replication}

Em implantações que não são da Dynamic Media, você replica *all* ativos (imagens e vídeo) do ambiente Experience Manager Author para o nó Experience Manager Publish . Esse workflow é necessário porque os servidores de Publicação do Experience Manager também entregam os ativos.

No entanto, em implantações do Dynamic Media, como os ativos são fornecidos por meio do Cloud Service, não há necessidade de replicar esses mesmos ativos para nós de publicação do Experience Manager. Esse workflow de &quot;publicação híbrida&quot; evita custos de armazenamento extras e tempos de processamento mais longos para replicar ativos. Outros conteúdos, como páginas do Site, continuam a ser veiculados a partir dos nós de Publicação do Experience Manager .

Os filtros fornecem uma maneira de *exclude* ativos de serem replicados para o nó de publicação do Experience Manager.

#### Uso de filtros de ativos padrão para replicação {#using-default-asset-filters-for-replication}

Se você estiver usando o Dynamic Media para geração de imagens, ou vídeo, ou ambos, poderá usar os filtros padrão que o Adobe fornece como estão. Os seguintes filtros estão ativos por padrão:

<table> 
 <tbody> 
  <tr> 
   <td> </td> 
   <td><strong>Filtro</strong></td> 
   <td><strong>Mimetype</strong></td> 
   <td><strong>Representações</strong></td> 
  </tr> 
  <tr> 
   <td>Entrega de imagem do Dynamic Media</td> 
   <td><p>filter-images</p> <p>conjuntos de filtros</p> <p> </p> </td> 
   <td><p>Começa com <strong>image/</strong></p> <p>Contém <strong>application/</strong> e termina com <strong>set</strong>.</p> </td> 
   <td>As "imagens-filtro" prontas para uso (aplica-se a ativos de imagens individuais, incluindo imagens interativas) e "conjuntos de filtros" (aplica-se a Conjuntos de rotação, Conjuntos de imagens, Conjuntos de mídia mista e Conjuntos de carrossel): 
    <ul> 
     <li>Excluir da replicação a imagem original e as representações de imagem estática.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Entrega de vídeo do Dynamic Media</td> 
   <td>filter-video</td> 
   <td>Começa com <strong>video/</strong></td> 
   <td>O "filter-video" pronto para uso: 
    <ul> 
     <li>Exclua da replicação do vídeo original e das representações estáticas de miniatura.<br /> <br /> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>Os filtros se aplicam aos tipos MIME e não podem ser específicos de caminho.

#### Personalização de filtros de ativos para replicação {#customizing-asset-filters-for-replication}

1. No Experience Manager, toque no logotipo do Experience Manager para acessar o console de navegação global e toque no **[!UICONTROL Ferramentas]** e navegue até **[!UICONTROL Geral]** > **[!UICONTROL CRXDE Lite]**.
1. Na árvore da pasta esquerda, navegue até `/etc/replication/agents.author/publish/jcr:content/damRenditionFilters` para analisar os filtros.

   ![chlimage_1-2](assets/chlimage_1-2.png)

1. Para definir o Tipo MIME para o filtro, você pode localizar o Tipo MIME da seguinte maneira:

   No painel esquerdo, expanda **[!UICONTROL conteúdo]** > **[!UICONTROL barragem]** > **[!UICONTROL &lt;`locate_your_asset`>]** > **[!UICONTROL jcr:content]** > **[!UICONTROL metadados]** e, em seguida, na tabela à direita, localize **[!UICONTROL dc:format]**.

   O gráfico a seguir é um exemplo do caminho de um ativo para dc:format.

   ![chlimage_1-3](assets/chlimage_1-3.png)

   Observe que a variável `dc:format` para o ativo `Fiji Red.jpg` é `image/jpeg`.

   Para que esse filtro se aplique a todas as imagens, independentemente do formato, defina o valor como `image/*` em que `*` é uma expressão regular aplicada a todas as imagens de qualquer formato.

   Para que o filtro seja aplicado somente às imagens do JPEG de tipo , insira um valor de `image/jpeg`.

1. Defina quais representações deseja incluir ou excluir da replicação.

   Os caracteres que você pode usar para filtrar para replicação incluem:

   <table> 
    <tbody> 
    <tr> 
    <td><strong>Caractere a ser usado</strong></td> 
    <td><strong>Como ele filtra ativos para replicação</strong></td> 
    </tr> 
    <tr> 
    <td>*</td> 
    <td>Caracteres curingas<br /> </td> 
    </tr> 
    <tr> 
    <td>+</td> 
    <td>Inclui ativos para replicação.</td> 
    </tr> 
    <tr> 
    <td>-</td> 
    <td>Exclui ativos da replicação.</td> 
    </tr> 
    </tbody> 
   </table>

   Navegar para **content/dam/&lt;`locate your asset`>/jcr:content/renditions**.

   O gráfico a seguir é um exemplo das representações de um ativo.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   Se você quiser apenas replicar o original, insira `+original`.
