---
title: sys.sp_cdc_get_ddl_history (Transact-SQL) | Документация Майкрософт
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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 657d7b6cc21c573d2d9535d36392f9b7eb94200f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47827224"
---
# <a name="sysspcdcgetddlhistory-transact-sql"></a>sys.sp_cdc_get_ddl_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает журнал изменений языка описания данных DDL, связанный с заданным экземпляром записи, со времени включения системы отслеживания информации об изменениях данных для этого экземпляра записи. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_get_ddl_history [ @capture_instance = ] 'capture_instance'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @capture_instance =] '*capture_instance*"  
 Имя экземпляра отслеживания, связанного с исходной таблицей. *capture_instance* — **sysname** и не может иметь значение NULL.  
  
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
  
## <a name="remarks"></a>Примечания  
 Изменения DDL в исходной таблице, которые изменяют структуру столбцов, таких как добавление или удаление столбца или изменения существующего столбца, тип данных сохраняются в [cdc.ddl_history](../../relational-databases/system-tables/cdc-ddl-history-transact-sql.md) таблицы. Эти изменения доступны хранимым процедурам. Записи в таблицу «cdc.ddl_history» добавляются во время считывания процессом отслеживания транзакций DDL в журнале.  
  
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
  
## <a name="see-also"></a>См. также  
 [sys.sp_cdc_help_change_data_capture &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-help-change-data-capture-transact-sql.md)  
  
  
