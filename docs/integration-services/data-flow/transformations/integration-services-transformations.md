---
title: "Преобразования служб Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "преобразования [службы Integration Services], указанные"
  - "преобразования [службы Integration Services], типы"
  - "преобразования [службы Integration Services]"
  - "поток данных [Integration Services], преобразования"
  - "преобразования бизнес-аналитики [службы Integration Services]"
  - "преобразования соединения"
  - "преобразования разбиения [службы Integration Services]"
  - "пользовательские преобразования [службы Integration Services]"
  - "преобразования строк [службы Integration Services]"
  - "преобразования наборов строк [службы Integration Services]"
ms.assetid: c70c4f6e-82dd-4948-b923-fd5193f67f7e
caps.latest.revision: 56
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 56
---
# Преобразования служб Integration Services
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] являются компонентами потока данных пакета, которые выполняют статистическую обработку данных, а также соединяют, распространяют и изменяют данные. Преобразования могут также выполнять операции поиска и формировать образцы наборов данных. В этом разделе описываются преобразования, которые содержат службы [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] , и поясняется работа этих преобразований.  
  
## Преобразования бизнес-аналитики  
 Следующие преобразования реализуют такие операции бизнес-аналитики, как очистка данных, выполнение интеллектуального анализа текста и выполнение запросов прогнозов интеллектуального анализа данных.  
  
|Преобразование|Description|  
|--------------------|-----------------|  
|[Преобразование «Медленно изменяющееся измерение»](../../../integration-services/data-flow/transformations/slowly-changing-dimension-transformation.md)|Преобразование, которое настраивает обновление медленно изменяющегося измерения.|  
|[Преобразование «Нечеткое группирование»](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)|Преобразование, стандартизирующее значения данных столбца.|  
|[Преобразование «Нечеткий уточняющий запрос»](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)|Преобразование, выполняющее поиск значений в ссылочной таблице при помощи нечеткого соответствия.|  
|[Преобразование «Извлечение терминов»](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)|Преобразование, извлекающее термины из текста.|  
|[Преобразование «Уточняющий запрос термина»](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)|Преобразование, которое ищет термины в ссылочной таблице и подсчитывает термины, извлеченные из текста.|  
|[Преобразование «Запрос интеллектуального анализа данных»](../../../integration-services/data-flow/transformations/data-mining-query-transformation.md)|Преобразование, которое выполняет запросы прогноза интеллектуального анализа данных.|  
|[Преобразование «Очистка DQS»](../../../integration-services/data-flow/transformations/dqs-cleansing-transformation.md)|Преобразование, которое исправляет данные из подключенного источника данных, применяя правила, созданные для источника данных.|  
  
## Преобразования строк  
 Следующие преобразования обновляют значения столбцов и создают новые столбцы. Преобразование применяется к каждой входной строке преобразования.  
  
|Преобразование|Description|  
|--------------------|-----------------|  
|[Преобразование «Таблица символов»](../../../integration-services/data-flow/transformations/character-map-transformation.md)|Преобразование, которое применяет строковые функции к символьным данным.|  
|[Преобразование «Копирование столбца»](../../../integration-services/data-flow/transformations/copy-column-transformation.md)|Преобразование, которое добавляет копии входных столбцов к выходу преобразования.|  
|[Преобразование «Конвертация данных»](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)|Преобразование, преобразующее тип данных столбца в другой тип данных.|  
|[Преобразование «Производный столбец»](../../../integration-services/data-flow/transformations/derived-column-transformation.md)|Преобразование, которое заполняет столбцы результатами выражений.|  
|[Преобразование «Экспорт столбца»](../../../integration-services/data-flow/transformations/export-column-transformation.md)|Преобразование, вставляющее данные из потока данных в файл.|  
|[Преобразование «Импорт столбца»](../../../integration-services/data-flow/transformations/import-column-transformation.md)|Преобразование, которое считывает данные из файла и добавляет в поток данных.|  
|[Компонент скрипта](../../../integration-services/data-flow/transformations/script-component.md)|Преобразование, которое использует скрипт для извлечения, преобразования или загрузки данных.|  
|[Преобразование «Команда OLE DB»](../../../integration-services/data-flow/transformations/ole-db-command-transformation.md)|Преобразование, выполняющее команды SQL для каждой строки потока данных.|  
  
