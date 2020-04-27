---
title: sys. sp_cdc_help_change_data_capture (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: fdf0086fe3a87823a419f3535888ea3211ee9ef1
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67905175"
---
# <a name="syssp_cdc_help_change_data_capture-transact-sql"></a>sys.sp_cdc_help_change_data_capture (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает конфигурацию системы отслеживания измененных данных для каждой таблицы, включенной для системы отслеживания измененных данных в текущей базе данных. Для каждой исходной таблицы может возвращаться до двух строк — по одной строке для каждого экземпляра отслеживания. Система отслеживания измененных данных доступна не во всех выпусках [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], поддерживаемых различными выпусками, см. [в разделе функции, поддерживаемые различными выпусками SQL Server 2016](../../sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_help_change_data_capture   
  [ [ @source_schema = ] 'source_schema' ]  
  [, [ @source_name = ] 'source_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_schema = ] "*source_schema*"  
 Имя схемы, к которой относится исходная таблица. Аргумент *source_schema* имеет тип **sysname**и значение по умолчанию NULL. Если указан *source_schema* , необходимо также указать *source_name* .  
  
 Если значение не равно NULL, *source_schema* должен существовать в текущей базе данных.  
  
 Если *source_schema* не равно null, *source_name* также должен иметь значение, отличное от NULL.  
  
 [ @source_name = ] "*source_name*"  
 Имя исходной таблицы. Аргумент *source_name* имеет тип **sysname**и значение по умолчанию NULL. Если указан *source_name* , необходимо также указать *source_schema* .  
  
 Если значение не равно NULL, *source_name* должен существовать в текущей базе данных.  
  
 Если *source_name* не равно null, *source_schema* также должен иметь значение, отличное от NULL.  
  
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
|supports_net_changes|**bit**|Включена поддержка отслеживания сетевых изменений.|  
|has_drop_pending|**bit**|Не используется в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].|  
|имя_роли|**sysname**|Имя роли базы данных, которая использовалась для управления доступом к информации об изменениях.<br /><br /> NULL = роль не используется.|  
|index_name|**sysname**|Имя индекса, который использовался для уникальной идентификации строк в исходной таблице.|  
|filegroup_name|**sysname**|Имя файловой группы, в которой расположена таблица изменений.<br /><br /> NULL = таблица изменений расположена в файловой группе по умолчанию для базы данных.|  
|create_date|**datetime**|Дата включения экземпляра отслеживания.|  
|index_column_list|**nvarchar(max)**|Список столбцов индекса, который использовался для уникальной идентификации строк в исходной таблице.|  
|captured_column_list|**nvarchar(max)**|Список отслеживаемых исходных столбцов.|  
  
## <a name="remarks"></a>Remarks  
 Если оба *source_schema* и *source_name* по умолчанию имеют значение null или явно задают значение null, эта хранимая процедура возвращает сведения обо всех экземплярах отслеживания базы данных, к которым вызывающий объект имеет доступ. Если *source_schema* и *SOURCE_NAME* не равны NULL, возвращаются только сведения о конкретной именованной таблице с поддержкой.  
  
## <a name="permissions"></a>Разрешения  
 Если *source_schema* и *source_name* имеют значение null, авторизация вызывающего объекта определяет, какие включенные таблицы включены в результирующий набор. Чтобы включать сведения о таблице, вызывающие объекты должны иметь разрешение SELECT для всех отслеживаемых столбцов в экземпляре отслеживания, а также входить во все определенные шлюзовые роли. Члены роли db_owner database могут просматривать сведения обо всех определенных экземплярах отслеживания. Когда запрашиваются сведения об определенной активной таблице, к именованной таблице применяются те же требования относительно разрешений SELECT и членства в роли.  
  
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
  
### <a name="b-returning-change-data-capture-configuration-information-for-all-tables"></a>Б) Возвращение сведений о конфигурации системы отслеживания изменений для всех таблиц  
 В следующем примере возвращаются данные конфигурации для всех активных таблиц в базе данных, которые содержат информацию об изменениях, доступ к которой может получать вызывающий объект.  
  
```  
USE AdventureWorks2012;  
GO  
EXECUTE sys.sp_cdc_help_change_data_capture;  
GO  
```  
  
  
