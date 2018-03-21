---
title: "sys.Servers (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: cc6dcb18c9961bffcf65db5f918ad54f19ca78ae
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого зарегистрированного связанного или удаленного сервера и строку для локального сервера, с **server_id** = 0.  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Локальный идентификатор связанного сервера.|  
|**name**|**sysname**|Когда **server_id** = 0, это имя сервера.<br /><br /> Когда **server_id** > 0, это локальное имя связанного сервера.|  
|**product**|**sysname**|Имя продукта связанного сервера. «SQL Server» указывает, что это другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**provider**|**sysname**|Имя поставщика OLE DB для соединения со связанным сервером.|  
|**data_source**|**nvarchar(4000)**|Свойство соединения источника данных OLE DB.|  
|**расположение**|**nvarchar(4000)**|Свойство соединения местоположения OLE DB. NULL — если нет.|  
|**provider_string**|**nvarchar(4000)**|Свойство соединения строки поставщика OLE DB.<br /><br /> Имеет значение NULL, если только вызывающий не обладает разрешением ALTER ANY LINKED SERVER.|  
|**catalog**|**sysname**|Свойство соединения каталога OLE DB. NULL — если нет.|  
|**connect_timeout**|**int**|Время ожидания соединения в секундах; 0 — не указано.|  
|**query_timeout**|**int**|Время ожидания запроса в секундах; 0 — не указано.|  
|**is_linked**|**бит**|0 = является сервером старого стиля, добавленные с помощью **sp_addserver**, с помощью различных RPC и распределенных транзакций поведения.<br /><br /> 1 = стандартный связанный сервер.|  
|**is_remote_login_enabled**|**бит**|Параметр RPC установлен на включение входящих удаленных имен входа для этого сервера.|  
|**is_rpc_out_enabled**|**бит**|Исходящие (от этого сервера) RPC включены.|  
|**is_data_access_enabled**|**бит**|Сервер включен для распределенных запросов.|  
|**is_collation_compatible**|**бит**|Параметры сортировки удаленных данных рассматриваются как совместимые с локальными данными, если нет доступных сведений о параметрах сортировки.|  
|**uses_remote_collation**|**бит**|При значении 1 используйте параметры сортировки, переданные удаленным сервером; в ином случае используйте параметры сортировки, указанные следующим столбцом.|  
|**collation_name**|**sysname**|Имя параметров сортировки, которые должны быть использованы, или NULL, если следует использовать локальные параметры сортировки.|  
|**lazy_schema_validation**|**бит**|При значении 1 проверка правильности схемы при запуске запроса не производится.|  
|**is_system**|**бит**|Доступ на этот сервер может получить только внутренняя система.|  
|**is_publisher**|**бит**|Сервер является издателем репликации.|  
|**is_subscriber**|**бит**|Сервер является подписчиком репликации.|  
|**is_distributor**|**бит**|Сервер является распространителем репликации.|  
|**is_nonsql_subscriber**|**бит**|Сервер является подписчиком репликации, отличным от SQL Server.|  
|**is_remote_proc_transaction_promotion_enabled**|**бит**|Если 1, вызов удаленной хранимой процедуры приводит к запуску распределенной транзакции и привлекает к выполнению транзакции MS DTC. Дополнительные сведения см. в статье [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md).|  
|**modify_date**|**datetime**|Дата последнего изменения сведений о сервере.|  
  
## <a name="permissions"></a>Разрешения  
 Значение в **provider_string** всегда имеет значение NULL, если только вызывающий не обладает разрешением ALTER ANY LINKED SERVER.  
  
 Разрешения не требуются для просмотра локального сервера (**server_id** = 0).  
  
 При создании связанного или удаленного сервера, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает имя входа, сопоставленное для **открытый** роли сервера. Это означает, что все имена входа по умолчанию дают возможность просматривать связанные и удаленные сервера. Чтобы ограничить видимость этих серверов, удалите сопоставление имени входа по умолчанию, выполнив [sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) и указав значение NULL для *locallogin* параметра.  
  
 Если сопоставление удалено, только те пользователи, которые добавлены явно со связанным или удаленным именем входа, могут просматривать связанные или удаленные сервера соответственно. Для просмотра связанных и удаленных серверов после удаления сопоставления имен входа по умолчанию необходимы следующие разрешения.  
  
-   ALTER ANY LINKED SERVER или ALTER ANY LOGIN ON SERVER.  
  
-   Членство в **setupadmin** или **sysadmin** предопределенных ролей сервера  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
