---
title: "Ограничения для базы данных Stretch | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/14/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.service: "sql-server-stretch-database"
ms.suite: ""
ms.technology: 
  - "dbe-stretch"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "База данных Stretch, ограничения"
  - "База данных Stretch, критические препятствия"
  - "ограничения (база данных Stretch)"
  - "критические препятствия (база данных Stretch)"
ms.assetid: 2b1fbec1-7859-44fc-8417-724fc57a59c0
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# Ограничения для базы данных Stretch
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Дополнительные сведения об ограничениях для таблиц с поддержкой растяжения и об ограничениях, не позволяющих включать Stretch для таблицы.  
  
##  <a name="Caveats"></a> Ограничения для таблиц, совместимых со Stretch  
  
В таблицах с поддержкой Stretch действуют указанные ниже ограничения.  
  
### Ограничения  
-   В таблице Azure, содержащей перенесенные данные, не обеспечивается уникальность для ограничений UNIQUE и PRIMARY KEY.  
  
### Операции DML  
-   Нельзя обновлять или удалять из таблицы с поддержкой Stretch или представления, содержащего такие таблицы, перенесенные строки или строки, подходящие для переноса.  
  
-   Нельзя вставлять строки в таблицу с поддержкой Stretch на связанном сервере.  
  
### Индексы  
-   Нельзя создать индекс для представления, включающего в себя таблицу, совместимую со Stretch.  
  
-   Фильтры индексов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не распространяются на удаленную таблицу.  
  
##  <a name="Limitations"></a> Ограничения, не позволяющие включить в таблице поддержку Stretch  
   
 В настоящее время включить в таблице поддержку Stretch не позволяют указанные ниже элементы.  
  
 ### Свойства таблицы:  
-   Таблицы, содержащие больше 1023 столбцов или больше 998 индексов  
  
-   Таблицы FileTable или таблицы, содержащие данные FILESTREAM  
  
-   Таблицы, активно использующие отслеживание изменений или запись измененных данных  
  
-   Таблицы, оптимизированные для памяти  
  
 ### Типы данных  
 -   ntext, ntext, и image  
  
-   timestamp  
  
-   sql_variant  
  
-   XML  
  
-   Типы данных CLR, включая geometry, geography, hierarchyid и определяемые пользователем типы CLR  
  
 ### Типы столбцов:  
 -   COLUMN_SET;  
  
-   Вычисляемые столбцы  
  
### Ограничения  
-   Ограничения по умолчанию и проверочные ограничения  
  
-   Ограничения внешнего ключа со ссылкой на таблицу. В иерархическом отношении (например, Order и Order_Detail) можно включить поддержку Stretch для дочерней таблицы (Order_Detail), но не для родительской таблицы (Order).  
  
### Индексы  
-   Полнотекстовые индексы  
  
-   XML-индексы  
  
-   Пространственные индексы  
  
-   индексированные представления, которые ссылаются на таблицу.  
  
## См. также:  
 [Определение баз данных и таблиц для базы данных Stretch с использованием помощника базы данных Stretch](../../sql-server/stretch-database/stretch database databases and tables - stretch database advisor.md)   
 [Включение базы данных Stretch для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Настройка базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  