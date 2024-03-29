---
title: Modelos de carta de referência
seo-title: Reference letter templates
description: O AEM Forms fornece modelos de layout de cartas para o Gerenciamento de correspondência que você pode usar para criar cartas rapidamente.
seo-description: AEM Forms provides Correspondence Management letter layout templates that you can use to create letters quickly.
uuid: 3b2312d9-daa0-435b-976f-4969b54c5056
products: SG_EXPERIENCEMANAGER/6.3/FORMS
content-type: reference
topic-tags: correspondence-management
discoiquuid: afeb9f4d-3feb-4a0e-8884-e3ec1309b33b
exl-id: 319db420-3318-4ef7-be2b-1ff2b1c08563
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 2%

---

# Modelos de carta de referência {#reference-letter-templates}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

No Gerenciamento de correspondência, um modelo de carta contém campos de formulário típicos, recursos de layout como um cabeçalho e rodapé e &quot;áreas de destino&quot; vazias para o posicionamento do conteúdo.

O Gerenciamento de correspondência fornece modelos de carta no pacote do AEM Forms [Pacote do complemento AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html). Para instalar um pacote, consulte [Como trabalhar com pacotes](/help/sites-administering/package-manager.md). Você pode personalizar os modelos no Designer de acordo com suas necessidades comerciais e de marcas. O pacote inclui os seguintes modelos:

* Clássico
* Simples clássico
* Balanceado à Esquerda
* Equilibrado à Direita
* Visual Esquerda
* Parte superior visual
* Visual Top - Classic

Depois de instalar o pacote, os modelos de layout (XDPs) são listados na pasta de modelos no seguinte local:

`https://[server]:[port]/[context-root]/aem/forms.html/content/dam/formsanddocuments/templates-folder`

A seguir estão os campos comuns em todos os templates deste pacote:

* Data
* Saudação
* Fechamento de texto
* Texto de assinatura

![Todos os modelos de letras CM listados](assets/templatescorrespondence.png)

Depois de instalar o pacote AEM-FORMS-6.3-REFERENCE-LAYOUT-TEMPLATES, os modelos são listados na pasta de modelos

## Clássico {#classic}

Com um logotipo no topo, o modelo Clássico é adequado para uma carta profissional simples.

![clássica](assets/classic.png)

Visualização de PDF de uma carta criada com o modelo Clássico

## Simples clássico {#classic-simple}

Inclui campos para capturar o número de telefone e o endereço de email. Um modelo Simples clássico é semelhante ao modelo Clássico, exceto que ele não tem campos nos quais você pode inserir o endereço do recipient.

![Fragmento de informações de contato](assets/classicsimple.png)

Visualização de PDF de uma carta criada com o modelo Simples clássico

## Balanceado à Esquerda {#balanced-left}

O modelo Esquerda Equilibrada inclui o logotipo à esquerda da carta.

![balancecedleft](assets/balancedleft.png)

Visualização de PDF de uma carta criada com o modelo Esquerda Equilibrada

## Equilibrado à Direita {#balanced-right}

O modelo Equilibrado à Direita tem o logotipo da empresa à esquerda e fornece espaço para inserir o endereço dos recipients na própria letra. O modelo Equilibrado à direita também inclui um rodapé que reflui quando a carta tem várias páginas.

![direito equilibrado](assets/balancedright.png)

Visualização de PDF de uma carta criada usando o modelo Direito Equilibrado

## Visual Esquerda {#visual-left}

O modelo da Esquerda visual tem um cabeçalho lateral à esquerda da página com o logotipo da empresa posicionado sobre a cabeça lateral. O modelo da Esquerda visual tem um campo de assunto, mas nenhum rodapé.

![visual left](assets/visualleft.png)

Visualização de PDF de uma carta criada usando o modelo Esquerda Visual

## Parte superior visual {#visual-top}

O modelo do Visual Top tem margem visual no topo. O modelo do Visual Top tem um campo para inserir o endereço do destinatário na própria página. O modelo Superior visual tem o campo de assunto e um rodapé que reflui para letras que se estendem para várias páginas.

![visualização](assets/visualtop.png)

Visualização de PDF de uma carta criada usando o modelo Visual Top

## Visual Top - Classic {#visual-top-classic}

O modelo Visual Top - Classic tem um cabeçalho na parte superior da página com o logotipo da empresa. O modelo Início visual - Clássico tem um campo para inserir um assunto, mas nenhum rodapé.

![visual altopclassic](assets/visualtopclassic.png)

Visualização de PDF de uma carta criada usando o modelo Visual Top - Classic
