---
title: Ferramenta de migração CRX2OAK
seo-title: CRX2OAK Migration Tool
description: Notas de versão específicas da ferramenta de migração CRX2OAK do Adobe Experience Manager 6.4.
seo-description: Release notes specific to the Adobe Experience Manager 6.4 CRX2OAK Migration tool.
uuid: 1b582faf-2dc6-41a2-9419-7e82347f9d6c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: cfdaceac-a5b3-4070-ad4c-f1457b1e2e4b
exl-id: 441c8ba0-f8b2-4c2c-b7be-cfdad9e1e498
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 2%

---

# Ferramenta de migração CRX2OAK {#crx-oak-migration-tool}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

## Lista de alterações e correções {#list-of-changes-and-fixes}

### 1.8.6 (junho de 2018) {#june}

* OAK-7339 Corrija todos os lados com UnsupportedOperationException em MissingBlobStore ao introduzir LoopbackBlobStore
* Use Oak 1.8.4

### 1.8.4 (abril de 2018) {#april}

* Usar o Oak versão 1.8.2
* O erro de migração do GRANITE-18104 Repo de 6.3 para 6.4 deve ser mais significativo
* GRANITE-16571 Substituir uso do SHA-1

   * A soma de verificação da ferramenta agora é SHA-512 ao usar a opção —version

* GRANITE-17601 Incorporar Oak-upgrade no CRX2Oak com oak-blob-cloud
* GRANITE-18553 crx2oak deixa as propriedades da versão no nó mesmo quando as versões não são migradas

### Versão 1.6.8 (março de 2017) {#version-march}

* Atualização da versão do Oak para 1.6.1.
* CQ-61847 Mesclar crx2oak-quickstart-extension com crx2oak (perfis de migração adicionados)
* CQ-97488 Promover e soltar AEM modos de execução (regravando sling.options.file)
* GRANITE-12798/OAK-4260 Capacidade de colar a pontuação do segmento Oak ao Oak Segment Tar

### Versão 1.4.2 (março de 2016) {#version-march-1}

* Atualizar a versão do Oak para 1.4.1
* OAK-3846 / GRANITE-10748 Renomear nós SNS se eles violarem restrições do tipo de nó
* OAK-3910 / GRANITE-10730 Migrando nó que herda de `mix:versionable` sem histórico de versão
* OAK-4128 / GRANITE-11757 `RepositorySidegrade` não copia propriedades do nó raiz

### Versão 1.3.4 (janeiro de 2016) {#version-january}

* Atualizar a versão do Oak para 1.3.16
* OAK-3844 / GRANITE-10730 Melhor suporte para nós com versão sem históricos de versão
* OAK-3846 Renomear nós SNS se eles violarem restrições do tipo de nó

### Versão 1.3.2 (dezembro de 2015) {#version-december}

* Atualiza a versão do Oak para 1.3.12
* O diretório de armazenamento de dados não deve ser movido após a migração (GRANITE-10447)
* Mesclar crx2oak-quickstart-extension com crx2oak (CQ-61847)
* crx2oak falha em valores duplicados no repositório (CQ-61906)
* Início AEM longo após a migração do CQ 5.x (GRANITE-10309)
* Suporte para vários servidores LDAP no crx2oak (GRANITE-9917)
* Impor verificação do comprimento máximo do nome do nó (OAK-3111)
* Suporte ao S3DataSource como a fonte de migração (OAK-3685)
