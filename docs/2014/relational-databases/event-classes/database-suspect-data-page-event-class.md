---
title: Класс событий Database Suspect Data Page | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- suspect_pages system table
- database mirroring [SQL Server], event notifications
- Database Suspect Data Page event class
ms.assetid: 098e1443-a8a0-425c-9311-0a479b1370ed
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 78e6a175ce7757a9e9808a5a993bec6a44a3db2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62662997"
---
# <a name="database-suspect-data-page-event-class"></a>Database Suspect Data Page, класс событий
  Класс событий **Database Suspect Data Page** регистрирует добавление страниц в таблицу [suspect_pages](/sql/relational-databases/system-tables/suspect-pages-transact-sql) базы данных [msdb](../databases/msdb-database.md). Он включается в трассировки для отслеживания появления подозрительных страниц.  
  
> [!NOTE]  
>  Данное событие возникает асинхронно по отношению к вставке соответствующей строки в таблицу **suspect_pages** . Таким образом, прослушивающее это событие задание даже может не сразу обнаружить соответствующую запись в таблице **suspect_pages** .  
  
 Если класс событий **Database Suspect Data Page** включен в трассировку, связанные с этим издержки невелики. Но они могут увеличиться при увеличении количества подозрительных страниц, например при проблемах с жестким диском.  
  
## <a name="database-suspect-data-page-event-class-data-columns"></a>Столбцы данных класса событий Database Suspect Data Page  
  
|Имя столбца данных|Тип данных|Description|Идентификатор столбца|Фильтруемый|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|Идентификатор базы данных, для которой возникло событие подозрительной страницы. Это то же самое, что столбец **database_id** таблицы **suspect_pages** .|3|Да|  
|**EventClass**|**int**|Событие имеет тип 213.|27|нет|  
|**EventSequence**|**int**|Порядковый номер класса событий в пакете.|51|нет|  
|**SPID**|**int**|Идентификатор задачи [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , при выполнении которой возникла подозрительная страница.|12|Да|  
|**StartTime**|**datetime**|Время возникновения события.|14|Да|  
|**ObjectID**|**int**|Идентификатор файла базы данных, содержащего подозрительную страницу. Это то же самое, что столбец **file_id** таблицы **suspect_pages** .|22|Да|  
|**ObjectID2**|**int**|Идентификатор подозрительной страницы в файле. Это то же самое, что столбец **page_id** таблицы **suspect_pages** .|56|Да|  
|**Ошибка**|**int**|Тип происшедшей ошибки. Это значение такое же, как и значение **event_type** для страницы таблицы **suspect_pages** .|31|Да|  
  
## <a name="see-also"></a>См. также:  
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Управление таблицей suspect_pages (SQL Server)](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
