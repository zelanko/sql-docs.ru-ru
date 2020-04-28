---
title: sys. sp_cdc_get_captured_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns
- sys.sp_cdc_get_captured_columns_TSQL
- sp_cdc_get_captured_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_get_captured_columns
- sp_cdc_get_captured_columns
- change data capture [SQL Server], querying metadata
ms.assetid: d9e680be-ab9b-4e0c-b63a-90658f241df8
author: rothja
ms.author: jroth
ms.openlocfilehash: cf7c7ff03ec1318b1fe2fca8454f8ff39cd336a4
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68083741"
---
# <a name="syssp_cdc_get_captured_columns-transact-sql"></a>sys.sp_cdc_get_captured_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о метаданных системы отслеживания измененных данных для исходных столбцов, отслеживаемых указанным экземпляром отслеживания. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемых различными выпусками, см. [в разделе функции, поддерживаемые различными выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_get_captured_columns   
    [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @capture_instance = ] "*capture_instance*"  
 Имя экземпляра отслеживания, связанного с исходной таблицей. *capture_instance* имеет тип **sysname** и не может иметь значение null.  
  
 Чтобы создать отчет об экземплярах отслеживания для таблицы, выполните хранимую процедуру [sys. sp_cdc_help_change_data_capture](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md) .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Имя схемы исходной таблицы.|  
|source_table|**sysname**|Имя исходной таблицы.|  
|capture_instance|**sysname**|Имя экземпляра отслеживания.|  
|column_name|**sysname**|Имя отслеживаемого исходного столбца данных.|  
|column_id|**int**|Идентификатор столбца в исходной таблице.|  
|column_ordinal|**int**|Положение столбца в исходной таблице.|  
|Тип данных|**sysname**|Тип данных столбца.|  
|character_maximum_length|**int**|Максимальная длина символьного столбца; в противном случае — NULL.|  
|numeric_precision|**tinyint**|Точность чисел для числового столбца; в противном случае — NULL.|  
|numeric_precision_radix|**smallint**|Основание определения точности числовых столбцов; в противном случае — NULL.|  
|numeric_scale|**int**|Масштаб числового столбца; в противном случае — NULL.|  
|datetime_precision|**smallint**|Точность для столбца типа datetime; в противном случае — NULL.|  
  
## <a name="remarks"></a>Remarks  
 Используйте представление sys. sp_cdc_get_captured_columns, чтобы получить сведения о столбцах, возвращенных запросом функций запроса экземпляра отслеживания [CDC. fn_cdc_get_all_changes_<capture_instance>](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md) или [cdc. fn_cdc_get_net_changes_<](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)capture_instance>. Имена, идентификаторы и положение столбцов не изменяются в течение всего времени существования экземпляра отслеживания. Изменяется только тип данных столбца, если изменяется тип данных базового исходного столбца отслеживаемой таблицы. Добавление и удаление столбцов из исходной таблицы не влияет на столбцы, обрабатываемые уже существующими экземплярами отслеживания.  
  
 Используйте представление [sys. sp_cdc_get_ddl_history](../../relational-databases/system-stored-procedures/sys-sp-cdc-get-ddl-history-transact-sql.md) для получения сведений о инструкциях языка описания данных DDL, примененных к исходной таблице. Результирующий набор содержит сведения обо всех изменениях DDL, изменивших структуру отслеживаемого исходного столбца.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли базы данных db_owner. Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных. Если вызывающий объект не имеет разрешения на просмотр исходных данных, то функция возвращает ошибку 22981 (Объект не существует или доступ запрещен).  
  
## <a name="examples"></a>Примеры  
 В следующем примере извлекается информация о столбцах, обрабатываемых экземпляром отслеживания `HumanResources_Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_get_captured_columns   
    @capture_instance = N'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys. sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
