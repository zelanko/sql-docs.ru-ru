---
title: Получить поля для всех событий | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extended events [SQL Server], getting fields
- xe
ms.assetid: 4e4ee03f-5bca-42ed-a37c-db1c82e3aad2
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fac62e2160086d920e3e73e770eaaf1cc82e0b88
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191877"
---
# <a name="get-the-fields-for-all-events"></a>получить поля для всех событий
  Выполнение этой задачи предполагает использование редактора запросов в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 После выполнения инструкций данной процедуры на вкладке **Результаты** редактора запросов будут отображены следующие столбцы.  
  
-   package_name  
  
-   event_name  
  
-   event_field  
  
-   field_type  
  
-   column_type  
  
 Можно использовать приведенные выше сведения при настройке сеансов событий, в которых используются сегментированные цели. Дополнительные сведения см. в разделе [SQL Server Extended Events Targets](../../2014/database-engine/sql-server-extended-events-targets.md).  
  
## <a name="before-you-begin"></a>Перед началом работы  
 Перед созданием сеанса расширенных событий [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] рекомендуется выявить поля, связанные с этими событиями.  
  
## <a name="to-get-the-fields-for-all-events-using-query-editor"></a>Получение полей для всех событий с помощью редактора запросов  
  
-   В редакторе запросов выполните следующие инструкции.  
  
    ```  
    select p.name package_name, o.name event_name, c.name event_field, c.type_name field_type, c.column_type column_type  
    from sys.dm_xe_objects o  
    join sys.dm_xe_packages p  
          on o.package_guid = p.guid  
    join sys.dm_xe_object_columns c  
          on o.name = c.object_name  
    where o.object_type = 'event'  
    order by package_name, event_name  
    ```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_xe_objects (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)   
 [sys.dm_xe_packages (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
