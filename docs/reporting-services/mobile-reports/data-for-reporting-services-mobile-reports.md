---
title: "Data for Reporting Services mobile reports | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "02/08/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91138ef8-ddb4-4ac5-a1e4-fa4cf1c58dcc
caps.latest.revision: 15
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 15
---
# Data for Reporting Services mobile reports
Модель данных для [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-long.md)] очень простая. Данные импортируются в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] как коллекция наборов данных. Формальные отношения между наборами данных не требуются. Уточняющие запросы от одного набора к другому выполняются, если значения их ключей соответствуют. Агрегаты даты и времени обрабатываются в среде выполнения мобильных отчетов. Они совпадают для разных наборов данных, даже если степень детализации данных даты и времени в этих наборах отличается.   
  
Данные можно импортировать из двух источников:   
  
* **Локальные файлы Excel**. Выберите документ Excel и укажите, какие листы необходимо импортировать. После импорта эти данные сохраняются в определении мобильного отчета. Чтобы обновить данные из исходного файла Excel, используйте команду **Обновить данные** в верхнем правом углу вкладки **Данные** в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)]. См. дополнительные сведения о [подготовке данных Excel для мобильных отчетов SSRS](../../reporting-services/mobile-reports/prepare-excel-data-for-reporting-services-mobile-reports.md).  
  
* **Общие наборы данных [!INCLUDE[PRODUCT_NAME](../../includes/server-product-name.md)]**. Просмотрите список опубликованных наборов данных на сервере и выберите те, которые нужно добавить в мобильный отчет. Мобильные отчеты на основе данных сервера всегда остаются связанными с исходными наборами данных сервера и отражают последнее состояние данных на сервере. См. [список поддерживаемых источников данных](https://msdn.microsoft.com/library/ms159219.aspx).   
  
  См. дополнительные сведения о [получении данных из общих наборов в издателе мобильных отчетов](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md).  
  
После импорта данных в [!INCLUDE[PRODUCT_NAME](../../includes/ss-mobilereptpub-short.md)] процедура создания и проектирования мобильных отчетов одинакова при любом источнике данных.   
  
## Подключение элементов мобильного отчета к данным ##  
  
Каждый элемент [!INCLUDE[PRODUCT_NAME](../../includes/short-product-name.md)] содержит один или несколько параметров данных. Например, элемент радиального датчика содержит два параметра данных: основное значение и значение для сравнения. Каждый из этих параметров указывает только на одно поле (столбец) в конкретном представлении данных.   
  
Среда выполнения мобильных отчетов предоставляет совокупные значения датчика на основе выбора пользователя. Обратите внимание, что значение для сравнения одного и того же экземпляра радиального датчика может быть привязано к полю в другом представлении данных.   
  
### См. также:  
-  [Prepare data for Reporting Services mobile reports](../../reporting-services/mobile-reports/prepare-data-for-reporting-services-mobile-reports.md)
- [Создание и публикация мобильных отчетов с помощью издателя мобильных отчетов SQL Server](../../reporting-services/mobile-reports/create-mobile-reports-with-sql-server-mobile-report-publisher.md)  
- [Get data from shared datasets](../../reporting-services/mobile-reports/get-data-from-shared-datasets-in-reporting-services-mobile-reports.md)
- [Сохранение форматирования дат для данных служб Analysis Services в мобильных отчетах](../../reporting-services/mobile-reports/retain-date-formatting-for-analysis-services-in-mobile-reports.md) 
  
  
