---
title: '"Gerenciamento de correspondência: Solução de problemas"'
seo-title: Solução de problemas do gerenciamento de correspondência
description: Solução de problemas do gerenciamento de correspondência
seo-description: Solução de problemas do gerenciamento de correspondência
uuid: 25828cdd-110e-4a84-8f31-d82cd610a54f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cc473808-e71a-4834-bb30-91e6df783e60
feature: Correspondence Management
translation-type: tm+mt
source-git-commit: 75312539136bb53cf1db1de03fc0f9a1dca49791
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 6%

---


# Gerenciamento de correspondência: Solução de problemas {#correspondence-management-troubleshooting}

## Erros ao salvar uma letra {#errors-when-saving-a-letter}

### Problema {#issue}

Um dos seguintes erros é exibido ao salvar uma carta:

* O vínculo de dados não está presente para o módulo de texto
* Forneça a informação de propriedade necessária para o seguinte

### Motivo {#reason}

Esses erros podem ocorrer devido a um dos seguintes:

* Um dicionário de dados está vinculado à carta, mas não está presente no servidor.
* Um dicionário de dados é vinculado à letra, mas tem um sublinhado (_) em seu nome.

### Solução alternativa {#workaround}

Certifique-se de que o dicionário de dados que você está usando na carta esteja presente no servidor e não tenha um sublinhado (_) em seu nome.

## Erro ao visualizar uma carta {#error-when-previewing-a-letter}

### Problema {#issue-1}

Ao visualizar uma carta, o erro &quot;Erro na carta de carregamento: Não foi possível importar o ativo da entrada XML&quot; é exibido mesmo quando um ativo de texto não publicado anteriormente na carta é publicado.

### Solução alternativa {#workaround-1}

Redefina o cache de letras na instância de publicação usando as seguintes etapas e tente visualizar novamente a carta:

1. Vá para **`https://[server]:[port]/[contextPath]/system/console/configMgr`** e faça logon como Administrador.
1. Selecione **Configurações de gerenciamento de correspondência**.
1. Em **Configurações de Gerenciamento de Correspondência**, desative **Ativar Cache de Carta** e clique em **Salvar.**
1. Ative **Ativar Cache de Carta** e clique em **Salvar**.
1. Tente novamente visualizar a carta.

