---
title: Criar um formulário adaptável usando um conjunto de formulários adaptáveis
seo-title: Create an adaptive form using a set of adaptive forms
description: Com o AEM Forms, reúna formulários adaptáveis para criar um único formulário adaptável grande e entender seus recursos.
seo-description: With AEM Forms, bring adaptive forms together to author a single large adaptive form, and understand its features.
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
feature: Adaptive Forms
exl-id: 969b0c11-adc7-476e-8c82-d444fccba984
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 1%

---

# Criar um formulário adaptável usando um conjunto de formulários adaptáveis {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Visão geral {#overview}

Em um fluxo de trabalho, como um aplicativo para abrir uma conta bancária, seus usuários preenchem vários formulários. Em vez de solicitar que eles preencham um conjunto de formulários, é possível empilhar os formulários e criar um formulário grande (formulário pai). Ao adicionar um formulário adaptável ao formulário maior, ele é adicionado como um painel (formulário filho). Você adiciona um conjunto de formulários filho para criar um formulário pai. Você pode mostrar ou ocultar painéis com base na entrada do usuário. Botões do formulário pai, como enviar e redefinir, substituem os botões do formulário filho. Para adicionar um formulário adaptável no formulário pai, você pode arrastar e soltar o formulário adaptável do navegador de ativos (como fragmentos de formulário adaptáveis).

Os recursos disponíveis são:

* Criação independente
* Mostrar/ocultar formulários apropriados
* Carregamento lento

Recursos como criação independente e carregamento lento proporcionam aprimoramentos de desempenho em relação ao uso de componentes individuais para criar o formulário pai.

>[!NOTE]
>
>Não é possível usar formulários/fragmentos adaptáveis baseados em XFA como formulários filhos ou pais.

## Por trás das cenas {#behind-the-scenes}

É possível adicionar fragmentos e formulários adaptáveis baseados em XSD no formulário pai. A estrutura do formulário pai é igual a [qualquer formulário adaptável](/help/forms/using/prepopulate-adaptive-form-fields.md). Ao adicionar um formulário adaptável como um formulário filho, ele é adicionado como um painel no formulário pai. Os dados de um formulário filho vinculado são armazenados no campo `data`raiz do `afBoundData` seção do esquema XML do formulário pai.

Por exemplo, seus clientes preenchem um formulário de aplicativo. Os dois primeiros campos do formulário são nome e identidade. Seu XML é:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
        </data>
    </afBoundData>
</afData>
```

Você adiciona outro formulário no aplicativo que permite que seus clientes preencham o endereço do escritório. A raiz do esquema do formulário filho é `officeAddress`. Aplicar `bindref` `/application/officeAddress` ou `/officeAddress`. If `bindref`não for fornecido, o formulário filho será adicionado como `officeAddress` subárvore. Consulte o XML do formulário abaixo:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
        </data>
    </afBoundData>
</afData>
```

Se você inserir outro formulário que permita aos clientes fornecer endereço residencial, aplique `bindref` `/application/houseAddress or /houseAddress.`O XML tem a seguinte aparência:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
            <houseAddress>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </houseAddress>
        </data>
    </afBoundData>
</afData>
```

Se desejar manter o mesmo nome de subraiz que a raiz do esquema ( `Address`neste exemplo), use bindrefs indexados.

Por exemplo, aplique bindrefs `/application/address[1]` ou `/address[1]` e `/application/address[2]` ou `/address[2]`. O XML do formulário é:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <address>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
            <address>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
        </data>
    </afBoundData>
</afData>
```

É possível alterar a subárvore padrão do formulário/fragmento adaptável usando o `bindRef` propriedade. O `bindRef` permite especificar o caminho que aponta para um local na estrutura de árvore do esquema XML.

Se o formulário filho não estiver vinculado, seus dados serão armazenados no campo `data`raiz do `afUnboundData` seção do esquema XML do formulário pai.

É possível adicionar um formulário adaptável como um formulário secundário várias vezes. Certifique-se de que `bindRef` é modificado corretamente para que cada instância usada do formulário adaptável aponte para uma subraiz diferente na raiz dos dados.

>[!NOTE]
>
>Se diferentes formulários/fragmentos forem mapeados para a mesma subraiz, os dados serão substituídos.

## Adicionar um formulário adaptável como um formulário filho usando o navegador de ativos {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Execute as etapas a seguir para adicionar um formulário adaptável como um formulário filho usando o navegador de ativos.

1. Abra o formulário pai no modo de edição.
1. Na barra lateral, clique em **Ativos** ![navegador de ativos](assets/assets-browser.png). Em Ativos, selecione **Formulário adaptável** no menu suspenso .
   [ ![Seleção de formulário adaptável em Ativos](assets/asset.png)](assets/asset-1.png)

1. Arraste e solte o formulário adaptável que deseja adicionar como um formulário filho.
   [ ![Arraste e solte o formulário adaptável em seu site](assets/drag-drop.png)](assets/drag-drop-1.png)O formulário adaptável solto é adicionado como um formulário filho.
