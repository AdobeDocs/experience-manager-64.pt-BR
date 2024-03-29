---
title: "Banco de dados do Microsoft SQL Server: Ajustar a configuração"
seo-title: "Microsoft SQL Server database: Fine-tuning the configuration"
description: Saiba como ajustar a configuração do banco de dados do Microsoft SQL Server.
seo-description: Learn how you can fine tune the configuration of your Microsoft SQL Server database.
uuid: 2d618aab-3c67-4edb-a28f-a20904689e6f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS, SG_AEMFORMS
discoiquuid: 70559a94-42ea-411a-a32f-5f38bc17ff96
exl-id: 5392027c-eb5a-49c4-bf9b-fe7d399ae0a1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 2%

---

# Banco de dados do Microsoft SQL Server: Ajustar a configuração {#microsoft-sql-server-database-fine-tuning-the-configuration}

>[!CAUTION]
>
>AEM 6.4 chegou ao fim do suporte estendido e esta documentação não é mais atualizada. Para obter mais detalhes, consulte nossa [períodos de assistência técnica](https://helpx.adobe.com/br/support/programs/eol-matrix.html). Encontre as versões compatíveis [here](https://experienceleague.adobe.com/docs/).

Você deve alterar as configurações padrão ao usar o Microsoft SQL Server. Clique com o botão direito do mouse no servidor local do Oracle Enterprise Manager para acessar a caixa de diálogo de propriedades.

## Configurações de memória {#memory-settings}

Altere a alocação mínima de memória para o maior número possível. Se o banco de dados estiver sendo executado em um computador separado, use toda a memória. As configurações padrão não alocam memória de forma agressiva, o que dificulta o desempenho em quase qualquer banco de dados. Você deve ser mais agressivo em alocar memória em máquinas de produção.

## Configurações do processador {#processor-settings}

Modifique as configurações do processador e, o mais importante, marque a caixa de seleção Aumentar prioridade do SQL Server no Windows para que o servidor use a maior quantidade possível de ciclos. A configuração Usar fibras NT é menos importante, mas você também pode selecioná-la.

## Configurações do banco de dados {#database-settings}

Altere as configurações do banco de dados. A configuração mais importante é o Intervalo de recuperação, que especifica a quantidade máxima de tempo para aguardar a recuperação após uma falha. A configuração padrão é de um minuto. Usar um valor maior, de 5 a 15 minutos, melhora o desempenho, pois dá ao servidor mais tempo para gravar alterações do log do banco de dados de volta nos arquivos do banco de dados.

>[!NOTE]
>
>Essa configuração não compromete o comportamento transacional, pois altera apenas o comprimento da reprodução do arquivo de log que deve ser feita na inicialização.

Defina o tamanho Espaço Alocado para o log e o arquivo de dados para que seja muito maior que o banco de dados inicial. Considere quanto o banco de dados pode crescer em um ano. Idealmente, o log e os arquivos de dados são alocados em uma extensão contígua para que os dados não acabem fragmentados em todo o disco.
