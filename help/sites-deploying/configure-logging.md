---
title: Logs
seo-title: Logging
description: Saiba como configurar parâmetros globais para o serviço de registro central, configurações específicas para os serviços individuais ou como solicitar o registro de dados.
seo-description: Learn how to configure global parameters for the central logging service, specific settings for the individual services or how to request data logging.
uuid: 8c9e3628-2f2c-445d-9706-5c7725b85fe2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 5aa69b10-2cd0-4d34-8104-8c3b88405926
feature: Configuring
exl-id: d94b776d-db06-4f46-ac7f-c3b8e4160b69
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '700'
ht-degree: 1%

---

# Logs{#logging}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

O AEM oferece a possibilidade de configurar:

* parâmetros globais para o serviço de registro central
* Solicitar registro de dados; uma configuração de registro especializada para obter informações de solicitação
* Configurações específicas para cada serviço; por exemplo, um arquivo de log individual e o formato para as mensagens de log

Estas são todas [Configurações do OSGi](/help/sites-deploying/configuring-osgi.md).

>[!NOTE]
>
>Fazer logon AEM é baseado nos princípios do Sling. Consulte [Registro do Sling](https://sling.apache.org/site/logging.html) para obter mais informações.

## Registro global {#global-logging}

[Configuração de registro do Apache Sling](/help/sites-deploying/osgi-configuration-settings.md) é usada para configurar o logger raiz. Isso define as configurações globais para fazer logon AEM:

* o nível de registro
* a localização do ficheiro de registro central
* o número de versões a conservar
* rotação de versão; tamanho máximo ou intervalo de tempo
* o formato a ser usado ao gravar mensagens de log

>[!NOTE]
>
>Essa [Artigo da Base de conhecimento](https://helpx.adobe.com/experience-manager/kb/HowToRotateRequestAndAccessLog.html) explica como girar os arquivos request.log e access.log.

## Registradores e escritores para serviços individuais {#loggers-and-writers-for-individual-services}

Além das configurações de registro global, o AEM permite definir configurações específicas para um serviço individual:

* nível de registro específico
* a localização do ficheiro de registro individual
* o número de versões a conservar
* rotação de versão; tamanho máximo ou intervalo de tempo
* o formato a ser usado ao gravar mensagens de log
* o logger (o serviço OSGi que fornece as mensagens de log)

Isso permite canalizar mensagens de log de um único serviço em um arquivo separado. Isto pode ser particularmente útil durante o desenvolvimento ou testes; por exemplo, quando você precisa de um nível de log aumentado para um serviço específico.

AEM usa o seguinte para gravar mensagens de log no arquivo:

1. Um **Serviço OSGi** (logger) grava uma mensagem de log.
1. A **Logger** O pega essa mensagem e a formata de acordo com sua especificação.
1. A **Gravador de Registro** grava todas essas mensagens no arquivo físico que você definiu.

Esses elementos são vinculados pelos seguintes parâmetros para os elementos apropriados:

* **Logger (logger)**

   Defina os serviços que geram as mensagens.

* **Arquivo de log (registrador de log)**

   Defina o arquivo físico para armazenar as mensagens de log.

   Isso é usado para vincular um Agente de registro a um Escritor de registro. O valor deve ser idêntico ao mesmo parâmetro na configuração do Gravador de log para que a conexão seja feita.

* **Arquivo de log (Gravador de log)**

   Defina o arquivo físico no qual as mensagens de log serão gravadas.

   Isso deve ser idêntico ao mesmo parâmetro na configuração do Gravador de log, ou a correspondência não será feita. Se não houver correspondência, um Escritor implícito será criado com a configuração padrão (rotação diária do log).

### Registradores e escritores padrão {#standard-loggers-and-writers}

Determinados Registradores e Escritores estão incluídos em uma instalação padrão de AEM.

O primeiro é um caso especial, uma vez que controla ambos os `request.log` e `access.log` arquivos:

* O logger:

   * Apache Sling Customizable Request Data Logger

      (org.apache.sling.engine.impl.log.RequestLoggerService)

   * Escreva mensagens sobre o conteúdo da solicitação no `request.log`.

* Links para:

   * Logon de solicitação do Apache Sling

      (org.apache.sling.engine.impl.log.RequestLogger)

   * Grava as mensagens em `request.log` ou `access.log`.

Elas podem ser personalizadas, se necessário, embora a configuração padrão seja adequada para a maioria das instalações.

Os outros pares seguem a configuração padrão:

* O logger:

   * Configuração do Apache Sling Logging Logger

      (org.apache.sling.commons.log.LogManager.fatory.config)

   * Gravações `Information` mensagens para `logs/error.log`.

* Links para o Escritor:

   * Configuração do gravador de log do Apache Sling

      (org.apache.sling.commons.log.LogManager.fatory.writer)

* O logger:

   * Configuração do Apache Sling Logging Logger (org.apache.sling.commons.log.LogManager.fatory.config.649d51b7-6425-45c9-81e6-2697a03d6be7)

   * Gravações `Warning` mensagens para `../logs/error.log` para o serviço `org.apache.pdfbox`.

* Não se vincula a um Escritor específico, portanto, criará e usará um Escritor implícito com configuração padrão (rotação diária do log).

### Criando seus próprios registradores e escritores {#creating-your-own-loggers-and-writers}

Você pode definir seu próprio par de Registrador/Escritor:

1. Crie uma nova instância da Configuração de Fábrica [Configuração do Apache Sling Logging Logger](/help/sites-deploying/osgi-configuration-settings.md).

   1. Especifique o arquivo de log.
   1. Especifique o logger.
   1. Configure os outros parâmetros, conforme necessário.

1. Crie uma nova instância da Configuração de Fábrica [Configuração do gravador de log do Apache Sling](/help/sites-deploying/osgi-configuration-settings.md).

   1. Especifique o Arquivo de Log - deve corresponder ao especificado para o Logger.
   1. Configure os outros parâmetros, conforme necessário.

>[!NOTE]
>
>Em determinadas circunstâncias, talvez você queira criar um [arquivo de log personalizado](/help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file).
