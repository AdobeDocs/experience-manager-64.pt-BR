---
title: Texto de espaço reservado no AEM Forms
seo-title: Placeholder text in AEM Forms
description: O texto de espaço reservado destina-se a ajudar o usuário com a entrada de dados quando o controle não tem valor. Pode ser um valor de amostra ou uma breve descrição do formato esperado.
seo-description: Placeholder text is intended to aid the user with data entry when the control has no value. It could be a sample value or a brief description of the expected format.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: Adaptive Forms
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 3%

---

# Texto de espaço reservado no AEM Forms {#placeholder-text-in-aem-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O texto do espaço reservado representa uma palavra ou frase curta. Destina-se a ajudar o usuário com a entrada de dados quando o controle não tem valor. Um texto de espaço reservado pode ser um valor de amostra ou uma breve descrição do formato esperado. O texto do espaço reservado é mostrado antes que o usuário insira um valor, ele é removido quando o usuário insere ou seleciona um valor.

>[!NOTE]
>
>O texto de espaço reservado, se especificado, deve ter um valor que não contenha caracteres de nova linha.

![Componente de data com e sem texto de espaço reservado](assets/dat-picker-place-holder-text.png)

**A.** Componente de data com texto de espaço reservado **B.** Componente de data sem texto de espaço reservado

O AEM Forms suporta o texto de espaço reservado para os campos Caixa de senha, Seletor de data, Caixa numérica e caixa de texto.\
Os textos de espaço reservado não são suportados para o widget de data HTML5 nativo. Para especificar um texto de Espaço reservado:

1. Clique com o botão direito do mouse em um componente compatível com o Texto de espaço reservado e clique em **Editar**. A caixa de diálogo Editar componente é exibida.

1. Abra o **Título e texto** guia .
1. Especifique uma palavra ou uma frase curta no **Caixa de texto Espaço reservado**. Clique em **OK**.

>[!NOTE]
>
>O texto de espaço reservado não é suportado no Microsoft Internet Explorer 9.
