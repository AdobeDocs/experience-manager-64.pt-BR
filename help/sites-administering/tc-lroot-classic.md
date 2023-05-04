---
title: Criar uma raiz de idioma usando a interface clássica
seo-title: Creating a Language Root Using the Classic UI
description: Saiba como criar uma raiz de idioma usando a interface clássica.
seo-description: Learn how to create a language root using the Classic UI.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
feature: Language Copy
exl-id: 316903a8-22cf-45e6-a9f3-ac1d75beddec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 3%

---

# Criar uma raiz de idioma usando a interface clássica{#creating-a-language-root-using-the-classic-ui}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O procedimento a seguir usa a interface clássica para criar uma raiz de idioma de um site. Para obter mais informações, consulte [Criar uma raiz de idioma](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. No console Sites, na árvore Sites, selecione a página raiz do site. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Adicione uma nova página secundária que represente a versão de idioma do site:

   1. Clique em Nova > Nova página.
   1. Na caixa de diálogo, especifique o Título e o Nome. O Nome precisa estar no formato de `<language-code>` ou `<language-code>_<country-code>`, por exemplo, en, en_US, en_us, en_GB, en_gb.

      * O código de idioma suportado é o código de duas letras em letras minúsculas, conforme definido pelo ISO-639-1
      * O código de país suportado é o código de duas letras em letras minúsculas ou maiúsculas, conforme definido pela ISO 3166
   1. Selecione o modelo e clique em Criar.

   ![newpagefr](assets/newpagefr.png)

1. No console Sites, na árvore Sites, selecione a página raiz do site.
1. No menu Ferramentas, selecione Cópia de idioma.

   ![toolsidiagecopy](assets/toolslanguagecopy.png)

   A caixa de diálogo Cópia de idioma exibe uma matriz de versões de idioma e páginas da Web disponíveis. Um x em uma coluna de idioma significa que a página está disponível nesse idioma.

   ![language agecopydialog](assets/languagecopydialog.png)

1. Para copiar uma página ou árvore de página existente para uma versão de idioma, selecione a célula para essa página na coluna de idioma. Clique na seta e selecione o tipo de cópia a ser criada.

   No exemplo a seguir, a página equipamento/óculos escuros/íris está sendo copiada para a versão em francês.

   ![definagecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Tipo de cópia do idioma | Descrição |
   |---|---|
   | auto | Usa o comportamento de páginas principais |
   | ignorar | Não cria uma cópia desta página e dos seus filhos |
   | `<language>+` (por exemplo, francês+) | Copia a página e todos os seus filhos desse idioma |
   | `<language>` (por exemplo, francês) | Copia somente a página desse idioma |

1. Clique em OK para fechar a caixa de diálogo.
1. Na próxima caixa de diálogo, clique em Sim para confirmar a cópia.
