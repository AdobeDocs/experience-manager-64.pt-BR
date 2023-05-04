---
title: Configuração das extensões do Acrobat Reader DC para captura de dados
seo-title: Configuring Acrobat Reader DC extensions for data capture
description: Saiba como configurar extensões do Acrobat Reader DC para captura de dados.
seo-description: Learn how to configure Acrobat Reader DC extensions for data capture.
uuid: af6b3c72-601e-4f54-8343-a323eeee5906
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 8f8367fe-a8e9-46ee-a980-1633be02932d
exl-id: 3609ad29-f5b4-4426-8bbc-7c2e38f9b140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# Configuração das extensões do Acrobat Reader DC para captura de dados {#configuring-acrobat-reader-dc-extensions-for-data-capture}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Se os usuários da instalação do AEM forms usarem a funcionalidade de captura de dados do Content Services (obsoleto), é recomendável criar uma função com acesso somente leitura para esses usuários.

***observação**: O Adobe® LiveCycle® Content Services ES (obsoleto) é um sistema de gerenciamento de conteúdo instalado com o LiveCycle. Ele permite que os usuários criem, gerenciem, monitorem e otimizem processos centrados em seres humanos. O suporte aos Serviços de conteúdo (obsoleto) termina em 31/12/2014.

A captura de dados exige que você atribua uma função de usuário para acessar a SampleReaderExtensionsCredential. Você pode atribuir a função de Administrador de Confiança padrão, mas considere que essa função fornece aos usuários gerais e não administrativos privilégios de administrador poderosos que controlam as configurações de Confiança de PKI e gerenciam as Credenciais de PKI, o que poderia comprometer a segurança da instalação dos formulários de AEM em um ambiente de produção. Recomenda-se que o administrador do sistema dos formulários AEM crie uma função que conceda somente leitura ao Armazenamento de Confiança e atribua essa nova função a usuários não administradores que usam captura de dados.

## Criar uma função para usuários de captura de dados {#create-a-role-for-data-capture-users}

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Gerenciamento de funções e, em seguida, clique em Nova função.
1. Insira o nome da função (por exemplo, Usuário da captura de dados) e a descrição nos campos apropriados, em seguida, clique em Avançar.
1. Na tela Permissões de função , clique em Localizar permissões e selecione Leitura de credencial na lista de permissões disponíveis.
1. Clique em OK e depois em Concluir.

## Atribuir a função de captura de dados {#assign-the-data-capture-role}

1. No console de administração, clique em Configurações > Gerenciamento de usuários > Gerenciamento de funções e, em seguida, clique em Localizar.
1. Clique na função de usuário de captura de dados criada.
1. Na guia Usuários/grupos da função , clique em Localizar usuários/grupos.
1. Na tela Localizar usuários e grupos, clique em Localizar, selecione os usuários que exigem a função de usuário de captura de dados e clique em OK.
1. Na tela Editar função , clique em Salvar.
