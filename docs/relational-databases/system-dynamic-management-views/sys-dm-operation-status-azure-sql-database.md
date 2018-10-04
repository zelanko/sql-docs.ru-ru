---
title: sys.dm_operation_status (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/05/2017
ms.prod: ''
ms.prod_service: sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_operation_status_TSQL
- dm_operation_status
- sys.dm_operation_status
- sys.dm_operation_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_operation_status dynamic management view
- sys.dm_operation_status dynamic management view
ms.assetid: cc847784-7f61-4c69-8b78-5f971bb24d61
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 335888ba664751bb20348472736ad697b8fe2b6d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633482"
---
# <a name="sysdmoperationstatus-azure-sql-database"></a>sys.dm_operation_status (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Возвращает сведения об операциях, выполненных в базах данных на сервере [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|Идентификатор операции. Не равно NULL.|  
|resource_type|**int**|Обозначает тип ресурса, в котором выполняется операция. Не равно NULL. В текущем выпуске это представление отслеживает операции, выполняемые только в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и соответствующие целочисленному значению 0.|  
|resource_type_desc|**nvarchar(2048)**|Описание типа ресурса, в котором выполняется операция. В текущем выпуске это представление отслеживает операции, выполняемые только в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
|major_resource_id|**sql_variant**|Имя ресурса [!INCLUDE[ssSDS](../../includes/sssds-md.md)], в котором выполняется операция. Не равно NULL.|  
|minor_resource_id|**sql_variant**|Только для внутреннего применения. Не равно NULL.|  
|операции|**nvarchar(60)**|Операции, выполняемые на [!INCLUDE[ssSDS](../../includes/sssds-md.md)], такие как CREATE или ALTER.|  
|state|**tinyint**|Состояние операции.<br /><br /> 0 = Ожидает согласования<br />1 = выполняется<br />2 = завершена<br />3 = ошибка<br />4 = отмена|  
|state_desc|**nvarchar(120)**|PENDING = операция ожидает доступности ресурсов или квоты.<br /><br /> IN_PROGRESS = операция запущена и выполняется.<br /><br /> COMPLETED = операция успешно завершена.<br /><br /> FAILED = ошибка операции. См. в разделе **error_desc** столбца сведения.<br /><br /> CANCELLED = выполнение операции остановлено по запросу пользователя.|  
|percent_complete|**int**|Процент завершения выполнения операции. Значения не являются непрерывными и допустимые значения перечислены ниже. Не равно NULL.<br/><br/>0 = операция не запущена<br/>50 = операция выполняется<br/>100 = операция завершена|  
|error_code|**int**|Код ошибки, возникшей при неудачном выполнении операции. Если значение равно 0, операция завершилась успешно.|  
|error_desc|**nvarchar(2048)**|Описание ошибки, которая возникла во время неудачного выполнения операции.|  
|error_severity|**int**|Степень серьезности ошибки, которая возникла во время неудачного выполнения операции. Дополнительные сведения об уровнях серьезности ошибок см. в разделе [степени серьезности ошибок ядра СУБД](http://go.microsoft.com/fwlink/?LinkId=251052).|  
|error_state|**int**|Зарезервировано для последующего использования. Совместимость с будущими версиями не гарантируется.|  
|start_time|**datetime**|Метка времени начала операции.|  
|last_modify_time|**datetime**|Метка времени последнего изменения записи для длительных операций. Для успешно выполненных операций в этом поле отображается метка времени завершения операции.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно только в **master** базы данных имени входа субъекта уровня сервера.  
  
## <a name="remarks"></a>Примечания  
 Для использования этого представления, должны быть подключены к **master** базы данных. Используйте `sys.dm_operation_status` просмотра в **master** базы данных из [!INCLUDE[ssSDS](../../includes/sssds-md.md)] server для отслеживания состояния следующих операций, выполняемых на [!INCLUDE[ssSDS](../../includes/sssds-md.md)]:  
  
-   Создание базы данных  
  
-   Копирование базы данных. Копирование базы данных создает запись данного представления на исходном и целевом серверах.  
  
-   Изменение базы данных  
  
-   Изменение уровня производительности уровня службы  
  
-   Изменение уровня службы базы данных, например с Basic на Standard.  
  
-   Настройка связи георепликации.  
  
-   Завершение связи георепликации.  
  
-   Восстановление базы данных  
  
-   Удаление базы данных  
  
## <a name="example"></a>Пример  
 Показать последние операции георепликации, связанные с базы данных «mydb».  
  
```  
SELECT * FROM sys.dm_ operation_status   
   WHERE major_resource_id = ‘myddb’   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>См. также  
 [Георепликация динамические административные представления и функции &#40;база данных Azure SQL&#41;](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)   
 [sys.dm_geo_replication_link_status &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys.geo_replication_links &#40;базы данных SQL Azure&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
