---
title: Solucionar problemas do AEM durante a criação
seo-title: Troubleshooting AEM when Authoring
description: Alguns problemas que podem ocorrer ao usar o AEM
seo-description: Some issues that you might encounter when using AEM
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
exl-id: b0890070-c9e8-4ce4-9149-00c8c38298ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 41%

---

# Solucionar problemas do AEM durante a criação  {#troubleshooting-aem-when-authoring}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

A seção a seguir aborda alguns problemas que você poderá enfrentar ao usar o AEM, junto com sugestões sobre como resolvê-los.

>[!NOTE]
>
>Ao enfrentar problemas, também vale a pena verificar a lista de [Problemas conhecidos](/help/release-notes/known-issues.md) para sua instância (pacotes de versões e serviços).

>[!NOTE]
>
>Os usuários que tiverem privilégios de administrador e quiserem resolver problemas com o AEM, poderão utilizar os métodos de resolução de problemas descritos em [AEM de solução de problemas (para administradores)](/help/sites-administering/troubleshoot.md). Se você não tiver privilégios suficientes, consulte o administrador do sistema sobre AEM de solução de problemas.

## A versão antiga da página ainda está no site publicado {#old-page-version-still-on-published-site}

* **Problema**:

   * Você fez alterações em uma página e replicou a página para o site de publicação, mas a variável *old* A versão da página ainda está sendo exibida no site de publicação.

* **Motivo**:

   * Isso pode ter várias causas, na maioria das vezes o cache (seu navegador local ou o Dispatcher), embora, às vezes, possa ser um problema com a fila de replicação.

* **Soluções**:

   * Há várias possibilidades aqui:
   * Confirme se a página foi replicada corretamente. Verifique o status da página e, se necessário, o estado da fila de replicação.
   * Limpar o cache no seu navegador local e acessar a página novamente.
   * Adicionar `?` ao final do URL da página. Por exemplo:

      * `http://localhost:4502/sites.html/content?`
      * Isso solicitará a página diretamente do AEM e ignorará o Dispatcher. Se você receber a página atualizada, isso será uma indicação de que é necessário limpar o cache do Dispatcher.
   * Entre em contato com o administrador do sistema se houver problemas com as filas de replicação.


## Ações de componentes não visíveis na barra de ferramentas {#component-actions-not-visible-on-toolbar}

* **Problema**:

   * A ampla variedade de ações aplicáveis do componente não é visível ao editar uma página de conteúdo no ambiente do autor. 

* **Motivo**:

   * Em casos raros, uma ação anterior pode afetar a barra de ferramentas.

* **Solução**:

   * Atualize a página.
