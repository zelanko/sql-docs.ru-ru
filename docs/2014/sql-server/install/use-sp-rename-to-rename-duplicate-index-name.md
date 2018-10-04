---
title: С помощью хранимой процедуры sp_rename переименуйте повторяющиеся имена индексов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- table names [SQL Server]
- duplicate table names
- index names [SQL Server]
- sp_rename
- duplicate index names
ms.assetid: ee66c7a5-eb6d-4fcf-970c-ab099d78c8d9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 641dbb6e33f7b39a7542fdd43a940c487a4b21d9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48093044"
---
# <a name="use-sprename-to-rename-duplicate-index-name"></a>При помощи хранимой процедуры sp_rename переименуйте повторяющиеся имена индексов
  Советник по переходу обнаружил повторяющиеся имена таблиц или индексированных представлений. Перед обновлением переименуйте повторяющиеся индексы, чтобы их не было.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
  
1.  Определите наличие повторяющихся имен индексов, выполнив следующий запрос.  
  
    ```  
    SELECT DISTINCT OBJECT_NAME(o.id), name  
    FROM sysindexes as o  
    WHERE EXISTS   
        (SELECT name FROM sysindexes  as i  
          WHERE i.id = o.id  
          AND i.name = o.name and i.indid < o.indid);  
    ```  
  
2.  Используйте **sp_rename** для изменения одного из имен индексов. Поскольку имена индексов одинаковые, невозможно определить, какой из этих индексов будет переименован. Следующий шаг позволит различить такие индексы.  
  
    ```  
    EXEC sp_rename N'table_name.index_name', N'new_index_name', N'INDEX'  
    ```  
  
3.  Проверьте, какой из индексов был переименован, выполнив следующий запрос. Этот запрос возвращает все индексы, включая имена ключевых столбцов, в указанной таблице или представлении.  
  
    ```  
    SELECT i.name AS IndexName, c.name AS ColumnName, ik.colid, ik.keyno  
    FROM sysindexes i  
    JOIN sysindexkeys ik ON i.id = ik.id and i.indid = ik.indid   
    JOIN syscolumns c ON c.id = ik.id and ik.colid = c.colid  
    WHERE i.id = OBJECT_ID('table_or_view_name')  
    ```  
  
4.  При необходимости используйте **sp_rename** еще раз, чтобы исправления имен индексов.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
