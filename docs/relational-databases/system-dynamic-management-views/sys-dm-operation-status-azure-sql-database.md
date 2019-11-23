---
title: sys. dm_operation_status (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/05/2017
ms.service: sql-database
ms.reviewer: ''
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
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: c49e4e01dd8ddaf0667546a8cc221a7918f42c81
ms.sourcegitcommit: a154b3050b6e1993f8c3165ff5011ff5fbd30a7e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "70911209"
---
# <a name="sysdm_operation_status-azure-sql-database"></a>sys.dm_operation_status (база данных SQL Azure)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-asdw-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-asdw-xxx-md.md)]

  Возвращает сведения об операциях, выполненных в базах данных на сервере [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
|Column Name|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|session_activity_id|**uniqueidentifier**|Идентификатор операции. Не равно NULL.|  
|resource_type|**int**|Обозначает тип ресурса, в котором выполняется операция. Не равно NULL. В текущем выпуске это представление отслеживает операции, выполняемые только в [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и соответствующие целочисленному значению 0.|  
|resource_type_desc|**nvarchar (2048)**|Описание типа ресурса, в котором выполняется операция. В текущем выпуске это представление отслеживает операции, выполняемые только в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
|major_resource_id|**sql_variant**|Имя ресурса [!INCLUDE[ssSDS](../../includes/sssds-md.md)], в котором выполняется операция. Не равно NULL.|  
|minor_resource_id|**sql_variant**|Только для внутреннего применения. Не равно NULL.|  
|операции|**nvarchar(60)**|Операции, выполняемые на [!INCLUDE[ssSDS](../../includes/sssds-md.md)], такие как CREATE или ALTER.|  
|state|**tinyint**|Состояние операции.<br /><br /> 0 = Ожидает согласования<br />1 = выполняется<br />2 = завершена<br />3 = ошибка<br />4 = отмена|  
|state_desc|**nvarchar(120)**|PENDING = операция ожидает доступности ресурсов или квоты.<br /><br /> IN_PROGRESS = операция запущена и выполняется.<br /><br /> COMPLETED = операция успешно завершена.<br /><br /> FAILED = ошибка операции. Дополнительные сведения см. в столбце **error_desc** .<br /><br /> CANCELLED = выполнение операции остановлено по запросу пользователя.|  
|percent_complete|**int**|Процент завершения выполнения операции. Значения не являются непрерывными, а допустимые значения перечислены ниже. Не равно NULL.<br/><br/>0 = операция не запущена<br/>50 = выполняется операция<br/>100 = операция завершена|  
|error_code|**int**|Код ошибки, возникшей при неудачном выполнении операции. Если значение равно 0, операция завершилась успешно.|  
|error_desc|**nvarchar (2048)**|Описание ошибки, которая возникла во время неудачного выполнения операции.|  
|error_severity|**int**|Степень серьезности ошибки, которая возникла во время неудачного выполнения операции. Дополнительные сведения о серьезности ошибок см. в разделе [ядро СУБД серьезности ошибок](https://go.microsoft.com/fwlink/?LinkId=251052).|  
|error_state|**int**|Зарезервировано для последующего использования. Совместимость с будущими версиями не гарантируется.|  
|start_time|**datetime**|Метка времени начала операции.|  
|last_modify_time|**datetime**|Метка времени последнего изменения записи для длительных операций. Для успешно выполненных операций в этом поле отображается метка времени завершения операции.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно в базе данных **master** только для входа субъекта уровня сервера.  
  
## <a name="remarks"></a>Remarks  
 Чтобы использовать это представление, необходимо подключиться к базе данных **master** . Используйте представление `sys.dm_operation_status` в базе данных **master** сервера [!INCLUDE[ssSDS](../../includes/sssds-md.md)], чтобы отвести состояние следующих операций, выполняемых с [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
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
 Отображение последних операций георепликации, связанных с базой данных "MyDB".  
  
```  
SELECT * FROM sys.dm_operation_status   
   WHERE major_resource_id = 'myddb'   
   ORDER BY start_time DESC;  
```  
  
## <a name="see-also"></a>См. также статью  
 [Динамические административные представления и функции &#40;георепликации  базы данных&#41; SQL Azure](../../relational-databases/system-dynamic-management-views/geo-replication-dynamic-management-views-and-functions-azure-sql-database.md)  
 [sys. dm_geo_replication_link_status &#40;базы&#41; данных SQL Azure](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md)   
 [sys. geo_replication_links &#40;базы&#41; данных SQL Azure](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [ALTER DATABASE (база данных SQL Azure)](../../t-sql/statements/alter-database-azure-sql-database.md)  
  
  
