---
title: sys.sp_cdc_help_change_data_capture (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cdc_help_change_data_capture_TSQL
- sys.sp_cdc_help_change_data_capture_TSQL
- sp_cdc_help_change_data_capture
- sys.sp_cdc_help_change_data_capture
dev_langs:
- TSQL
helpviewer_keywords:
- change data capture [SQL Server], querying metadata
- sys.sp_cdc_help_change_data_capture
- sp_cdc_help_change_data_capture
ms.assetid: 91fd41f5-1b4d-44fe-a3b5-b73eff65a534
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b1fd52d38d96f83c6be7c0a327fca797f934a466
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263220"
---
# <a name="sysspcdchelpchangedatacapture-transact-sql"></a>sys.sp_cdc_help_change_data_capture (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает конфигурацию системы отслеживания измененных данных для каждой таблицы, включенной для системы отслеживания измененных данных в текущей базе данных. Для каждой исходной таблицы может возвращаться до двух строк — по одной строке для каждого экземпляра отслеживания. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о функциях, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_schema =] '*source_schema*"  
 Имя схемы, к которой относится исходная таблица. *source_schema* — **sysname**, значение по умолчанию NULL. Когда *source_schema* указано, *source_name* также должен быть указан.  
  
 Если значение NULL, *source_schema* должен существовать в текущей базе данных.  
  
 Если *source_schema* отлично от NULL, *source_name* также должен иметь значение NULL.  
  
 [ @source_name =] '*source_name*"  
 Имя исходной таблицы. *source_name* — **sysname**, значение по умолчанию NULL. Когда *source_name* указано, *source_schema* также должен быть указан.  
  
 Если значение NULL, *source_name* должен существовать в текущей базе данных.  
  
 Если *source_name* отлично от NULL, *source_schema* также должен иметь значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|source_schema|**sysname**|Имя схемы исходной таблицы.|  
|source_table|**sysname**|Имя исходной таблицы.|  
|capture_instance|**sysname**|Имя экземпляра отслеживания.|  
|object_id|**int**|Идентификатор таблицы изменений, связанной с исходной таблицей.|  
|source_object_id|**int**|Идентификатор исходной таблицы.|  
|start_lsn|**binary(10)**|Регистрационный номер LSN, представляющий нижнюю конечную точку для запроса к таблице изменений.<br /><br /> NULL = не установлена нижняя конечная точка.|  
|end_lsn|**binary(10)**|Номер LSN, представляющий верхнюю конечную точку для запроса к таблице изменений. В [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] этот столбец всегда имеет значение NULL.|  
|supports_net_changes|**бит**|Включена поддержка отслеживания сетевых изменений.|  
|has_drop_pending|**бит**|Не используется в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|имя_роли|**sysname**|Имя роли базы данных, которая использовалась для управления доступом к информации об изменениях.<br /><br /> NULL = роль не используется.|  
|index_name|**sysname**|Имя индекса, который использовался для уникальной идентификации строк в исходной таблице.|  
|filegroup_name|**sysname**|Имя файловой группы, в которой расположена таблица изменений.<br /><br /> NULL = таблица изменений расположена в файловой группе по умолчанию для базы данных.|  
|create_date|**datetime**|Дата включения экземпляра отслеживания.|  
|index_column_list|**nvarchar(max)**|Список столбцов индекса, который использовался для уникальной идентификации строк в исходной таблице.|  
|captured_column_list|**nvarchar(max)**|Список отслеживаемых исходных столбцов.|  
  
## <a name="remarks"></a>Замечания  
 Если оба *source_schema* и *source_name* по умолчанию значение NULL или значение NULL, явно заданные Эта хранимая процедура возвращает сведения обо всех базы данных экземпляры отслеживания, выделенных вызывающий объект доступ к. Когда *source_schema* и *source_name* имеют значение NULL, возвращаются сведения только об определенной включенной таблице с именем.  
  
## <a name="permissions"></a>Разрешения  
 Когда *source_schema* и *source_name* имеют значение NULL, определяемые авторизацией вызывающего объекта включена, включаемые в результирующем наборе. Чтобы включать сведения о таблице, вызывающие объекты должны иметь разрешение SELECT для всех отслеживаемых столбцов в экземпляре отслеживания, а также входить во все определенные шлюзовые роли. Члены роли db_owner database могут просматривать сведения обо всех определенных экземплярах отслеживания. Когда запрашиваются сведения об определенной активной таблице, к именованной таблице применяются те же требования относительно разрешений SELECT и членства в роли.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-change-data-capture-configuration-information-for-a-specified-table"></a>A. Возвращение сведений о конфигурации системы отслеживания изменений для указанной таблицы  
 В следующем примере возвращается конфигурация системы отслеживания информации об изменениях для таблицы `HumanResources.Employee`.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture   
    @source_schema = N'HumanResources',   
    @source_name = N'Employee';  
GO  
```  
  
### <a name="b-returning-change-data-capture-configuration-information-for-all-tables"></a>Б. Возвращение сведений о конфигурации системы отслеживания изменений для всех таблиц  
 В следующем примере возвращаются данные конфигурации для всех активных таблиц в базе данных, которые содержат информацию об изменениях, доступ к которой может получать вызывающий объект.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture;  
GO  
```  
  
  
