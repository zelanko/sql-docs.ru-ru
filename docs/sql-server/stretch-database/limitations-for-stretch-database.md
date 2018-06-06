---
title: Ограничения для Stretch Database | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, limitations
- Stretch Database, blocking issues
- limitations (Stretch Database)
- blocking issues (Stretch Database)
ms.assetid: 2b1fbec1-7859-44fc-8417-724fc57a59c0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5537ba71505cf14657e69f0e3ec5ccb8b125ebf3
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34773140"
---
# <a name="limitations-for-stretch-database"></a>Ограничения для Stretch Database
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md-winonly.md)]


  Дополнительные сведения об ограничениях для таблиц с поддержкой растяжения и об ограничениях, не позволяющих включать Stretch для таблицы.  
  
##  <a name="Caveats"></a> Ограничения для таблиц, совместимых со Stretch  
  
В таблицах с поддержкой Stretch действуют указанные ниже ограничения.  
  
### <a name="constraints"></a>Ограничения  
-   В таблице Azure, содержащей перенесенные данные, не обеспечивается уникальность для ограничений UNIQUE и PRIMARY KEY.  
  
### <a name="dml-operations"></a>Операции DML  
-   Нельзя обновлять или удалять из таблицы с поддержкой Stretch или представления, содержащего такие таблицы, перенесенные строки или строки, подходящие для переноса.  
  
-   Нельзя вставлять строки в таблицу с поддержкой Stretch на связанном сервере.  
  
### <a name="indexes"></a>Индексы  
-   Нельзя создать индекс для представления, включающего в себя таблицу, совместимую со Stretch.  
  
-   Фильтры индексов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не распространяются на удаленную таблицу.  
  
##  <a name="Limitations"></a> Ограничения, не позволяющие включить в таблице поддержку Stretch  
   
 В настоящее время включить в таблице поддержку Stretch не позволяют указанные ниже элементы.  
  
 ### <a name="table-properties"></a>Свойства таблицы:  
-   Таблицы, содержащие больше 1023 столбцов или больше 998 индексов  
  
-   Таблицы FileTable или таблицы, содержащие данные FILESTREAM  
  
-   Таблицы, активно использующие отслеживание изменений или запись измененных данных  
  
-   Таблицы, оптимизированные для памяти  
  
### <a name="data-types"></a>Типы данных  
-   ntext, ntext, и image  
  
-   TIMESTAMP  
  
-   sql_variant  
  
-   XML  
  
-   Типы данных CLR, включая geometry, geography, hierarchyid и определяемые пользователем типы CLR  
  
 ### <a name="column-types"></a>Типы столбцов:  
 -   COLUMN_SET;  
  
-   Вычисляемые столбцы  
  
### <a name="constraints"></a>Ограничения  
-   Ограничения по умолчанию и проверочные ограничения  
  
-   Ограничения внешнего ключа со ссылкой на таблицу. В иерархическом отношении (например, Order и Order_Detail) можно включить поддержку Stretch для дочерней таблицы (Order_Detail), но не для родительской таблицы (Order).  
  
### <a name="indexes"></a>Индексы  
-   Полнотекстовые индексы  
  
-   XML-индексы  
  
-   Пространственные индексы  
  
-   индексированные представления, которые ссылаются на таблицу.  
  
## <a name="see-also"></a>См. также:  
 [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Включение Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Настройка базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  
