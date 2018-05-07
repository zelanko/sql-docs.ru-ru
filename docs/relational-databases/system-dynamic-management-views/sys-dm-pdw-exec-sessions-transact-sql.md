---
title: sys.dm_pdw_exec_sessions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/07/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
caps.latest.revision: 8
author: barbkess
ms.author: barbkess
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7fb7963e658c95ad386f95f63a107fc5bb80c72e
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех сеансах в настоящее время или недавно открытые на устройстве. Он содержит одну строку для каждого сеанса.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|Идентификатор текущего запроса или запроса последнего запуска (Если этот сеанс ЗАВЕРШИТСЯ и выполнении запроса во время завершения). Ключ для этого представления.|Уникален во всех сеансах в системе.|  
|status|**nvarchar(10)**|Для текущих сеансов указывает, является ли сеанс в данный момент активным или простоя. Для предыдущих сеансов сеанса, который может отображаться состояние закрытым или уничтоженным (если сеанса было принудительно закрыто).|«АКТИВНО», «ЗАКРЫТО», «ПРОСТОЙ», «ЗАВЕРШЕНО»|  
|request_id|**nvarchar(32)**|Идентификатор текущего запроса или выполнения последнего запроса.|Уникален в пределах всех запросов в системе. Значение NULL, если ни одно выполнено.|  
|security_id|**varbinary(85)**|Идентификатор безопасности участника, для запуска сеанса.||  
|login_name|**nvarchar(128)**|Имя входа участника выполнения сеанса.|Любая строка, соответствующий соглашениям об именах пользователей.|  
|login_time|**datetime**|Дата и время, когда пользователь вошел в систему, и этот сеанс был создан.|Допустимые **datetime** до текущего времени.|  
|query_count|**int**|Получает число запросов/requeststhis сеанса выполнялась с момента создания.|Больше или равно 0.|  
|is_transactional|**бит**|Захватывает ли сеанс в данный момент находится в транзакции или нет.|0 для автоматической фиксации, 1 для транзакций.|  
|client_id|**nvarchar(255)**|Записывает сведения о клиенте для сеанса.|Любая допустимая строка.|  
|APP_NAME|**nvarchar(255)**|Записывает сведения об имени приложения, при необходимости установить как часть процесса соединения.|Любая допустимая строка.|  
|sql_spid|**int**|Идентификатор SPID. Используйте `session_id` этого сеанса. Используйте `sql_spid` столбца для присоединения к **sys.dm_pdw_nodes_exec_sessions**.<br /><br /> **\*\* Предупреждение \* \***  этот столбец содержит закрытых SPID.||  
  
 Сведения о максимальное число строк, сохраняемых в этом представлении, обратитесь к разделу максимальные значения представление системы в [минимальное и максимальное значения (SQL Server PDW)](http://msdn.microsoft.com/en-us/5243f018-2713-45e3-9b61-39b2a57401b9) раздела.  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и параллельные хранилища данных динамических административных представлений &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
