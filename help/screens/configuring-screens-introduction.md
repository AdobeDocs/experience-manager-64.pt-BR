---
title: Configuração e implantação de telas AEM
seo-title: Configuração e implantação do Screens
description: O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows. Esta página descreve a configuração e a implantação do AEM Screens e também resume as diretrizes de seleção h/w para o dispositivo do player.
seo-description: O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows. Esta página descreve a configuração e a implantação do AEM Screens e também resume as diretrizes de seleção h/w para o dispositivo do player.
uuid: 8ee5311f-b377-4035-af77-e1391a840745
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: a94d0891-d75f-482e-8d2a-e0cbf953a9de
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Configuring and Deploying AEM Screens{#configuring-and-deploying-aem-screens}

Esta página mostra como instalar e configurar os players do Screens em seus dispositivos e aborda os seguintes tópicos:

* Instalação do AEM Screens Player
* Configuração do servidor
* Diretrizes de seleção de hardware para o dispositivo do player
* Próximas etapas

## Instalação do AEM Screens Player {#installing-aem-screens-player}

O AEM Screens player está disponível para Android, Chrome OS, iOS e Windows.

Para baixar o **AEM Screens Player**, visite a página Downloads [**do **](https://download.macromedia.com/screens/)AEM 6.4 Player.

>[!NOTE]
>
>Depois de baixar o Player mais recente (*.exe*), siga as etapas no player para concluir a instalação ad hoc:
>
>1. Pressione longamente no canto superior esquerdo para abrir o painel admin.
>1. Navegue até **Configuração** no menu de ação esquerdo, digite o endereço de localização da instância do AEM no **Servidor** e clique em **Salvar**.
   >
   >
1. Clique no link **Registro** no menu de ação esquerdo e nas etapas abaixo para concluir o processo de registro do dispositivo.
>



### Additional Resources {#additional-resources}

Consulte os seguintes tópicos para obter informações detalhadas:

* Para baixar o Android Player, visite o **Google Play**. Para saber mais sobre a implementação do Android Watchdog, consulte **[Implementação do Android Player](implementing-android-player.md)**.

* Para implementar o Chrome OS Player, consulte o Console [de gerenciamento do](implementing-chrome-os-player.md) Chrome para obter mais informações.
* Para configurar o AEM Screens Windows player, consulte [Implementação do Windows Player](implementing-windows-player.md).

## Server Configuration {#server-configuration}

>[!NOTE]
>
>**Importante**:
>
>O AEM Screens player não usa o token CSRF (Cross-Site Request Forgery). Portanto, para configurar e o servidor AEM estar pronto para usar para o AEM Screens, ignore o filtro de referenciador permitindo referenciadores vazios.

### Pré-requisitos {#prerequisites}

Os seguintes pontos chave abaixo ajudam a configurar e o servidor AEM a estar pronto para uso no AEM Screens:

#### Permitir solicitações de referenciador vazias {#allow-empty-referrer-requests}

Siga as etapas abaixo para ativar o Filtro de referência Apache Sling que permite vazio. Isso é necessário para a operação ideal do protocolo de controle entre o AEM Screens Player e o servidor AEM Screens.

1. Navegue até **Configuração do console da Web do Adobe Experience Manager **via instância do AEM —> ícone de martelo —> **Operações** —> Console **da** Web.

   ![screen_shot_2019-02-11at15405pm](assets/screen_shot_2019-02-11at15405pm.png)

1. **A Configuração** do console da Web do Adobe Experience Manager é aberta. Procure por sling referrer.

   Para pesquisar a propriedade do referenciador sling, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

   ![screen_shot_2019-02-11at15629pm](assets/screen_shot_2019-02-11at15629pm.png)

1. Marque a opção **Permitir vazio** , conforme mostrado na figura abaixo.

   ![screen_shot_2018-12-04at22911pm](assets/screen_shot_2018-12-04at22911pm.png)

1. Clique em **Salvar** para ativar o Filtro de referência Apache Sling Permitir vazio.

#### Ativar interface de usuário de toque para telas AEM {#enable-touch-ui-for-aem-screens}

O AEM Screens requer a interface de usuário TOQUE e não funcionará com a interface de usuário CLASSIC do Adobe Experience Manager (AEM).

1. Navegue até *&lt;yourAuthorInstance>/system/console/configMgr/com.day.cq.wcm.core.impl.AuthoringUIModeServiceImpl*
1. Certifique-se de que o modo **de criação da interface de usuário** padrão esteja definido como **TOUCH (TOQUE**), como mostrado na figura abaixo

Como alternativa, você também pode executar a mesma configuração usando as ferramentas*&lt;yourAuthorInstance> *->* (ícone de martelo)* -> **Operações** ->Console **da** Web e pesquisar o Serviço **de modo de interface de criação** WCM.

![screen_shot_2018-12-04at22425pm](assets/screen_shot_2018-12-04at22425pm.png)

>[!NOTE]
>
>Você sempre pode ativar a interface clássica para usuários específicos usando as preferências do usuário.

#### AEM no modo de execução NOSAMPLECONTENT {#aem-in-nosamplecontent-runmode}

A execução do AEM na produção usa o modo de execução **NOSAMPLECONTENT** . Remova o cabeçalho *X-Frame-Options=SAMEORIGIN* (na seção do cabeçalho de resposta adicional) de

[http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet](http://localhost:4502/system/console/configMgr/org.apache.sling.engine.impl.SlingMainServlet).

Isso é necessário para que o AEM Screens Player reproduza canais online.

#### Restrições de senha {#password-restrictions}

Com as alterações mais recentes em ***DeviceServiceImpl***, não é necessário remover as restrições de senha.

Você pode configurar ***DeviceServiceImpl*** a partir do link abaixo para habilitar a restrição de senha ao criar a senha para os usuários do dispositivo de telas:

[http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService](http://localhost:4502/system/console/configMgr/com.adobe.cq.screens.device.impl.DeviceService)

Siga as etapas abaixo para configurar ***DeviceServiceImpl***:

1. Navegue até Configuração **do console da Web do** Adobe Experience Manager por meio da instância do AEM —> ícone de martelo —> **Operações** —> Console **da** Web.

1. **A Configuração** do console da Web do Adobe Experience Manager é aberta. Procure o serviço de dispositivos. Para pesquisar a propriedade, pressione **Command+F** para **Mac** e **Control+F** para **Windows**.

![screen_shot_2019-02-21at24951pm](assets/screen_shot_2019-02-21at24951pm.png)

#### Configuração do Dispatcher {#dispatcher-configuration}

Para **Dispatcher, **adicione cabeçalhos de cliente a arquivos .any. Permita que os seguintes cabeçalhos passem:

* &quot;X-Requested-With&quot;
* &quot;X-SET-HEARTBEAT&quot;
* &quot;X-REQUEST-COMMAND&quot;

#### Codificação Java {#java-encoding}

Defina a codificação ****** Java como Unicode. Por exemplo, *Dfile.encoding=Cp1252* não funcionará.

>[!NOTE]
>
>**Recomendação:**
>
>É recomendável usar HTTPS para o AEM Screens Server em uso de produção.

## Diretrizes de seleção de hardware para o dispositivo do player {#hardware-selection-guidelines-for-player-device}

A seção a seguir fornece as diretrizes de seleção de hardware para um projeto do Screens:

* Projetor ou painel de vídeo para o player do PC e para o ***monitor*** ou para o projetor, sempre obtenha componentes do nível comercial ou ***industrial*** .

* Sempre envolva-se com fornecedores que servem o mercado de placas digitais.
* Considere sempre fatores ambientais como temperatura ambiente e umidade relativa.
* Verifique sempre os requisitos de energia e o condicionamento de energia.
* Analise cuidadosamente as necessidades de desempenho e as portas de E/S necessárias para o aplicativo.

A tabela a seguir resume as configurações de hardware com casos de uso típicos de um projeto do AEM Screens:

<table> 
 <tbody> 
  <tr> 
   <td>Configuração do player</td> 
   <td>Processador</td> 
   <td>Memória</td> 
   <td>SSD de armazenamento</td> 
   <td>GPU</td> 
   <td>Exibir</td> 
   <td>E/S</td> 
   <td>Casos de uso típicos</td> 
  </tr> 
  <tr> 
   <td>Básico</td> 
   <td>Processador Intel® Atom dual core, i3 ou quad core básico</td> 
   <td><p>4 GB de memória</p> <p>2 MB de cache</p> </td> 
   <td><p>・ChromeOS 32 GB</p> <p>・ Windows 128GB</p> </td> 
   <td>OnBoard</td> 
   <td>1920x1080</td> 
   <td>DVI, <br /> Ethernet / sem fio,<br /> 2xUSB</td> 
   <td> 
    <ul> 
     <li>Looping padrão em tela cheia <br /> </li> 
     <li>Programação de anúncios</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Padrão</td> 
   <td>Quad Core, processador Intel® Core i5</td> 
   <td><p>8 GB de memória</p> <p>4 MB de cache</p> </td> 
   <td>128 GBB</td> 
   <td>OnBoard</td> 
   <td>3840 x 2160 (4 K)</td> 
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 2xUSB</td> 
   <td> 
    <ul> 
     <li>Conteúdo dinâmico de origem única </li> 
     <li>Interativo simples</li> 
     <li> 1-3 Layouts de zona</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Avançado </td> 
   <td>Quad Core com hyperthreading, processador Intel® Core i7</td> 
   <td><p>16 GB de memória</p> <p>8 MB de cache</p> </td> 
   <td>256 GB</td> 
   <td>GPU Discreta</td> 
   <td>3840 x 2160 (4 K)</td> 
   <td>DVI, HDMI<br /> Ethernet / Wireless,<br /> 4xUSB</td> 
   <td> 
    <ul> 
     <li>4 ou mais zonas de conteúdo, reprodução de vídeo simultâneo</li> 
     <li> Multipáginas interativas</li> 
     <li>Acionadores de dados de várias fontes</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

## Próximas etapas {#the-next-steps}

Depois de instalar e configurar o Reprodutor do Screens, siga os tópicos abaixo para começar:

1. [Criar e gerenciar projetos de telas](creating-a-screens-project.md)
1. [Criar e gerenciar canais](managing-channels.md)
1. [Criar e gerenciar locais](managing-locations.md)
1. [Criar e gerenciar exibições](managing-displays.md)
1. [Atribuir canais](channel-assignment.md)
1. [Gerenciar dispositivos](managing-devices.md)
1. [Registrando um dispositivo](device-registration.md)
1. [Atribuir dispositivos](managing-devices.md)
1. [Criar e gerenciar programações](managing-schedules.md)
1. [Player do AEM Screens](working-with-screens-player.md)
1. [Solução de problemas do Device Control Center](monitoring-screens.md)

