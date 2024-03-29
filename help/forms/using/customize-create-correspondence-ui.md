---
title: Personalizar criar interface do usuário de correspondência
seo-title: Customize create correspondence UI
description: Saiba como personalizar e criar interface do usuário de correspondência.
seo-description: Learn how to customize create correspondence UI.
uuid: 5b6eb8fd-0270-4638-bdf4-cb7015919d57
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 3efd8f5a-9f38-4d9b-88d6-d8fde6c9a644
feature: Correspondence Management
exl-id: 63cd01d2-a0d5-4f85-b9d2-ec3007ce3fa9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 1%

---

# Personalizar criar interface do usuário de correspondência {#customize-create-correspondence-ui}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

O Gerenciamento de correspondência permite reformular a marca de seu modelo de solução para obter um melhor valor de marca e aderir aos padrões de marca de sua organização. A reformulação da marca da interface do usuário inclui a alteração do logotipo da organização, que é exibido no canto superior esquerdo da interface do usuário Criar correspondência.

Você pode alterar o logotipo na interface do usuário Criar correspondência com o logotipo de sua organização.

![O ícone personalizado na interface do usuário Criar correspondência](assets/0_1_introscreenshot.png)
**Figura:** *O ícone personalizado na interface do usuário Criar correspondência*

### Alteração do logotipo na interface do usuário Criar correspondência {#changing-the-logo-in-the-create-correspondence-ui}

Para configurar uma imagem de logotipo de sua escolha, faça o seguinte:

