---
title: Criar e atribuir recursos de habilitação
seo-title: Create and Assign Enablement Resources
description: Adicionar recursos de ativação
seo-description: Add enablement resources
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 9f447a54-4512-41ab-b8d3-327e751eda58
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 5%

---

# Criar e atribuir recursos de habilitação {#create-and-assign-enablement-resources}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Adicionar um recurso de ativação {#add-an-enablement-resource}

Para adicionar um recurso de ativação ao novo site da comunidade:

* Na instância do autor
   * Por exemplo, [http://localhost:4502/](http://localhost:4503/)
* Fazer logon como administrador do sistema
* Na navegação global, selecione **Comunidades > [Recursos](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* Selecione o site da comunidade ao qual os recursos de ativação estão sendo adicionados
   * Selecionar `Enablement Tutorial`
* No menu, selecione ` Create`
* Selecionar **[!UICONTROL Recurso]**

![chlimage_1-201](assets/chlimage_1-201.png)

### Informações básicas {#basic-info}

Preencha as informações básicas do Recurso:

* **[!UICONTROL Nome do site]**: defina para o nome do site da comunidade selecionado: Tutorial de ativação
* **[!UICONTROL Nome do Recurso &amp;;]**: Lição de Esqui 1
* **[!UICONTROL Tags]**: Tutorial: Esportes / Esqui
* **[!UICONTROL Mostrar no catálogo]**: Ligado
* **[!UICONTROL Descrição]**: Deslizando sobre a neve para os principiantes
* **[!UICONTROL Adicionar imagem]**: Adicionar uma imagem para representar o Recurso ao membro na exibição Atribuições
   ![chlimage_1-202](assets/chlimage_1-202.png)
* Selecione **[!UICONTROL Próximo]**

### Adicionar conteúdo {#add-content}

Embora pareça que vários Recursos podem ser selecionados, somente um é permitido.

Selecione o `'+' icon`, no canto superior direito, para iniciar o processo de escolha do Recurso identificando a fonte.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

Faça upload de um recurso. Se um recurso de vídeo, faça o upload de uma imagem personalizada para exibição antes que o vídeo comece a ser reproduzido ou permita que uma miniatura seja gerada a partir do vídeo (pode levar alguns minutos - não é necessário aguardar).

![chlimage_1-205](assets/chlimage_1-205.png)

* select **[!UICONTROL Próximo]**

### Configurações {#settings}

* **[!UICONTROL Configurações sociais]**
Deixe as configurações padrão para experimentar comentários e avaliações dos recursos de ativação pelos alunos.
* **[!UICONTROL Data de vencimento]**

   *(Opcional)* Pode ser selecionada uma data até à qual a atribuição deve ser concluída.
* **[!UICONTROL Autor do recurso]**

   *(Opcional)* Deixe em branco.
* **[!UICONTROL Contato do Recurso &amp;;]**

   *(Obrigatório)* Use o menu suspenso para selecionar o membro `Quinn Harper`.
* **[!UICONTROL Especialista de recurso]**

   *(Opcional)* Deixe em branco.
   **Observação**: se os usuários ou grupos não estiverem visíveis, verifique se eles foram adicionados à variável `Community Enable Members` grupo e *Salvo* na instância de publicação.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* Selecione **[!UICONTROL Próximo]**

### Atribuições {#assignments}

* **[!UICONTROL Adicionar destinatários]**
Deixe indefinido, pois esse recurso de ativação será adicionado a um caminho de aprendizado. Se um aluno for atribuído ao recurso de ativação individual, bem como a um LearningPath contendo o recurso de ativação, o aluno será atribuído ao recurso de ativação duas vezes.

![chlimage_1-207](assets/chlimage_1-207.png)

* Selecione **[!UICONTROL Criar]**

![chlimage_1-208](assets/chlimage_1-208.png)

A criação bem-sucedida do Recurso retorna ao console Recursos com o Recurso recém-criado selecionado. Nesse console, é possível publicar, adicionar alunos e alterar outras configurações.

Para fazer upload de uma nova versão do recurso de ativação, é recomendável criar um novo recurso e, em seguida, cancelar a inscrição dos membros da versão antiga e inscrevê-los na nova versão.

### Publicar o recurso {#publish-the-resource}

Antes de os Inscritos poderem ver o Recurso atribuído, eles devem ser publicados:

* Selecione o mundo `Publish`ícone

A ativação é confirmada com uma mensagem de sucesso:

![chlimage_1-209](assets/chlimage_1-209.png)

## Adicionar um segundo recurso de ativação {#add-a-second-enablement-resource}

Repita as etapas acima para criar e publicar um segundo recurso de ativação relacionado do qual um caminho de aprendizado será criado.

![chlimage_1-210](assets/chlimage_1-210.png)

**Publicar** o segundo recurso.

Retorne à lista Tutorial de ativação de Recursos.

*Dica: se ambos os recursos não estiverem visíveis, atualize a página.*

![chlimage_1-211](assets/chlimage_1-211.png)

## Adicionar um caminho de aprendizado {#add-a-learning-path}

Um caminho de aprendizagem é um agrupamento lógico de recursos de ativação que formam um curso.

* No console Recursos, selecione `+ Create`
* Selecionar **[!UICONTROL Caminho de aprendizado]**

![chlimage_1-212](assets/chlimage_1-212.png)

Adicione o **[!UICONTROL Informações básicas]**:

* **[!UICONTROL Nome do caminho de aprendizado]**: Lições de Esqui
* **[!UICONTROL Tags]**: Tutorial: Esqui
* **[!UICONTROL Mostrar no catálogo]**: deixar desmarcado
* **[!UICONTROL Fazer upload de uma imagem]** para representar o caminho de aprendizagem no console Recursos

![chlimage_1-213](assets/chlimage_1-213.png)

* Selecione **[!UICONTROL Próximo]**

Pule o próximo painel, pois não há caminhos de aprendizado de pré-requisito para adicionar.

* Selecione **[!UICONTROL Próximo]**

No painel Adicionar recursos

* Selecionar `+ Add Resources` para selecionar os 2 recursos de lesões de esqui a serem adicionados ao caminho de aprendizado

   Observação: Somente **publicado** Os recursos serão selecionáveis.

>[!NOTE]
>
>Você só pode selecionar os recursos disponíveis no mesmo nível que o caminho de aprendizagem. Por exemplo, para um caminho de aprendizado criado em um grupo, somente os recursos de nível de grupo estão disponíveis; para um caminho de aprendizado criado em um site da comunidade, os recursos nesse site estão disponíveis para adição ao caminho de aprendizado.

* Selecione **[!UICONTROL Enviar]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* Selecione **[!UICONTROL Próximo]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL Adicionar destinatários]**
Use o menu suspenso para selecionar a variável 
`Community Ski Class` grupo, que deve incluir membros `Riley Taylor` e `Sidney Croft.`

* **[!UICONTROL Contato do Caminho de Aprendizagem &amp;;]**

   *(Obrigatório)* Use o menu suspenso para selecionar o membro `Quinn Harper`.

* Selecione **[!UICONTROL Criar]**

![chlimage_1-217](assets/chlimage_1-217.png)

A criação bem-sucedida do caminho de aprendizado retorna ao console Recursos com o caminho de aprendizado recém-criado selecionado. Nesse console, é possível publicar, adicionar alunos e alterar outras configurações.

**Publicar** o caminho de aprendizado.
