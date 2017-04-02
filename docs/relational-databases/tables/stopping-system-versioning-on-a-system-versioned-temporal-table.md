---
title: "Остановка системного управления версиями в темпоральной таблице с системным управлением версиями | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "10/11/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-tables"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dddd707e-bfb1-44ff-937b-a84c5e5d1a94
caps.latest.revision: 10
author: "CarlRabeler"
ms.author: "carlrab"
manager: "jhubbard"
caps.handback.revision: 10
---
# Остановка системного управления версиями в темпоральной таблице с системным управлением версиями
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Возможно, вам временно или навсегда понадобится остановить управление версиями в темпоральной таблице.   
Для этого нужно задать для предложения **SYSTEM_VERSIONING** значение **OFF**.  
  
## Установка для предложения SYSTEM_VERSIONING значения OFF  
 Остановите системное управление версиями, если в темпоральной таблице нужно провести определенные операции обслуживания или если таблица с управлением версиями больше не нужна. В результате этой операции вы получите две отдельные таблицы:  
  
-   текущую таблицу с определением периода;  
  
-   прежнюю таблицу в качестве обычной таблицы.  
  
### Важные замечания  
  
-   Если задать значение **SYSTEM_VERSIONING = OFF** или удалить период **SYSTEM_TIME**, это не приведет к потере данных.  
  
-   Если задать **SYSTEM_VERSIONING = OFF** и не исключить удаление периода **SYSTEM_TIME**, система продолжит обновлять столбцы периода при каждой операции вставки и обновления. Элементы, удаленные из текущей таблицы, не подлежат восстановлению.  
  
-   Удалите период **SYSTEM_TIME**, чтобы полностью удалить столбцы периода.  
  
-   Если задать **SYSTEM_VERSIONING = OFF**, все пользователи с необходимыми разрешениями смогут изменять схему и содержимое прежней таблицы или даже окончательно удалить ее.  
  
### Окончательное удаление SYSTEM_VERSIONING  
 В этом примере окончательно удаляется параметр SYSTEM_VERSIONING и полностью удаляются столбцы периода. Удалять столбцы периода необязательно.  
  
```  
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
/*Optionally, DROP PERIOD if you want to revert temporal table to a non-temporal*/   
ALTER TABLE dbo.Department   
DROP PERIOD FOR SYSTEM_TIME;  
  
```  
  
### Временное удаление SYSTEM_VERSIONING  
 Это список операций, которые требуют, чтобы для системного управления версиями было задано значение **OFF**:  
  
-   удаление ненужных данных из журнала (**DELETE** или **TRUNCATE**);  
  
-   удаление данных из текущей таблицы без управления версиями (**DELETE**, **TRUNCATE**);  
  
-   секционирование **SWITCH OUT** из текущей таблицы;  
  
-   секционирование **SWITCH IN** в прежнюю таблицу.  
  
 В этом примере действие SYSTEM_VERSIONING временно прекращается для выполнения определенных операций обслуживания. Если необходимо временно остановить управление версиями для обслуживания таблицы, настоятельно рекомендуем делать это в ходе транзакции, чтобы обеспечить согласованность данных.  
  
```  
BEGIN TRAN   
ALTER TABLE dbo.Department SET (SYSTEM_VERSIONING = OFF);   
TRUNCATE TABLE [History].[DepartmentHistory]   
WITH (PARTITIONS (1,2))   
ALTER TABLE dbo.Department SET    
(   
SYSTEM_VERSIONING = ON (HISTORY_TABLE = History.DepartmentHistory)   
);   
COMMIT ;  
  
```  
  
## Эта статья помогла вам? Мы слушаем  
 Какие сведения вы искали и удалось ли вам их найти? Мы прислушиваемся к вашим отзывам для совершенствования материалов. Отправляйте свои комментарии по адресу [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Stopping%20System-Versioning%20on%20a%20System-Version%20Temporal%20Table%20page).  
  
## См. также:  
 [Темпоральные таблицы](../../relational-databases/tables/temporal-tables.md)   
 [Приступая к работе c темпоральными таблицами с системным управлением версиями](../../relational-databases/tables/getting-started-with-system-versioned-temporal-tables.md)   
 [Управление хранением данных журнала в темпоральных таблицах с системным управлением версиями](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Темпоральные таблицы с системным управлением версиями и таблицы, оптимизированные для памяти](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Создание темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/creating-a-system-versioned-temporal-table.md)   
 [Изменение данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/modifying-data-in-a-system-versioned-temporal-table.md)   
 [Запрос данных в темпоральной таблице с системным управлением версиями](../../relational-databases/tables/querying-data-in-a-system-versioned-temporal-table.md)   
 [Изменение схемы темпоральной таблицы с системным управлением версиями](../../relational-databases/tables/changing-the-schema-of-a-system-versioned-temporal-table.md)  
  
  