---
description: Ограничения для Stretch Database
title: Ограничения для Stretch Database
ms.date: 06/14/2016
ms.service: sql-server-stretch-database
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Stretch Database, limitations
- Stretch Database, blocking issues
- limitations (Stretch Database)
- blocking issues (Stretch Database)
ms.assetid: 2b1fbec1-7859-44fc-8417-724fc57a59c0
author: rothja
ms.author: jroth
ms.custom: seo-dt-2019
ms.openlocfilehash: c53fe235850dbb932e5773c82cc22cc19d62e749
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88454366"
---
# <a name="limitations-for-stretch-database"></a>Ограничения для Stretch Database
[!INCLUDE [sqlserver2016-windows-only](../../includes/applies-to-version/sqlserver2016-windows-only.md)]


  Дополнительные сведения об ограничениях для таблиц с поддержкой растяжения и об ограничениях, не позволяющих включать Stretch для таблицы.  
  
##  <a name="limitations-for-stretch-enabled-tables"></a><a name="Caveats"></a> Ограничения для таблиц, совместимых со Stretch  
  
В таблицах с поддержкой Stretch действуют указанные ниже ограничения.  
  
### <a name="constraints"></a>Ограничения  
-   В таблице Azure, содержащей перенесенные данные, не обеспечивается уникальность для ограничений UNIQUE и PRIMARY KEY.  
  
### <a name="dml-operations"></a>Операции DML  
-   Нельзя обновлять или удалять из таблицы с поддержкой Stretch или представления, содержащего такие таблицы, перенесенные строки или строки, подходящие для переноса.  
  
-   Нельзя вставлять строки в таблицу с поддержкой Stretch на связанном сервере.  
  
### <a name="indexes"></a>Индексы  
-   Нельзя создать индекс для представления, включающего в себя таблицу, совместимую со Stretch.  
  
-   Фильтры индексов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не распространяются на удаленную таблицу.  
  
##  <a name="limitations-that-currently-prevent-you-from-enabling-stretch-for-a-table"></a><a name="Limitations"></a> Ограничения, не позволяющие включить в таблице поддержку Stretch  
   
 В настоящее время включить в таблице поддержку Stretch не позволяют указанные ниже элементы.  
  
 ### <a name="table-properties"></a>Свойства таблицы  
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
  
 ### <a name="column-types"></a>Типы столбцов  
 -   COLUMN_SET;  
  
-   Вычисляемые столбцы  
  
### <a name="constraints"></a>Ограничения  
-   Ограничения по умолчанию и проверочные ограничения  
  
-   Ограничения внешнего ключа со ссылкой на таблицу. В иерархическом отношении (например, Order и Order_Detail) можно включить поддержку Stretch для дочерней таблицы (Order_Detail), но не для родительской таблицы (Order).  
  
### <a name="indexes"></a>Индексы  
-   Полнотекстовые индексы  
  
-   XML-индексы  
  
-   Пространственные индексы  
  
-   Индексированные представления, которые ссылаются на таблицу  
  
## <a name="see-also"></a>См. также:  
 [Определение баз данных и таблиц для Stretch Database с использованием помощника Stretch Database](../../sql-server/stretch-database/stretch-database-databases-and-tables-stretch-database-advisor.md)   
 [Включение Stretch Database для базы данных](../../sql-server/stretch-database/enable-stretch-database-for-a-database.md)   
 [Настройка базы данных Stretch для таблицы](../../sql-server/stretch-database/enable-stretch-database-for-a-table.md)  
  
  
