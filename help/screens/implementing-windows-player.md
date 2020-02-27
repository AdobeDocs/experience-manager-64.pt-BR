---
title: Implementação do Windows 10 Player
seo-title: Implementação do Windows 10 Player
description: 'Siga esta página para saber mais sobre como configurar o AEM Screens Windows 10 player. '
seo-description: 'Siga esta página para saber mais sobre como configurar o AEM Screens Windows 10 player. '
uuid: cdd7e9f1-f836-4d52-8026-80537a6623ca
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
content-type: reference
discoiquuid: 9b66225a-a893-491b-b47c-ae7b3048ed80
translation-type: tm+mt
source-git-commit: c8694726dc29b391a157db3ef230f21517c957bd

---


# Implementação do Windows 10 Player{#implementing-windows-player}

Esta seção descreve como configurar o AEM Screens para o player do Windows 10. Ele fornece informações sobre o arquivo de configuração e as opções disponíveis e recomendações sobre quais configurações usar para desenvolvimento e teste.

## Instalação do Windows Player {#installing-windows-player}

Para implementar o Windows Player para o AEM Screens, instale o Windows Player para o AEM Screens.

Visite a página Downloads [****](https://download.macromedia.com/screens/)do AEM 6.4 Player.

### Método ad-hoc {#ad-hoc-method}

O método Ad-Hoc para instalar o Windows Player mais recente (*.exe*) e visitar a página Downloads [**do **](https://download.macromedia.com/screens/)AEM 6.4 Player.

Depois de baixar o aplicativo, siga as etapas no player para concluir a instalação ad-hoc:

1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
1. Navegue até **Configuração** no menu de ação esquerdo e digite o local (endereço) da instância do AEM à qual deseja se conectar e clique em **Salvar**.

1. Clique no link **Registro** no menu de ação esquerdo para concluir o processo de registro do dispositivo.

### Registrando vários Players do Windows 10 com uma configuração {#registering-multiple-windows-players-with-one-configuration}

Depois de instalar o Windows player, você pode registrar vários players com uma configuração.

>[!NOTE]
>
>**Registro em massa do Windows Player**
>
>Ao implementar o Windows player, não é necessário configurar manualmente cada player. Em vez disso, você pode atualizar o arquivo JSON de configuração depois que ele for testado e estiver pronto para implantação.
>
>A configuração garantirá que todos os players que executam ping no mesmo servidor sejam fornecidos no arquivo de configuração. Você ainda deve registrar cada player manualmente.

Siga as etapas abaixo para configurar o Windows 10 Player:

1. Instale o Windows Player.
1. Localize o arquivo de configuração em ***%appdata%\com.adobe.aem.screens.player\config.json***.
1. Atualize o JSON de configuração usando as informações abaixo e copie a mesma pasta para todos os sistemas em que o player reside.

### Atributos de política {#policy-attributes}

A tabela a seguir resume os atributos de política com um exemplo de política JSON para referência:

| **Nome da política** | **Propósito** |
|---|---|
| server | O URL para o servidor Adobe Experience Manager (AEM). |
| resolução | A resolução do dispositivo. |
| rebootSchedule | O cronograma para reinicializar o player. |
| enableAdminUI | Ative a interface de usuário do administrador para configurar o dispositivo no site. Definido como falso depois que estiver totalmente configurado e em produção. |
| enableOSD | Ative a interface do comutador de canal para que os usuários alternem os canais no dispositivo. Considere a configuração como false depois de estar totalmente configurada e em produção. |
| enableActivityUI | Permite mostrar o progresso de atividades como download e sincronização. Ative para solução de problemas e desabilite-o assim que estiver totalmente configurado e em produção. |

#### Exemplo de arquivo JSON de política {#example-policy-json-file}

```
{
    "server": "http://localhost:4502",
    "resolution": "auto",
    "rebootSchedule": "at 4:00 am",
    "enableAdminUI": false,
    "enableOSD": false,
    "enableActivityUI": false
}
```

