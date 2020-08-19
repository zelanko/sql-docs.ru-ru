---
description: sys.sp_cdc_get_ddl_history (Transact-SQL)
title: sys. sp_cdc_get_ddl_history (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_get_ddl_history
- sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history_TSQL
- sys.sp_cdc_get_ddl_history
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sp_cdc_get_ddl_history
- sys.sp_cdc_get_ddl_history
ms.assetid: 4dee5e2e-d7e5-4fea-8037-a4c05c969b3a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f9835c61aeb1f11b57250465697187cfcc6501f8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88446661"
---
# <a name="syssp_cdc_get_ddl_history-transact-sql"></a>sys.sp_cdc_get_ddl_history (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает журнал изменений языка описания данных DDL, связанный с заданным экземпляром записи, со времени включения системы отслеживания информации об изменениях данных для этого экземпляра записи. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_get_ddl_history [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @capture_instance =] "*capture_instance*"  
 Имя экземпляра отслеживания, связанного с исходной таблицей. *capture_instance* имеет тип **sysname** и не может иметь значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Имя схемы исходной таблицы.|  
|source_table|**sysname**|Имя исходной таблицы.|  
|capture_instance|**sysname**|Имя экземпляра отслеживания.|  
|required_column_update|**bit**|Указывает, что изменение DDL требует обновления столбца в таблице изменений, чтобы отразить изменения типа данных в исходном столбце.|  
|ddl_command|**nvarchar(max)**|Инструкция DDL, примененная к исходной таблице.|  
|ddl_lsn|**binary(10)**|Регистрационный номер транзакции в журнале (LSN), связанный с изменением DDL.|  
|ddl_time|**datetime**|Время изменения DDL.|  
  
## <a name="remarks"></a>Remarks  
 Изменения DDL в исходной таблице, которые изменяют структуру столбцов исходной таблицы, например добавление или удаление столбца или изменение типа данных существующего столбца, хранятся в таблице [CDC. ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) . Эти изменения доступны хранимым процедурам. Записи в таблицу «cdc.ddl_history» добавляются во время считывания процессом отслеживания транзакций DDL в журнале.  
  
## <a name="permissions"></a>Разрешения  
 Для возвращения строк всех экземпляров отслеживания в базе данных необходимо членство в предопределенной роли базы данных «db_owner». Всем остальным пользователям необходимо разрешение SELECT для всех отслеживаемых столбцов в исходной таблице. Кроме того, если для экземпляра отслеживания была определена шлюзовая роль, требуется членство в этой роли базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере добавляется столбец в исходную таблицу `HumanResources.Employee`, а затем выполняется хранимая процедура `sys.sp_cdc_get_ddl_history` для сообщения о всех изменениях DDL, которые применялись к исходной таблице, связанной с экземпляром отслеживания `HumanResources_Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
ALTER TABLE HumanResources.Employee  
ADD Test_Column int NULL;  
GO  
-- Pause 10 seconds to allow the event to be logged.   
WAITFOR DELAY '00:00:10';  
GO   
EXECUTE sys.sp_cdc_get_ddl_history   
    @capture_instance = 'HumanResources_Employee';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys. sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
