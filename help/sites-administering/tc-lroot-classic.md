---
title: Criar uma raiz de idioma usando a interface clássica
seo-title: Criar uma raiz de idioma usando a interface clássica
description: Saiba como criar uma raiz de idioma usando a interface clássica.
seo-description: Saiba como criar uma raiz de idioma usando a interface clássica.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---


# Criar uma raiz de idioma usando a interface clássica{#creating-a-language-root-using-the-classic-ui}

O procedimento a seguir usa a interface clássica para criar uma raiz de idioma de um site. Para obter mais informações, consulte [Criação de uma raiz](/help/sites-administering/tc-prep.md#creating-a-language-root)de idioma.

1. No console Sites, na árvore Sites, selecione a página raiz do site. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Adicione uma nova página secundária que representa a versão do idioma do site:

   1. Clique em Nova > Nova página.
   1. Na caixa de diálogo, especifique o Título e o Nome. O Nome precisa estar no formato de `<language-code>` ou, `<language-code>_<country-code>`por exemplo, en, en_US, en_us, en_GB, en_gb.

      * O código de idioma suportado é o código de duas letras em minúsculas, conforme definido pela ISO-639-1
      * O código do país suportado é um código de duas letras em minúsculas ou maiúsculas, conforme definido pela ISO 3166
   1. Selecione o Modelo e clique em Criar.

   ![newpagefer](assets/newpagefr.png)

1. No console Sites, na árvore Sites, selecione a página raiz do site.
1. No menu Ferramentas, selecione Cópia de idioma.

   ![toolslanguage agecopy](assets/toolslanguagecopy.png)

   A caixa de diálogo Cópia de idioma exibe uma matriz de versões de idioma e páginas da Web disponíveis. Um x em uma coluna de idioma significa que a página está disponível nesse idioma.

   ![language agecopydialog](assets/languagecopydialog.png)

1. Para copiar uma página ou árvore de página existente para uma versão de idioma, selecione a célula dessa página na coluna de idioma. Clique na seta e selecione o tipo de cópia a ser criada.

   No exemplo a seguir, o equipamento/óculos escuros/página de íris está sendo copiado para a versão em francês.

   ![language agecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Tipo de cópia linguística | Descrição |
   |---|---|
   | auto | Usa o comportamento das páginas pai |
   | ignore | Não cria uma cópia desta página e dos seus filhos |
   | `<language>+` (por exemplo, francês+) | Copia a página e todos os seus filhos desse idioma |
   | `<language>` (por exemplo, francês) | Copia somente a página desse idioma |

1. Clique em OK para fechar a caixa de diálogo.
1. Na caixa de diálogo seguinte, clique em Sim para confirmar a cópia.

