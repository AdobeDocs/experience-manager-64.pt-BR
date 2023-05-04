---
title: Quais ambientes de teste são necessários?
seo-title: Which Test Environments are needed?
description: Vários ambientes devem ser considerados como parte do teste
seo-description: Several environments should be considered as part of testing
uuid: bb725e50-edae-4c20-8107-d1c8df2e60e2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: testing
content-type: reference
discoiquuid: db528b9b-3407-462d-8254-20b3cc2c3ccf
exl-id: c3c7c007-4814-4bd1-987e-534df4575a4a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 3%

---

# Quais ambientes de teste serão necessários?{#which-test-environments-will-be-needed}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Para definir quais configurações serão testadas, considere o seguinte:

**Desenvolvimento** - Para Unidade e determinados testes de integração.

**Teste** - Para a maioria dos testes.

**Ao vivo** - Para o desempenho final e os testes de esforço. Também para testes de aceitação com o cliente.

Você também precisará decidir quais instâncias serão necessárias, onde (normalmente, pelo menos uma de cada para todos os níveis de teste):

**Autor** - Essa instância permite que os autores insiram e publiquem conteúdo.

**Publicar** - Essa instância apresenta o site em seu formulário publicado para acesso de visitantes.

Deve ser testado junto com o Dispatcher.

Finalmente, o hardware real deve ser considerado - qualquer teste de desempenho deve ser feito em um sistema o mais próximo possível da configuração do ambiente ativo final. Por isso, também é recomendável dividir o lançamento do projeto em um:

**Lançamento suave** - Redução da disponibilidade; que permite tempo para testes de desempenho, ajuste e otimização em condições realistas no ambiente de produção.

**Inicialização forçada** - Disponibilidade total.
