---
title: "sp_helpdistributiondb (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 040970c34e8154538135e355744746e3ee1e3cb6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает свойства указанной базы данных распространителя. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@database=**] **"***имя_базы_данных***"**  
 Имя базы данных, для которой возвращаются свойства. *database_name* — **sysname**, значение по умолчанию  **%**  для всех баз данных, связанным с распространителем, для которых у пользователя есть разрешения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя базы данных распространителя.|  
|**min_distretention**|**int**|Минимальный срок хранения транзакций перед удалением (в часах).|  
|**max_distretention**|**int**|Максимальный срок хранения транзакций перед удалением (в часах).|  
|**срок хранения журнала**|**int**|Количество часов, в течение которых будет храниться журнал.|  
|**history_cleanup_agent**|**sysname**|Имя агента очистки журнала.|  
|**distribution_cleanup_agent**|**sysname**|Имя агента очистки распространителя.|  
|**status**|**int**|Только для внутреннего применения.|  
|**data_folder**|**nvarchar(255)**|Имя каталога, используемого для хранения файлов базы данных.|  
|**data_file**|**nvarchar(255)**|Имя файла базы данных.|  
|**data_file_size**|**int**|Исходный размер файла данных в мегабайтах.|  
|**log_folder**|**nvarchar(255)**|Имя каталога, в котором размещается файл журнала базы данных.|  
|**файл_журнала**|**nvarchar(255)**|Имя файла журнала.|  
|**log_file_size**|**int**|Исходный размер файла журнала в мегабайтах.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_helpdistributiondb** используется во всех типах репликации.  
  
## <a name="permissions"></a>Permissions  
 Члены **db_owner** предопределенной роли базы данных или **replmonitor** роли в базе данных распространителя и пользователи в списке доступа к публикации, публикации, использующей базу данных распространителя могут выполнять процедуру **sp_helpdistributiondb** для возврата сведений, относящихся к файлам. Члены **открытый** могут выполнять процедуру **sp_helpdistributiondb** для возврата сведений не относящиеся к файлу для базы данных распространителя, к которым они имеют доступ.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
