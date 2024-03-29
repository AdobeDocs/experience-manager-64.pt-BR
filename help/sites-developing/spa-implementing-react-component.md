---
title: Implementação de um componente de reação para SPA
seo-title: Implementing a React Component for SPA
description: Este artigo apresenta um exemplo de como adaptar um componente React simples e existente para funcionar com o Editor de SPA de AEM.
seo-description: This article presents an example of how to adapt a simple, existing React component to work with the AEM SPA Editor.
uuid: aebca2ea-a020-45e1-8043-f8c21154c660
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 86a981fe-25f3-451a-b262-8c497619e0ac
exl-id: da0e076b-afb7-4ebe-8e5e-48c00750e453
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 12%

---

# Implementação de um componente de reação para SPA{#implementing-a-react-component-for-spa}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Aplicativos de página única (SPAs) podem oferecer experiências interessantes para usuários de sites. Os desenvolvedores desejam criar sites usando estruturas SPA e os autores desejam editar com facilidade o conteúdo no AEM para um site criado usando estruturas SPA.

O recurso de criação de SPA oferece uma solução abrangente para oferecer suporte à SPA no AEM. Este artigo apresenta um exemplo de como adaptar um componente React simples e existente para funcionar com o Editor de SPA de AEM.

>[!NOTE]
>O recurso Editor de aplicativo de página única (SPA) requer AEM 6.4 service pack 2 ou mais recente.
>
>O Editor de SPA é a solução recomendada para projetos que exigem renderização do lado do cliente baseada em SPA estrutura (por exemplo, Reagir ou Angular).

## Introdução {#introduction}

Graças ao contrato simples e leve que é exigido pelo AEM e estabelecido entre o SPA e o Editor de SPA, tomar uma aplicação Javascript existente e adaptá-la para uso com um SPA em AEM é uma questão simples.

Este artigo ilustra o exemplo do componente meteorológico no SPA de amostra do We.Retail Journal.

Familiarize-se com o [estrutura de um pedido SPA para AEM](/help/sites-developing/spa-getting-started-react.md) antes de ler este artigo.

>[!CAUTION]
>Este documento usa o [Aplicativo de diário We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) apenas para fins de demonstração. Ele não deve ser utilizado ao trabalhar em projetos.
>
>Qualquer projeto do AEM deve utilizar o [Arquétipo de projeto do AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=pt-BR), que aceita projetos SPA que usam o React ou Angular e utiliza o SDK do SPA.

## O Componente Tempo {#the-weather-component}

O componente meteorológico é encontrado no canto superior esquerdo do aplicativo We.Retail Journal. Ele exibe o tempo atual de um local definido, puxando dados meteorológicos dinamicamente.

### Uso do Widget de tempo {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Ao criar o conteúdo do SPA no Editor de SPA, o componente meteorológico aparece como qualquer outro componente AEM, completo com uma barra de ferramentas e é editável.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

A cidade pode ser atualizada em uma caixa de diálogo como qualquer outro componente AEM.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

A alteração é persistente e o componente é atualizado automaticamente com novos dados meteorológicos.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementação do componente meteorológico {#weather-component-implementation}

O componente meteorológico é na verdade baseado em um componente React disponível publicamente, chamado de [React Open Weather](https://www.npmjs.com/package/react-open-weather), que foi adaptado para funcionar como um componente no aplicativo SPA amostra do We.Retail Journal .

A seguir estão trechos da documentação do NPM do uso do componente React Open Weather.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Revisar o código do componente climático personalizado ( `Weather.js`) no aplicativo We.Retail Journal :

* **Linha 16**: O widget React Open Weather é carregado conforme necessário.
* **Linha 46**: O `MapTo` relaciona esse componente React a um componente AEM correspondente para que ele possa ser editado no Editor de SPA.

* **Linhas 22-29**: O `EditConfig` for definida, verificando se a cidade foi preenchida e definindo o valor se estiver vazia.

* **Linhas 31-44**: O componente Tempo estende o `Component` e fornece os dados necessários, conforme definido na documentação de uso do NPM para o componente React Open Weather e renderiza o componente.

```javascript
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ~ Copyright 2018 Adobe Systems Incorporated
 ~
 ~ Licensed under the Apache License, Version 2.0 (the "License");
 ~ you may not use this file except in compliance with the License.
 ~ You may obtain a copy of the License at
 ~
 ~     https://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing, software
 ~ distributed under the License is distributed on an "AS IS" BASIS,
 ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 ~ See the License for the specific language governing permissions and
 ~ limitations under the License.
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
import React, {Component} from 'react';
import ReactWeather from 'react-open-weather';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Weather.css');

const WeatherEditConfig = {

    emptyLabel: 'Weather',

    isEmpty: function() {
        return !this.props || !this.props.cq_model || !this.props.cq_model.city || this.props.cq_model.city.trim().length < 1;
    }
};

class Weather extends Component {

    render() {
        let apiKey = "12345678901234567890";
        let city;

        if (this.props.cq_model) {
            city = this.props.cq_model.city;
            return <ReactWeather key={'react-weather' + Date.now()} forecast="today" apikey={apiKey} type="city" city={city} />
        }

        return null;
    }
}

MapTo('we-retail-journal/global/components/weather')(Weather, WeatherEditConfig);
```

Embora um componente de back-end já deva existir, o desenvolvedor de front-end pode aproveitar o componente React Open Weather no SPA We.Retail Journal com muito pouca codificação.

## Próxima etapa {#next-step}

Para obter mais informações sobre como desenvolver SPA para AEM, consulte o artigo [Desenvolvimento de SPA para AEM](/help/sites-developing/spa-architecture.md).
