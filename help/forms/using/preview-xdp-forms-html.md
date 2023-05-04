---
title: Gerar visualização de HTML5 de um formulário XDP
seo-title: Generate HTML5 preview of an XDP form
description: A guia Visualizar HTML no LiveCycle Designer pode ser usada para visualizar formulários como eles aparecem em um navegador.
seo-description: Preview HTML tab in LiveCycle Designer can be used to preview forms as they appear in a browser.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
feature: Mobile Forms
exl-id: f855d3f9-cf3c-4883-b82b-d607250c3dae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 2%

---

# Gerar visualização de HTML5 de um formulário XDP {#generate-html-preview-of-an-xdp-form}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Ao projetar um formulário no AEM Forms Designer, além de visualizar a representação de PDF de um formulário, você também pode visualizar uma representação de HTML5 dele. Você pode usar o **Visualizar HTML** para visualizar um formulário como ele apareceria em um navegador.

## Ativar a Visualização do HTML para formulários XDP no Designer {#html-preview-of-forms-in-forms-designer}

Para permitir que o Designer gere a visualização de HTML de formulários XDP, execute as seguintes configurações:

* Configurar o serviço de autenticação do Apache Sling
* Desativar modo protegido
* Fornecer detalhes do servidor AEM Forms

### Configurar o serviço de autenticação do Apache Sling {#configure-apache-sling-authentication-service}

1. Ir para `https://[server]:[port]/system/console/configMgr` no AEM Forms em execução no OSGi ou

   `https://[server]:[port]/lc/system/console/configMgr` no AEM Forms em execução no JEE.

1. Localize e clique em **Serviço de autenticação do Apache Sling** para abri-la no modo de edição.

1. Dependendo de você estar executando o AEM Forms em OSGi ou JEE, adicione o seguinte no **Requisitos de autenticação** campo :

   * AEM Forms no JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM Forms no OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Não copie e cole o valor especificado no campo Requisitos de autenticação , pois ele pode corromper os caracteres especiais no valor. Em vez disso, digite o valor especificado no campo .

1. Especifique um nome de usuário e senha em **[!UICONTROL Nome de usuário anônimo]** e **[!UICONTROL Senha do usuário anônimo]** , respectivamente. As credenciais especificadas são usadas para lidar com autenticação anônima e permitir acesso a usuários anônimos.
1. Clique em **Salvar** para salvar a configuração.

### Desativar modo protegido {#disable-protected-mode}

O [modo protegido](/help/forms/using/get-xdp-pdf-documents-aem.md) está ativada, por padrão. Mantenha-o ativado para os ambientes de produção. Você pode desativá-lo em um ambiente de desenvolvimento para visualizar o HTML5 Forms no Designer. Execute as seguintes etapas para desativá-lo:

1. Faça logon no Console da Web AEM como administrador.

   * URL para AEM Forms em OSGi é `https://[server]:[port]/system/console/configMgr`
   * O URL para AEM Forms no JEE é `https://[server]:[port]/lc/system/console/configMgr`

1. Abrir **[!UICONTROL Configurações do Mobile Forms]** para edição.
1. Desmarque a opção **[!UICONTROL Modo protegido]** e clique em **[!UICONTROL Salvar]**.

### Fornecer detalhes do servidor AEM Forms {#provide-details-of-aem-forms-server}

1. No Designer, acesse **Ferramentas** >  **Opções**.
1. Na janela Opções, selecione **Opções de servidor** forneça os detalhes a seguir e clique em **OK**.

   * **URL do servidor**: URL do servidor AEM Forms.
   * **Número da porta HTTP**: AEM porta do servidor. O valor padrão é 4502.
   * **Contexto de visualização do HTML:** Caminho do perfil para renderizar formulários XFA. Os perfis padrão a seguir são usados para visualizar o formulário no Designer. No entanto, também é possível especificar o caminho para um perfil personalizado.

      * `/content/xfaforms/profiles/default.html` (AEM Forms no OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms no JEE)
   * **Contexto do Forms Manager:** Caminho do contexto no qual a interface do usuário do Forms Manager é implantada. Os valores padrão são:

      * `/aem/forms` (AEM Forms no OSGi)
      * `/lc/forms` (AEM Forms no JEE)

   **Observação:** *Certifique-se de que o servidor do AEM Forms esteja funcionando. A visualização do HTML se conecta ao servidor CRX para* generate *uma pré-visualização.*

   ![Opções do AEM Forms Designer ](assets/server_options.png)

   Opções do AEM Forms Designer

1. Para visualizar um formulário no HTML, clique no **Visualizar HTML** guia .

   >[!NOTE]
   >
   >Se a guia HTML Preview estiver fechada, pressione F4 para abrir a guia Preview HTML. Você também pode selecionar Visualizar HTML no menu Visualizar para abrir a guia Visualizar HTML.

   >[!NOTE]
   >
   >A visualização HTML não oferece suporte a documentos PDF, a visualização HTML é apenas para documentos XDP.

## Visualização de formulário usando dados de amostra {#to-preview-a-form-using-sample-data}

O Designer permite que você visualize e teste seu formulário usando dados XML de amostra. É recomendável testar frequentemente seu formulário com dados de amostra para garantir que ele seja renderizado corretamente.

Se você não tiver dados de amostra, o Designer poderá criá-los ou você mesmo poderá criá-los. (Consulte [Geração automática de dados de amostra para visualizar um formulário](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) e [Para criar dados de amostra para visualizar um formulário](https://help.adobe.com/en_US/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Testar seu formulário usando uma fonte de dados de amostra garante que os dados e campos sejam mapeados e que os subformulários repetitivos se repitam conforme o esperado. É possível criar um layout de formulário equilibrado que forneça o espaço apropriado para cada objeto exibir os dados unidos.

1. Selecionar **Arquivo > Propriedades do formulário**.

1. Clique no botão **Visualizar** e, na caixa Arquivo de dados, digite o caminho completo para o arquivo de dados de teste. Você também pode usar o botão Procurar para navegar até o arquivo.

1. Clique em **OK**. Na próxima vez que você visualizar o formulário na **Visualizar HTML** , os valores de dados do arquivo XML de amostra aparecerão nos respectivos objetos.

## Visualizar formulários localizados em um repositório {#html-preview-of-forms-in-forms-manager}

No AEM Forms, é possível visualizar formulários e documentos em um repositório. A visualização ajuda a saber exatamente como os formulários se parecem e se comportam conforme serão usados pelos usuários finais.

[**Entre em contato com o suporte**](https://www.adobe.com/account/sign-in.supportportal.html)