1. Crie o [estrutura de pastas no CRX](#creatingfolderstructure).
1. [Faça upload do novo arquivo de logotipo](#uploadlogo) na pasta que você criou no CRX.

1. [Configurar o CSS](#createcss) no CRX para fazer referência ao novo logotipo.
1. Limpe o histórico do navegador e [atualizar a interface do usuário Criar correspondência](#refreshccrui).

## Criação da estrutura de pastas necessária {#creatingfolderstructure}

Crie a estrutura de pastas, conforme explicado abaixo, para hospedar a imagem de logotipo personalizada e a folha de estilos. A nova estrutura de pastas com a pasta raiz /apps é semelhante à estrutura da pasta /libs.

Para qualquer personalização, crie uma estrutura de pastas paralela, conforme explicado abaixo, na ramificação /apps.

A ramificação /apps (estrutura de pastas):

* Garante que os arquivos sejam seguros no caso de uma atualização do sistema. No caso de atualização, pacote de recursos ou hotfix, a ramificação /libs é atualizada e, se você hospedar suas alterações na ramificação /libs, elas serão substituídas.
* Ajuda você a não perturbar o sistema/ramificação atual, que pode ser desfeito por engano se você usar os locais padrão para armazenar os arquivos personalizados.
* Ajuda seus recursos a ter prioridade mais alta quando AEM pesquisas por recursos. AEM é configurado para pesquisar primeiro a ramificação /apps e, em seguida, a ramificação /libs para localizar um recurso. Esse mecanismo significa que o sistema usa sua sobreposição (e as personalizações definidas lá).

Use as seguintes etapas para criar a estrutura de pastas necessária na ramificação /apps:

1. Ir para `https://[server]:[port]/[ContextPath]/crx/de` e faça logon como Administrador.
1. Na pasta apps, crie uma pasta chamada `css` com caminho/estrutura semelhante à pasta css (localizada na pasta ccrui).

   Etapas para criar a pasta css:

   1. Clique com o botão direito do mouse no **css** no caminho a seguir e selecione **Nó de sobreposição**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css`

      ![Nó de sobreposição](assets/1_overlaynode_css.png)

   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css

      **Localização da sobreposição:** /apps/

      **Corresponder tipos de nó:** Verificado

      ![Caminho do nó de sobreposição](assets/0_1_5ioverlaynodedialog.png)

      >[!NOTE]
      >
      >Não faça alterações na ramificação /libs. As alterações feitas podem ser perdidas, pois essa ramificação pode ser alterada sempre que você:
      >
      >* Atualizar na sua instância
      >* Aplicar um hotfix
      >* Instalar um pacote de recursos


   1. Clique em **OK**. A pasta css é criada no caminho especificado.

1. Na pasta apps, crie uma pasta chamada `imgs` com caminho/estrutura semelhante à pasta imgs (localizada na pasta ccrui).

   1. Clique com o botão direito do mouse no **imgs** no caminho a seguir e selecione **Nó de sobreposição**: `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs`
   1. Certifique-se de que a caixa de diálogo Sobrepor nó tenha os seguintes valores:

      **Caminho:** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs

      **Localização da sobreposição:** /apps/

      **Corresponder tipos de nó:** Verificado

   1. Clique em **OK**.

      >[!NOTE]
      >
      >Você também pode criar a estrutura de pastas na pasta /apps manualmente.

1. Clique em **Salvar tudo** para salvar as alterações no servidor.

## Faça upload do novo logotipo para o CRX {#uploadlogo}

Faça upload do arquivo de logotipo personalizado para o CRX. As regras de HTML padrão regem a renderização do logotipo. Os formatos de arquivo de imagem compatíveis são compatíveis com o navegador usado para acessar o AEM Forms. Todos os navegadores suportam JPEG, GIF e PNG. Para obter mais informações, consulte a documentação específica do navegador sobre os formatos de imagem suportados.

* As dimensões padrão da imagem do logotipo são 48 px &amp;ast; 48 px. Certifique-se de que a imagem seja semelhante a esse tamanho ou maior que 48 px &amp;ast; 48 px.
* Se a altura da imagem do logotipo for superior a 50 px, a interface do usuário Criar correspondência dimensionará a imagem para uma altura máxima de 50 px, pois essa é a altura do cabeçalho. Ao dimensionar a imagem para baixo, a interface do usuário Criar correspondência mantém a proporção da imagem.
* A interface do usuário Criar correspondência não dimensiona a imagem se ela for pequena, portanto, certifique-se de usar uma imagem de logotipo com pelo menos 48 px de altura e largura suficiente para maior clareza.

Use as seguintes etapas para fazer upload do arquivo de logotipo personalizado para o CRX:

1. Ir para `https://[server]:[port]/[contextpath]/crx/de`. Se necessário, faça logon como Administrador.
1. No CRXDE, clique com o botão direito do mouse no **imgs** no caminho a seguir e selecione **Criar > Criar arquivo**:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/imgs/`

   ![Criar novo nó na pasta imgs](assets/2_contentexplorernewnode.png)

1. Na caixa de diálogo Criar arquivo, digite o nome do arquivo como CustomLogo.png (ou o nome do arquivo de logotipo).

   ![CustomLogo.png como novo nó](assets/3_contentexplorernewnode_customlogo.png)

1. Clique em **Salvar tudo**.

   No novo arquivo que você criou (aqui CustomLogo.png), a propriedade jcr:content é exibida.

1. Clique em jcr:content na estrutura de pastas.

   as propriedades do jcr:content são exibidas.

   ![jcrcontentproperties](assets/jcrcontentproperties.png)

1. Clique duas vezes no botão **jcr:data** propriedade.

   A caixa de diálogo Edit jcr:data é exibida.

   Agora clique na pasta newlogo.png , clique duas vezes em jcr:content (opção dim) e defina o tipo nt:resource. Caso não esteja presente, crie uma propriedade com o nome jcr:content.

1. Na caixa de diálogo Editar jcr:data, clique em **Procurar** e selecione o arquivo de imagem que deseja usar como logotipo (aqui CustomLogo.png).

   Os formatos de arquivo de imagem compatíveis são compatíveis com o navegador usado para acessar o AEM Forms. Todos os navegadores suportam JPEG, GIF e PNG. Para obter mais informações, consulte a documentação específica do navegador sobre os formatos de imagem suportados.

   ![Exemplo de arquivo de logotipo personalizado](assets/geometrixx-outdoors.png)
   **Figura:** *Exemplo - CustomLogo.png a ser usado como o logotipo personalizado*

1. Clique em **Salvar tudo**.

## Criar o CSS para integrar o logotipo à interface do usuário {#createcss}

A imagem de logotipo personalizada requer uma folha de estilos adicional para ser carregada no contexto de conteúdo.

Use as seguintes etapas para configurar a folha de estilos para renderizar o logotipo:

1. Ir para `https://[server]:[port]/[contextpath]/crx/de`. Se necessário, faça logon como Administrador.
1. Crie um arquivo chamado customcss.css (não é possível usar um nome de arquivo diferente) no seguinte local:

   `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/css/`

   Etapas para criar o arquivo customcss.css:

   1. Clique com o botão direito do mouse no **css** e selecione **Criar > Criar arquivo**.
   1. Na caixa de diálogo Novo arquivo , especifique o nome do CSS como `customcss.css`(não é possível usar um nome de arquivo diferente) e clique em **OK**.
   1. Adicione o seguinte código ao arquivo css recém-criado. Em content:url no código, especifique o nome da imagem que você carregou na pasta de imagens no CRXDE.

      ```css
      .logo, .logo:after {
      content:url("../imgs/CustomLogo.png");
      }
      ```

   1. Clique em **Salvar tudo**.

## Atualize a interface do usuário Criar correspondência para ver o logotipo personalizado {#refreshccrui}

Limpe o cache do navegador e abra a instância Criar interface de usuário de correspondência no navegador. Você deve ver o logotipo personalizado.

![Criar interface de usuário de correspondência com logotipo personalizado](assets/0_1_introscreenshot-1.png)
**Figura:** *O ícone personalizado na interface do usuário Criar correspondência*
