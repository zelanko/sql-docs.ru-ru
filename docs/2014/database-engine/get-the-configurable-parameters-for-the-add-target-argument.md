---
title: Получение настраиваемых параметров для аргумента ADD TARGET | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], ADD TARGET argument
- xe
ms.assetid: 08454543-c5c8-4ca3-9af9-f1d82264471c
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 368f019453fe0c8f5fcbef245db3f4b50769a210
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779149"
---
# <a name="get-the-configurable-parameters-for-the-add-target-argument"></a>получить настраиваемые параметры для аргумента ADD TARGET
  Выполнение этой задачи предполагает использование редактора запросов в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 После выполнения инструкций данной процедуры на вкладке **Результаты** редактора запросов будут отображены следующие столбцы.  
  
-   package_name  
  
-   target_name  
  
-   parameter_name  
  
-   parameter_type  
  
-   required  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 Перед созданием сеанса расширенных событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] полезно выяснить, какие параметры можно установить при использовании аргумента ADD TARGET в CREATE EVENT SESSION или ALTER EVENT SESSION.  
  
### <a name="to-get-the-configurable-parameters-for-the-add-target-argument-using-query-editor"></a>Получение настраиваемых параметров для аргумента ADD TARGET с использованием редактора запросов.  
  
-   В редакторе запросов выполните следующие инструкции.  
  
    ```  
    SELECT p.name package_name, o.name target_name, c.name parameter_name,   
    c.type_name parameter_type, CASE c.capabilities_desc WHEN 'mandatory' THEN 'yes' ELSE 'no' END   
    required   
    FROM sys.dm_xe_objects o JOIN sys.dm_xe_packages p ON o.package_guid = p.guid   
    JOIN sys.dm_xe_object_columns c ON o.name = c.object_name AND c.column_type = 'customizable'  
    WHERE o.object_type = 'target'   
    ORDER BY package_name, target_name, required DESC  
    ```  
  
## <a name="see-also"></a>См. также  
 [CREATE EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/create-event-session-transact-sql)   
 [ALTER EVENT SESSION (Transact-SQL)](/sql/t-sql/statements/alter-event-session-transact-sql)   
 [sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
