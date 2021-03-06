---
title: Implementação de um componente de reação para SPA
seo-title: Implementação de um componente de reação para SPA
description: Este artigo apresenta um exemplo de como adaptar um componente React simples e existente para trabalhar com o Editor de SPA AEM.
seo-description: Este artigo apresenta um exemplo de como adaptar um componente React simples e existente para trabalhar com o Editor de SPA AEM.
uuid: aebca2ea-a020-45e1-8043-f8c21154c660
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 86a981fe-25f3-451a-b262-8c497619e0ac
translation-type: tm+mt
source-git-commit: 8daa8943ccbca46c54f9dd7f1a25259a22a4b42f
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 2%

---


# Implementação de um componente de reação para SPA{#implementing-a-react-component-for-spa}

Aplicativos de página única (SPA) podem oferta experiências interessantes para usuários de sites. Os desenvolvedores querem ser capazes de criar sites usando estruturas SPA e os autores querem editar o conteúdo no AEM para um site criado usando estruturas SPA.

O recurso de criação de SPA oferta uma solução abrangente para suportar SPA dentro do AEM. Este artigo apresenta um exemplo de como adaptar um componente React simples e existente para trabalhar com o Editor de SPA AEM.

>[!NOTE]
>O recurso Editor de aplicativo de página única (SPA) requer AEM 6.4 service pack 2 ou mais recente.
>
>O Editor de SPA é a solução recomendada para projetos que exigem renderização do cliente baseada em SPA estrutura (por exemplo, Reagir ou Angular).

## Introdução {#introduction}

Graças ao contrato simples e leve que é exigido pela AEM e estabelecido entre o SPA e o Editor SPA, pegar um aplicativo Javascript existente e adaptá-lo para uso com um SPA em AEM é uma questão simples.

Este artigo ilustra o exemplo do componente meteorológico no SPA de amostra de Journal We.Retail.

Você deve estar familiarizado com a estrutura [de um aplicativo SPA para AEM](/help/sites-developing/spa-getting-started-react.md) antes de ler este artigo.

>[!CAUTION]
>Este documento usa o [Aplicativo de Journal We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) apenas para fins de demonstração. Não deve ser utilizado para qualquer trabalho de projeto.
>
>Qualquer projeto AEM deve aproveitar o [AEM Project Archetype](https://docs.adobe.com/content/help/pt-BR/experience-manager-core-components/using/developing/archetype/overview.html), que suporta projetos SPA usando React ou Angular e aproveita o SPA SDK.

## O componente de tempo {#the-weather-component}

O componente de tempo é encontrado no canto superior esquerdo do aplicativo de Journal We.Retail. Ele exibe o tempo atual de um local definido, puxando dados do tempo dinamicamente.

### Usando o Widget de tempo {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Ao criar o conteúdo do SPA no Editor de SPA, o componente meteorológico aparece como qualquer outro componente AEM, completo com uma barra de ferramentas e é editável.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

A cidade pode ser atualizada em uma caixa de diálogo como qualquer outro componente AEM.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

A alteração é persistente e o componente é atualizado automaticamente com novos dados meteorológicos.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implementação do componente de tempo {#weather-component-implementation}

O componente meteorológico é na verdade baseado em um componente React disponível ao público, chamado [Reagir Tempo Aberto](https://www.npmjs.com/package/react-open-weather), que foi adaptado para funcionar como um componente no aplicativo SPA amostra de Journal We.Retail.

A seguir estão trechos da documentação do NPM sobre o uso do componente React Open Weather.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Revisando o código do componente meteorológico personalizado ( `Weather.js`) no aplicativo de Journal We.Retail:

* **Linha 16**: O widget React Open Weather é carregado conforme necessário.
* **Linha 46**: A  `MapTo` função relaciona esse componente React a um componente AEM correspondente para que possa ser editado no Editor de SPA.

* **Linhas 22-29**: O  `EditConfig` está definido, verificando se a cidade foi preenchida e definindo o valor se estiver vazio.

* **Linhas 31-44**: O componente de Tempo estende a  `Component` classe e fornece os dados necessários, conforme definido na documentação de uso do NPM para o componente de Tempo Reato Aberto e renderiza o componente.

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

Embora um componente back-end já deva existir, o desenvolvedor front-end pode aproveitar o componente React Open Weather no SPA We.Retail do Journal com pouca codificação.

## Próxima etapa {#next-step}

Para obter mais informações sobre como desenvolver SPA para AEM, consulte o artigo [Desenvolvimento de SPA para AEM](/help/sites-developing/spa-architecture.md).