## Преобразования набора строк  
 Следующие преобразования создают новые наборы строк. Набор строк может включать в себя значения статистических функций и сортировки, образцы наборов строк или несведенные наборы строк.  
  
|Преобразование|Description|  
|--------------------|-----------------|  
|[Преобразование «Статистическая обработка»](../../../integration-services/data-flow/transformations/aggregate-transformation.md)|Преобразование, которое выполняет статистические функции, такие как AVERAGE, SUM и COUNT.|  
|[Преобразование «Сортировка»](../../../integration-services/data-flow/transformations/sort-transformation.md)|Преобразование, которое сортирует данные.|  
|[Преобразование «Процентная выборка»](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)|Преобразование, которое создает образец набора данных, задавая размер выборки в процентах.|  
|[Преобразование «Выборка строк»](../../../integration-services/data-flow/transformations/row-sampling-transformation.md)|Преобразование, которое создает образец набора данных с указанием количества строк в выборке.|  
|[Преобразование «Сведение»](../../../integration-services/data-flow/transformations/pivot-transformation.md)|Преобразование, которое создает менее нормализованную версию нормализованной таблицы.|  
|[Преобразование отмены свертывания](../../../integration-services/data-flow/transformations/unpivot-transformation.md)|Преобразование, которое создает более нормализованную версию ненормализованной таблицы.|  
  
## Преобразования «Разбиение» и «Соединение»  
 Следующие преобразования распределяют строки по различным выходам, создают копии входных данных преобразования, соединяют несколько входов в один выход и выполняют операции поиска.  
  
|Преобразование|Description|  
|--------------------|-----------------|  
|[Преобразование «Условное разбиение»](../../../integration-services/data-flow/transformations/conditional-split-transformation.md)|Преобразование, направляющее строки данных по различным выходам.|  
|[Преобразование «Многоадресная доставка»](../../../integration-services/data-flow/transformations/multicast-transformation.md)|Преобразование, распределяющее наборы данных по различным выходам.|  
|[Преобразование «Объединить все»](../../../integration-services/data-flow/transformations/union-all-transformation.md)|Преобразование, производящее слияние нескольких наборов данных.|  
|[Преобразование «Слияние»](../../../integration-services/data-flow/transformations/merge-transformation.md)|Преобразование, производящее слияние двух отсортированных наборов данных.|  
|[Преобразование «Соединение слиянием»](../../../integration-services/data-flow/transformations/merge-join-transformation.md)|Преобразование, соединяющее два набора данных при помощи соединения FULL, LEFT или INNER.|  
|[Преобразование «Уточняющий запрос»](../../../integration-services/data-flow/transformations/lookup-transformation.md)|Преобразование, выполняющее поиск значений в ссылочной таблице по полному совпадению.|  
|[Преобразование кэша](../../../integration-services/data-flow/transformations/cache-transform.md)|Преобразование, которое записывает данные из подключенного источника данных в потоке данных в диспетчер соединений с кэшем, сохраняющий данные в файл кэша. Преобразование «Уточняющий запрос» осуществляет поиск данных в файле кэша.|  
|[Преобразование распространителя сбалансированных данных](../../../integration-services/data-flow/transformations/balanced-data-distributor-transformation.md)|Преобразование равномерно распределяет буферы входящих строк между выходами в отдельных потоках для повышения производительности пакетов служб SSIS, выполняемых на многоядерных и мультипроцессорных серверах.|  
  
## Преобразования аудита  
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] включают следующие преобразования для добавления данных аудита и подсчета количества строк.  
  
|Преобразование|Description|  
|--------------------|-----------------|  
|[Преобразование «Аудит»](../../../integration-services/data-flow/transformations/audit-transformation.md)|Преобразование, которое формирует информацию о среде, доступной потоку данных в пакете.|  
|[Преобразование «Подсчет строк»](../../../integration-services/data-flow/transformations/row-count-transformation.md)|Преобразование, подсчитывающее строки в процессе их прохождения через преобразование и сохраняющее результат подсчета в переменной.|  
  
## Пользовательские преобразования  
 Также можно создавать пользовательские преобразования. Дополнительные сведения см. в статьях [Разработка пользовательского компонента преобразования с синхронными выходами](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md) и [Разработка пользовательского компонента преобразования с асинхронными выходами](../../../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md).  
  
  