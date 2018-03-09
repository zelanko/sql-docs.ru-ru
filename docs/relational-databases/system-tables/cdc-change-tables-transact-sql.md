---
title: "CDC.change_tables (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- cdc.change_tables
- cdc.change_tables_TSQL
dev_langs: TSQL
helpviewer_keywords: cdc.change_tables
ms.assetid: 3525a5f5-8d8b-46a8-b334-4b7cd9fb7c21
caps.latest.revision: "23"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dd28fa79040f39fd62c33b15478d18ed34766a8f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="cdcchangetables-transact-sql"></a>cdc.change_tables (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по одной строке для каждой таблицы изменений в базе данных. Таблица изменений, созданная при включении системы отслеживания измененных данных в исходной таблице. Не рекомендуется непосредственно запрашивать системные таблицы. Вместо этого выполните [sys.sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) хранимой процедуры.  
  |Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор таблицы изменений. Уникален в базе данных.|  
|**version**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] этот столбец возвращает 0.|  
|**source_object_id**|**int**|Идентификатор исходной таблицы, в который включена система отслеживания измененных данных.|  
|**capture_instance**|**sysname**|Имя экземпляра отслеживания, использующегося для именования объектов отслеживания, относящихся к конкретным экземплярам. По умолчанию имя является производным от имени схемы источника и имени исходной таблицы в формате *schemaname_sourcename*.|  
|**start_lsn**|**binary(10)**|Регистрационный номер транзакции в журнале (номер LSN), представляющий нижнюю конечную точку при запросе данных изменений в таблице изменений.<br /><br /> NULL = не установлена нижняя конечная точка.|  
|**end_lsn**|**binary(10)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] этот столбец всегда возвращает NULL.|  
|**supports_net_changes**|**bit**|Поддержка запросов сетевых изменений включается в таблице изменений.|  
|**has_drop_pending**|**bit**|Процесс отслеживания получил уведомление об удалении исходной таблицы.|  
|**role_name**|**sysname**|Имя роли базы данных, которая использовалась для доступа к данным изменений.<br /><br /> NULL = роль не используется.|  
|**index_name**|**sysname**|Имя индекса, который использовался для уникальной идентификации строк в исходной таблице. **index_name** имя индекса первичного ключа исходной таблицы или имя уникального индекса, указанного при включении отслеживания измененных данных в исходной таблице.<br /><br /> NULL = исходная таблица не имела первичного ключа при включении системы отслеживания измененных данных, а также не был задан уникальный индекс при включении системы отслеживания измененных данных.<br /><br /> Примечание: Если измененных данных будет включен в таблице, где существует первичный ключ, функцию отслеживания изменений данных использует индекс независимо от того, включено ли суммарных изменений. После включения системы отслеживания измененных данных в первичном ключе изменения не допускаются. Если в таблице нет первичного ключа, систему отслеживания измененных данных можно включить, но только при суммарных изменениях, установленных в false. После включения системы отслеживания измененных данных можно создать первичный ключ. Можно также изменить первичный ключ, поскольку система отслеживания измененных данных не использует первичный ключ.|  
|**filegroup_name**|**sysname**|Имя файловой группы, в которой расположена таблица изменений.<br /><br /> NULL = таблица изменений расположена в файловой группе по умолчанию для базы данных.|  
|**create_date**|**datetime**|Дата включения исходной таблицы.|  
|**partition_switch**|**bit**|Указывает, является ли **SWITCH PARTITION** команде **ALTER TABLE** могут быть выполнены для таблицы, в которой включено отслеживание изменений в данных. Значение 0 указывает на то, что переключение секций заблокировано. Несекционированные таблицы всегда возвращают значение 1.|  
  
## <a name="see-also"></a>См. также:  
 [sys.sp_cdc_help_change_data_capture &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
