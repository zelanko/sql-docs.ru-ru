---
title: "Секционирование с помощью темпоральных таблиц | Документация Майкрософт"
ms.custom: 
ms.date: 04/26/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: e76675099ab290d29231d434eb74e92b613185b7
ms.openlocfilehash: cb93e468300aea6a666ad04e9ce6ad20e1b85fc2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/29/2017

---
# <a name="partitioning-with-temporal-tables"></a>Секционирование с помощью темпоральных таблиц
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Секционирование в текущей и прежней таблицах можно использовать независимо друг от друга. Но с помощью секционирования нельзя изменить содержание данных без системного управления версиями.  
  
> [!NOTE]  
>  До выхода SQL Server 2016 с пакетом обновления 1 (SP1) функция секционирования была доступна только в выпусках Enterprise Edition. В SQL Server 2016 с пакетом обновления 1 (SP1) и более поздних версиях секционирование поддерживается во всех выпусках.
  
-   **Для текущей таблицы:**  
  
    -   **SWITCH IN** в текущую таблицу позволяет упростить загрузку данных и выполнение запросов, если **SYSTEM_VERSIONING** имеет значение **ON**  
  
    -   **SWITCH OUT** использовать нельзя, если **SYSTEM_VERSIONING** имеет значение **ON**  
  
-   **Для прежней таблицы:**  
  
    -   **SWITCH OUT** из прежней таблицы можно выполнить для очистки ненужной части данных, если **SYSTEM_VERSIONING** имеет значение **ON** .  
  
    -   **SWITCH IN** нельзя использовать, если **SYSTEM_VERSIONING** имеет значение **ON** , так как это может нарушить согласованность темпоральных данных.  
  
## <a name="did-this-article-help-you-were-listening"></a>Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Partitioning%20with%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Проверка согласованности системной темпоральной таблицы](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Рекомендации и ограничения для темпоральной таблицы](../../relational-databases/tables/temporal-table-considerations-and-limitations.md)   
 [Безопасность темпоральных таблиц](../../relational-databases/tables/temporal-table-security.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Представления и функции метаданных для временной таблицы](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

