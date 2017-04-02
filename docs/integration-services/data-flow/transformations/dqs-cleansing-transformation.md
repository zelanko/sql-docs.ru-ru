---
title: "Преобразование &#171;Очистка DQS&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "сбор данных"
  - "корректировка данных"
ms.assetid: d2ec1b1a-c745-4741-b57c-6fdb524a154c
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# Преобразование &#171;Очистка DQS&#187;
  Преобразование «Очистка DQS» используется службы Data Quality Services (DQS) для исправления данных из подключенного источника данных путем применения утвержденных правил, созданных для подключенного или аналогичного источника данных. Дополнительные сведения о правилах исправления данных см. в разделе [DQS Knowledge Bases and Domains](../../../data-quality-services/dqs-knowledge-bases-and-domains.md). Дополнительные сведения о службах DQS см. в разделе [Data Quality Services Concepts](../../../data-quality-services/data-quality-services-concepts.md).  
  
 Чтобы определить, требуется ли исправление данных, преобразование «Очистка DQS» обрабатывает данные из входного столбца, когда выполняются следующие условия.  
  
-   Столбец выбран для корректировки данных.  
  
-   Данные столбца относятся к типу, пригодному для корректировки данных.  
  
-   Столбец сопоставлен с доменом, имеющим совместимый тип данных.  
  
 Преобразование также включает вывод ошибок, настроенный пользователем для обработки ошибок на уровне строк. Чтобы настроить вывод ошибок, запустите **Редактор преобразования «Очистка DQS»**.  
  
 В поток данных можно включить [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md) для определения строк данных, которые, вероятнее всего, будут повторяться.  
  
## Проекты и значения служб DQS  
 При обработке данных с помощью преобразования «Очистка DQS» на сервере DQS создается проект очистки. Для управления проектом используется клиент DQS. Кроме того, можно использовать клиент DQS для импорта значений проекта в домен базы знаний служб DQS. Можно импортировать значения только в домен (или связанный домен), использование которого было настроено в преобразовании «Очистка DQS».  
  
## Связанные задачи  
  
-   [Открытие проектов служб Integration Services в клиенте DQS](../../../data-quality-services/open-integration-services-projects-in-data-quality-client.md)  
  
-   [Импорт значений проекта очистки в домен](../../../data-quality-services/import-cleansing-project-values-into-a-domain.md)  
  
-   [Применение правил качества данных к источнику данных](../../../integration-services/data-flow/transformations/apply-data-quality-rules-to-data-source.md)  
  
## См. также  
  
-   [Открытие, разблокировка, переименование и удаление проекта качества данных](https://msdn.microsoft.com/library/hh510417.aspx)  
  
-   Статья [Очистка сложных данных с использованием составных доменов](http://social.technet.microsoft.com/wiki/contents/articles/13324.using-dqs-cleansing-complex-data-using-composite-domains.aspx)на сайте social.technet.microsoft.com.  
  
  