---
title: Relatórios Relatórios Personalizados em Andamento
seo-title: Relatórios Relatórios Personalizados em Andamento
description: Você pode criar relatórios personalizados e adicioná-los à interface do usuário do Relatórios do AEM Forms no JEE Process.
seo-description: Você pode criar relatórios personalizados e adicioná-los à interface do usuário do Relatórios do AEM Forms no JEE Process.
uuid: 8974ec2d-ac54-4b44-9758-b1cf44b732fa
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: process-reporting
discoiquuid: c668bd53-f2d8-4f8c-83f2-be0afd65392a
translation-type: tm+mt
source-git-commit: f13d358a6508da5813186ed61f959f7a84e6c19f
workflow-type: tm+mt
source-wordcount: '1042'
ht-degree: 0%

---


# Relatórios de Relatórios Personalizados em Processo {#custom-reports-in-process-reporting}

Você pode usar a interface REST do QueryBuilder ou criar um serviço OSGi usando a API do QueryBuilder para criar um relatório personalizado.

## Etapas genéricas para criar um relatório personalizado {#generic-steps-to-build-a-custom-report}

Antes de adicionar qualquer relatório personalizado, execute o seguinte procedimento de modelo:

1. Os dados usados em relatórios personalizados devem estar disponíveis no Relatórios Process. Para garantir a disponibilidade dos dados, programe um trabalho de cron ou use a opção **[Sincronizar](https://helpx.adobe.com/livecycle/help/process-reporting/install-start-process-reporting.html#Process%20Reporting%20Home%20screen)** na interface do Relatórios do processo.
1. A solicitação de URL (encapsulando o query desejado) deve retornar um objeto de resultado de query apropriado. Para criar um query, você pode usar a interface REST de [QueryBuilder](https://docs.adobe.com/docs/en/cq/current/dam/customizing_and_extendingcq5dam/query_builder.html) para criar um serviço OSGi usando a API do QueryBuilder. Você pode criar query dinâmicos ou estáticos.

1. Crie uma interface de usuário personalizada para exibir os resultados. Você pode criar uma interface de usuário independente ou integrar um resultado com a interface de usuário existente do Relatórios do processo.

## Usando a interface REST do QueryBuilder {#using-the-rest-interface-of-the-querybuilder}

A interface REST do CRX QueryBuilder expõe a funcionalidade do Criador de Query de compartilhamento de ativos por meio de uma API Java e REST. Saiba como usar a [interface REST do CRX QueryBuilder](https://docs.adobe.com/docs/en/cq/current/dam/customizing_and_extendingcq5dam/query_builder.html), antes de executar as seguintes etapas:

1. Navegue até o URL `https://[server]:[port]/lc/bin/querybuilder.json`

1. Crie um query com base na estrutura do nó do armazenamento do Relatórios Process e nas propriedades do nó.

   Você pode especificar parâmetros opcionais para especificar deslocamento, limite, ocorrências e propriedades. Você pode codificar os argumentos para relatórios estáticos e buscar os parâmetros da interface do usuário para relatórios dinâmicos.

   Para buscar todos os nomes de processos, o query é:

   `https://[Server]:[Port]/lc/bin/querybuilder.json?exact=false&p.hits=selective&p.properties=pmProcessTitle&path=%2fcontent%2freporting%2fpm&property=pmNodeType&property.operation=equals&property.value=ProcessType&type=sling%3aFolder`

   >[!NOTE]
   >
   >Em cada query, o parâmetro path aponta para o local do armazenamento crx e os caracteres são escapados de acordo com o padrão de URL.

## Criação de um serviço usando a API do Construtor de Query  {#creating-a-service-using-query-builder-api-nbsp}

Os pré-requisitos para criar um serviço usando a API do construtor de Query são [criar e implantar o pacote OSGI do CQ](https://docs.adobe.com/docs/v5_2/html-resources/cq5_guide_developer/cq5_guide_developer.html) e [usando a API do Construtor de Query](https://docs.adobe.com/docs/en/cq/current/dam/customizing_and_extendingcq5dam/query_builder.html).

1. Crie um serviço OSGi com anotações apropriadas. Para acessar o QueryBuilder, use:

   ```
   @Reference(referenceInterface = QueryBuilder.class) 
    private QueryBuilder queryBuilder;
   ```

1. Criar um grupo de predicados. O código para criar um grupo de predicados é:

   ```
   PredicateGroup predicateGroup = new PredicateGroup(); 
    predicateGroup.setAllRequired(true);
   ```

1. Adicione predicados ao predicateGroup recém-criado. Algumas construções de predicado úteis são [JcrBoolPropertyPredicateEvaluator](https://docs.adobe.com/docs/en/cq/5-3/javadoc/com/day/cq/search/eval/JcrBoolPropertyPredicateEvaluator.html), [JcrPropertyPredicateEvaluator](https://docs.adobe.com/docs/en/cq/5-3/javadoc/com/day/cq/search/eval/JcrPropertyPredicateEvaluator.html), [RangePropertyPredicateEvaluator](https://docs.adobe.com/docs/en/cq/5-3/javadoc/com/day/cq/search/eval/RangePropertyPredicateEvaluator.html), [DateRangePredicateEvaluator](https://docs.adobe.com/docs/en/cq/5-3/javadoc/com/day/cq/search/eval/RelativeDateRangePredicateEvaluator.html) e [TypePredicateEvaluator](https://docs.adobe.com/docs/en/cq/5-3/javadoc/com/day/cq/search/eval/TypePredicateEvaluator.html).

   Para relatórios estáticos, codifique os predicados, enquanto para relatórios dinâmicos, obtenha os predicados da solicitação.

   O código de amostra para obter todas as instâncias de um processo é:

   ```java
   Predicate predicate;
   
     //Add the path Constraint
     predicate = new Predicate(PathPredicateEvaluator.PATH);
     predicate.set(PathPredicateEvaluator.PATH, "/content/reporting/pm"); // should point to the crx path being used to store data
     predicate.set(PathPredicateEvaluator.EXACT, "false");
     predicateGroup.add(predicate);
   
     //type nt:unstructured
     predicate = new Predicate(TypePredicateEvaluator.TYPE);
     predicate.set(TypePredicateEvaluator.TYPE, "nt:unstructured");
     predicateGroup.add(predicate);
   
     //NodeType: Process Instance
     predicate = new Predicate(JcrPropertyPredicateEvaluator.PROPERTY);
     predicate.set(JcrPropertyPredicateEvaluator.PROPERTY, "pmNodeType");
     predicate.set(JcrPropertyPredicateEvaluator.OPERATION, JcrPropertyPredicateEvaluator.OP_EQUALS);
     predicate.set(JcrPropertyPredicateEvaluator.VALUE, "ProcessInstance");
     predicateGroup.add(predicate);
   
     //processName
     predicate = new Predicate(JcrPropertyPredicateEvaluator.PROPERTY);
     predicate.set(JcrPropertyPredicateEvaluator.PROPERTY, "pmProcessName");
     predicate.set(JcrPropertyPredicateEvaluator.OPERATION, JcrPropertyPredicateEvaluator.OP_EQUALS);
     predicate.set(JcrPropertyPredicateEvaluator.VALUE, processName); //processName variable stores the name of the process whose instances need to be searched
     predicateGroup.add(predicate);
   ```

1. Defina o Query usando o predicateGroup.

   `Query query = queryBuilder.createQuery(predicateGroup, session);`

1. Obtenha o resultado do query.

   ```java
   query.setStart(offset); // hardcode or fetch from request
           if(hits == -1)         // hardcode or fetch from request
               hits = 0;
           query.setHitsPerPage(hits);
           SearchResult searchResult = query.getResult();
   ```

1. Iterar no resultado e transformar os resultados no formato desejado. O código para enviar os resultados no formato CSV é:

   ```java
   Iterator<Node> iter = searchResult.getNodes();
                   while(iter.hasNext()) {
                       Node node = iter.next();
                       row = new StringBuilder();
                       for (String property : includeProperties) { // the properties of the node which needs to be returned, or one can return all the properties too.
                           try {
                               row.append(node.getProperties(property).nextProperty().getString() + COMMA_SEPARATOR);
                           } catch (NoSuchElementException e) {
                               //Adding separator for no value
                               row.append(COMMA_SEPARATOR);
                           } catch (RepositoryException e) {
                               e.printStackTrace();
                           }
                       }
                       row.deleteCharAt(row.lastIndexOf(COMMA_SEPARATOR));
                       row.append(NEW_LINE);
                       out.write(row.toString().getBytes());
   ```

1. Use `org.apache.felix maven-bundle-plugin` para criar um pacote OSGi para o servlet.

1. Implante o pacote no servidor CRX.

### Exemplo de serviço {#service-example}

O exemplo de serviço a seguir conta instâncias de um processo que está no estado **RUNNING** e **COMPLETE** no fim de cada mês, trimestre e ano.

```java
package custom.reporting.service;
 
import java.text.DateFormatSymbols;
import java.util.Calendar;
import java.util.HashMap;
import java.util.Iterator;
import java.util.LinkedHashMap;
import java.util.Map;
import java.util.SortedSet;
import java.util.TreeSet;
 
import javax.jcr.Node;
import javax.jcr.Session;
 
import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.Service;
 
import com.day.cq.search.Predicate;
import com.day.cq.search.PredicateGroup;
import com.day.cq.search.Query;
import com.day.cq.search.QueryBuilder;
import com.day.cq.search.eval.JcrPropertyPredicateEvaluator;
import com.day.cq.search.eval.PathPredicateEvaluator;
import com.day.cq.search.eval.TypePredicateEvaluator;
import com.day.cq.search.result.SearchResult;
 
@Component(metatype = true, immediate = true, label = "PeriodicProcessVolume", description = "Service for supporting cutom reports pluggable to Process Reporting.")
@Service(value = PeriodicProcessVolume.class)
public class PeriodicProcessVolume {
 
    private static String[] monthNameList = new DateFormatSymbols().getMonths();
    private static String[] quaterNameList = { "I", "II", "III", "IV" };
 
    private final Map<Integer, Map<Integer, Long[]>> monthly = new HashMap<Integer, Map<Integer, Long[]>>();
    private final Map<Integer, Map<Integer, Long[]>> quaterly = new HashMap<Integer, Map<Integer, Long[]>>();
    private final Map<Integer, Long[]> yearly = new HashMap<Integer, Long[]>();
 
    @Reference(referenceInterface = QueryBuilder.class)
    private QueryBuilder queryBuilder;
 
    private void addConstraints(PredicateGroup predicateGroup, String processName) {
        Predicate predicate;
 
        //Add the path Constraint
        predicate = new Predicate(PathPredicateEvaluator.PATH);
        predicate.set(PathPredicateEvaluator.PATH, "/content/reporting/pm");
        predicate.set(PathPredicateEvaluator.EXACT, "false");
        predicateGroup.add(predicate);
 
        //type nt:unstructured
        predicate = new Predicate(TypePredicateEvaluator.TYPE);
        predicate.set(TypePredicateEvaluator.TYPE, "nt:unstructured");
        predicateGroup.add(predicate);
 
        //NodeType: Process Instance
        predicate = new Predicate(JcrPropertyPredicateEvaluator.PROPERTY);
        predicate.set(JcrPropertyPredicateEvaluator.PROPERTY, "pmNodeType");
        predicate.set(JcrPropertyPredicateEvaluator.OPERATION, JcrPropertyPredicateEvaluator.OP_EQUALS);
        predicate.set(JcrPropertyPredicateEvaluator.VALUE, "ProcessInstance");
        predicateGroup.add(predicate);
 
        //processName
        if (processName != null) {
            predicate = new Predicate(JcrPropertyPredicateEvaluator.PROPERTY);
            predicate.set(JcrPropertyPredicateEvaluator.PROPERTY, "pmProcessName");
            predicate.set(JcrPropertyPredicateEvaluator.OPERATION, JcrPropertyPredicateEvaluator.OP_EQUALS);
            predicate.set(JcrPropertyPredicateEvaluator.VALUE, processName);
            predicateGroup.add(predicate);
        }
    }
 
    private Long[] setFrequency(Long[] frequency, int index) {
        if (frequency == null) {
            frequency = new Long[2];
            frequency[0] = 0L;
            frequency[1] = 0L;
        }
        frequency[index] = frequency[index] + 1L;
        return frequency;
    }
 
    public void populateValues(Session session, String processName) {
        PredicateGroup predicateGroup = new PredicateGroup();
        predicateGroup.setAllRequired(true);
        try {
            addConstraints(predicateGroup, processName);
 
            long batchSize = 10000L;
            long start = 0l;
 
            while (true) {
                Query query = queryBuilder.createQuery(predicateGroup, session);
                query.setStart(start);
                query.setHitsPerPage(batchSize);
                SearchResult searchResult = query.getResult();
                Iterator<Node> itr = searchResult.getNodes();
                long length = 0;
                while (itr.hasNext()) {
                    length++;
                    Node n = itr.next();
                    Calendar calender = n.getProperty("pmCreateTime").getDate();
                    String status = n.getProperty("pmStatus").getString();
                    int index = 0;
                    if ("COMPLETE".equals(status)) {
                        index = 1;
                    } else if ("RUNNING".equals(status)) {
                        index = 0;
                    } else {
                        continue;
                    }
                    int month = calender.get(Calendar.MONTH);
                    int year = calender.get(Calendar.YEAR);
                    int quater;
                    if (month < 3) {
                        quater = 1;
                    } else if (month < 6) {
                        quater = 2;
                    } else if (month < 9) {
                        quater = 3;
                    } else {
                        quater = 4;
                    }
 
                    Long frequency[];
                    Map<Integer, Long[]> yearMonthMap = this.monthly.get(year);
                    if (yearMonthMap == null) {
                        yearMonthMap = new HashMap<Integer, Long[]>();
                    }
                    frequency = yearMonthMap.get(month);
                    frequency = setFrequency(frequency, index);
                    yearMonthMap.put(month, frequency);
                    this.monthly.put(year, yearMonthMap);
 
                    Map<Integer, Long[]> yearQuaterMap = this.quaterly.get(year);
                    if (yearQuaterMap == null) {
                        yearQuaterMap = new HashMap<Integer, Long[]>();
                    }
                    frequency = yearQuaterMap.get(quater);
                    frequency = setFrequency(frequency, index);
                    yearQuaterMap.put(quater, frequency);
                    this.quaterly.put(year, yearQuaterMap);
 
                    frequency = this.yearly.get(year);
                    frequency = setFrequency(frequency, index);
                    this.yearly.put(year, frequency);
                }
 
                if (length < batchSize) {
                    break;
                } else {
                    start = start + batchSize;
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
 
    }
 
    public Map<String, Long[]> getMonthly() {
        Map<String, Long[]> result = new LinkedHashMap<String, Long[]>();
        SortedSet<Integer> years = new TreeSet<Integer>(monthly.keySet());
        for (Integer year : years) {
            Map<Integer, Long[]> yearMonthMap = monthly.get(year);
            SortedSet<Integer> months = new TreeSet<Integer>(yearMonthMap.keySet());
            for (Integer month : months) {
                String str = monthNameList[month] + " " + year;
                result.put(str, yearMonthMap.get(month));
            }
        }
        return result;
    }
 
    public Map<String, Long[]> getQuaterly() {
        Map<String, Long[]> result = new LinkedHashMap<String, Long[]>();
        SortedSet<Integer> years = new TreeSet<Integer>(quaterly.keySet());
        for (Integer year : years) {
            Map<Integer, Long[]> quaterMonthMap = quaterly.get(year);
            SortedSet<Integer> quaters = new TreeSet<Integer>(quaterMonthMap.keySet());
            for (Integer quater : quaters) {
                String str = quaterNameList[quater - 1] + " " + year;
                result.put(str, quaterMonthMap.get(quater));
            }
        }
        return result;
    }
 
    public Map<Integer, Long[]> getYearly() {
        return yearly;
    }

}
```

O arquivo de amostra `pom.xml`a ser criado acima do serviço é:

```java
<project xmlns="https://maven.apache.org/POM/4.0.0" xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="https://maven.apache.org/POM/4.0.0 https://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
 
    <!-- ====================================================================== -->
    <!-- P R O J E C T  D E S C R I P T I O N                                   -->
    <!-- ====================================================================== -->
    <groupId>com.custom</groupId>
    <artifactId>sample-report-core</artifactId>
    <packaging>bundle</packaging>
    <name>PR Sample Report</name>
    <description>Bundle providing support for a custom report pluggable to process reporting.</description>
    <version>1</version>

    <!-- ====================================================================== -->
    <!-- B U I L D   D E F I N I T I O N                                        -->
    <!-- ====================================================================== -->
    <build>
        <plugins>
          <plugin>
              <groupId>org.apache.felix</groupId>
              <artifactId>maven-bundle-plugin</artifactId>
              <version>2.3.7</version>
              <extensions>true</extensions>
              <configuration>
                    <instructions>
                        <Bundle-Category>sample-report</Bundle-Category>
                        <Export-Package>
                            custom.reporting.service.*;
                        </Export-Package>
                     </instructions>
              </configuration>
          </plugin>
          <plugin>
                <groupId>org.apache.felix</groupId>
                <artifactId>maven-scr-plugin</artifactId>
                <version>1.11.0</version>
                <executions>
                    <execution>
                        <id>generate-scr-scrdescriptor</id>
                        <goals>
                            <goal>scr</goal>
                        </goals>
                        <configuration>
                            <!-- Private service properties for all services. -->
                            <properties>
                                <service.vendor>Sample Report</service.vendor>
                            </properties>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
 
    <!-- ====================================================================== -->
    <!-- D E P E N D E N C I E S                                                -->
    <!-- ====================================================================== -->
    <dependencies>
        <dependency>
          <groupId>com.day.cq</groupId>
          <artifactId>cq-search</artifactId>
          <version>5.6.4</version>
        </dependency>
 
        <dependency>
          <groupId>javax.jcr</groupId>
          <artifactId>jcr</artifactId>
          <version>2.0</version>
        </dependency>
 
        <dependency>
          <groupId>org.apache.felix</groupId>
          <artifactId>org.apache.felix.scr.annotations</artifactId>
          <version>1.9.0</version>
        </dependency>
    </dependencies>
</project>
```

## Criação de uma interface de usuário separada  {#creating-a-separate-ui-nbsp}

Os pré-requisitos para criar uma interface de usuário separada para exibir resultados são [Informações básicas sobre Sling](https://docs.adobe.com/docs/en/cq/5-6-1/developing/the_basics.html), [Criar um nó CRX](https://docs.adobe.com/docs/en/crx/current/developing/development_tools/developing_with_crxde_lite.html#Creating%20a%20Node) e fornecer [privilégios de acesso](https://docs.adobe.com/docs/en/crx/current/developing/development_tools/developing_with_crxde_lite.html#Access%20Control) apropriados.

1. Crie um Nó CRX no nó `/apps` e conceda as permissões de acesso apropriadas. (PERM_PROCESS_RELATÓRIOS_USER)
1. Defina o renderizador no nó `/content`.
1. Adicione arquivos JSP ou HTML ao nó criado na Etapa 1. Você também pode adicionar arquivos CSS.

   ![Um nó de amostra com arquivos JSP e CSS](assets/nodewithjspandcss.png)

   Um nó de amostra com arquivos JSP e CSS

1. Adicione o código javascript ao start de uma chamada Ajax para a API REST do querybuilder ou para o seu serviço. Além disso, adicione os argumentos apropriados.

1. Adicione um manipulador de sucesso apropriado à chamada Ajax para analisar e exibir o resultado. Você pode analisar o resultado em vários formatos (json/csv/usuário definido) e exibi-lo em uma tabela ou em outros formulários.

1. (Opcional) Adicione um manipulador de erros apropriado à chamada Ajax.

Um exemplo de código JSP que usa OSGi Service e a API do QueryBuilder é:

```
<%@taglib prefix="sling" uri="https://sling.apache.org/taglibs/sling/1.0"%>
<%request.setAttribute("silentAuthor", new Boolean(true));%>
<%@include file="/libs/foundation/global.jsp"%>
<%@ page import="java.util.Map,
java.util.Set,
com.adobe.idp.dsc.registry.service.ServiceRegistry,
javax.jcr.Session,
org.apache.sling.api.resource.ResourceResolver,
custom.reporting.service.PeriodicProcessVolume"%>
<%
response.setContentType("text/html");
response.setCharacterEncoding("utf-8");
%><!DOCTYPE HTML>
<html>
    <head>
        <meta charset="UTF-8">
 
        <link rel="stylesheet" href="/lc/apps/sample-report-process-reporting/custom-reports/periodicProcessVolume/style.css">
        <title>REPORT Monthly / Qaterly / Yearly</title>
        <script type="text/javascript">
 
            <%
                slingResponse.setCharacterEncoding("utf-8");
                ResourceResolver resolver = slingRequest.getResourceResolver();
                String processName = slingRequest.getParameter("processName");
                Session session = resolver.adaptTo(Session.class);
                custom.reporting.service.PeriodicProcessVolume periodicProcessVolume = sling.getService(custom.reporting.service.PeriodicProcessVolume.class);
                periodicProcessVolume.populateValues(session, processName);
                if (processName == null) {
                    processName = "All";
                }
            %>
            var lineSeprator = "<td>----------------</td>";
            var tableEnder = "<tr>" + lineSeprator + lineSeprator + lineSeprator + "</tr>";
 
            var tableColHeader = "<td>Running</td>";
            tableColHeader += "<td>Complete</td></tr>";
            tableColHeader += tableEnder;
 
            var monthly = "<table><tr><td>Month</td>";
            monthly += tableColHeader;
 
            <%
                Map<String, Long[]> monthlyMap = periodicProcessVolume.getMonthly();
                Set<String> monthKeys = monthlyMap.keySet();
                for (String key: monthKeys) {
                    Long[] frequencies = monthlyMap.get(key);
            %>
 
            monthly += "<tr><td> <%= key %> </td>";
            monthly += "<td> <%= frequencies[0] %> </td>";
            monthly += "<td> <%= frequencies[1] %> </td></tr>";
            <%
                }
            %>
 
            monthly += tableEnder;
 
            var quaterly = "<table><tr><td>Quater</td>";
            quaterly += tableColHeader;
 
            <%
                Map<String, Long[]> quaterMap = periodicProcessVolume.getQuaterly();
                Set<String> quaterKeys = quaterMap.keySet();
                for (String key: quaterKeys) {
                    Long[] frequencies = quaterMap.get(key);
            %>
 
            quaterly += "<tr><td> <%= key %> </td>";
            quaterly += "<td> <%= frequencies[0] %> </td>";
            quaterly += "<td> <%= frequencies[1] %> </td></tr>";
            <%
                }
            %>
 
            quaterly += tableEnder;
 
            var yearly = "<table><tr><td>Year</td>";
            yearly += tableColHeader;
 
            <%
                Map<Integer, Long[]> yearMap = periodicProcessVolume.getYearly();
                Set<Integer> yearKeys = yearMap.keySet();
                for (Integer key: yearKeys) {
                    Long[] frequencies = yearMap.get(key);
            %>
 
            yearly += "<tr><td> <%= key %> </td>";
            yearly += "<td> <%= frequencies[0] %> </td>";
            yearly += "<td> <%= frequencies[1] %> </td></tr>";
            <%
                }
            %>
 
            yearly += tableEnder;
 
            function reloadFrame(value) {
                if (value === '-1') {
                    window.location = "/lc/content/process-reporting-runtime/custom-reports/periodicProcessVolume.html";
                } else {
                    window.location = "/lc/content/process-reporting-runtime/custom-reports/periodicProcessVolume.html?processName=" + value;
                }
            }
 
            function populateTable(selection) {
                if (selection === 0) {
                    document.getElementById('tableHeading').innerHTML = 'Monthly';
                    document.getElementById('volumeTable').innerHTML = monthly;
                } else if (selection === 1) {
                    document.getElementById('tableHeading').innerHTML = 'Quaterly';
                    document.getElementById('volumeTable').innerHTML = quaterly;
                } else {
                    document.getElementById('tableHeading').innerHTML = 'Yearly';
                    document.getElementById('volumeTable').innerHTML = yearly;
                }
            }
 
            function fetchProcesses() {
                var xmlhttp = new XMLHttpRequest(),
                    request = '';
                xmlhttp.onreadystatechange = function() {
                   if (xmlhttp.readyState === 4 && xmlhttp.status === 200) {
                       var responseText,
                           response,
                           items,
                           hits = [],
                           responseSize = 0,
                           processName,
                           selectedIndex = 0,
                           comboBox;
                       responseText = xmlhttp.responseText;
                       if (responseText !== undefined && responseText !== null) {
                           response = JSON.parse(responseText);
                           responseSize = response.results;
                           hits = response.hits;
                       }
 
                       items = "<option value='-1'>All</option>";
 
                       for(var i = 0; i < responseSize; i++) {
                           processName = hits[i].pmProcessTitle;
                           if (processName === '<%= processName %>') {
                               selectedIndex = i + 1;
                           }
                           items += "<option value='" + processName + "'>" + processName + "</option>"
                       }
 
                       comboBox = document.getElementById('processSelection');
                       comboBox.innerHTML = items;
                       comboBox.selectedIndex = selectedIndex;
                   }
               };
               request = "/lc/bin/querybuilder.json?";
               request += "exact=false&";
               request += "p.hits=selective&";
               request += "p.properties=pmProcessTitle&";
               request += "path=%2fcontent%2freporting%2fpm&";
               request += "property=pmNodeType&";
               request += "property.operation=equals&";
               request += "property.value=ProcessType&";
               request += "type=sling%3aFolder";

               xmlhttp.open("POST", request, true);
               xmlhttp.setRequestHeader("Content-type","application/json");
               xmlhttp.send();
            }
 
        </script>
    </head>
    <body onLoad="fetchProcesses();populateTable(0);">
        Process:
        <select id="processSelection" onchange="reloadFrame(this.value);"></select>
        &nbsp &nbsp Period Interval:
        <select name="periodSelection" onchange="populateTable(this.selectedIndex);">
            <option value="1">Monthly</option>
            <option value="2">Quaterly</option>
            <option value="3">Yearly</option>
        </select>
        <br> <br> <br> <br>
        <div class="inline"> Process: &nbsp <b><%= processName %></b> &nbsp &nbsp Period: &nbsp </div> <b> <div id="tableHeading" class="inline"> </div> </b>
        <br><br>
        <div id="volumeTable"> </div>
 
    </body>
</html>
```

## Integração da interface do usuário do relatório na interface do Relatórios do processo existente  {#integrating-report-ui-in-existing-process-reporting-ui-nbsp}

Os pré-requisitos para criar uma interface de usuário separada para exibir resultados são [Informações básicas sobre Sling](https://wem.help.adobe.com/enterprise/en_US/10-0/wem/developing/the_basics.html), [Criar um nó CRX](https://docs.adobe.com/docs/en/crx/current/developing/development_tools/developing_with_crxde_lite.html#Creating%20a%20Node) e fornecer [privilégios de acesso](https://docs.adobe.com/docs/en/crx/current/developing/development_tools/developing_with_crxde_lite.html#Access%20Control) apropriados.

1. Crie uma interface de usuário separada conforme descrito na seção [Criação de uma interface de usuário separada](#creating-a-separate-ui-nbsp).
1. Crie um nó filho `nt:unstructured` no nó `/content/process-reporting-runtime/custom-reports` para cada relatório conectável.

   * **id** - Especifica o número de identificação exclusivo do relatório.
   * **name** - Especifica o nome do relatório. O nome é exibido na interface do usuário.
   * **link** - Especifica o link relativo para o renderizador da interface de usuário separada. O link é criado na Etapa 1.
   * **descrição** - Especifica a descrição de uma linha do relatório. Você pode deixar o campo de descrição vazio.
   * **ícone** - Especifica a imagem para representar pictorialmente o relatório. Você pode deixar o campo de ícone vazio.

   ![Propriedades do nó  ](assets/nodeproperties.png)

   Propriedades do nó

1. A interface do usuário do relatório é integrada à interface do Relatórios do processo. Depois de integrar a interface do usuário, a interface do usuário atualizada é semelhante às seguintes imagens:

   ![Interface do usuário de relatórios personalizados recém adicionados](assets/sample-ui-screen-shot-1.png)

   Interface do usuário de relatórios personalizados recém adicionados

   ![Tela de resultados dos relatórios personalizados](assets/jsp-display.png)

   Tela de resultados dos relatórios personalizados

## Pacote de amostra {#sample-package}

Importe o pacote `sample-report-pkg-1.zip` para integrar relatórios personalizados e IU discutidos no artigo à interface do usuário do Process Management.

[Obter arquivo](assets/sample-report-pkg-1.zip)

