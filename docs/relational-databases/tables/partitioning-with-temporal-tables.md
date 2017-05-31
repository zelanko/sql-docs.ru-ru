---
title: "Секционирование с помощью темпоральных таблиц | Документация Майкрософт"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 313714b8-4ad1-4c14-93a3-7f628a334a51
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0134010294aec01d47271a7e00e6a13e4a3ad208
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="partitioning-with-temporal-tables"></a>Секционирование с помощью темпоральных таблиц
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Секционирование в текущей и прежней таблицах можно использовать независимо друг от друга. Но с помощью секционирования нельзя изменить содержание данных без системного управления версиями.  
  
> [!NOTE]  
>  Секционирование доступно для выпуска Enterprise Edition.  
  
-   **Для текущей таблицы:**  
  
    -   **SWITCH IN** to the current table can be used to facilitate data loading and querying while **SYSTEM_VERSIONING** is **ON**  
  
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
  
  

