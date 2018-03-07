---
title: "CONNECTIONPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9ab513c11d86ca5d7496ad1fca2ff7527d69bba6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Возвращает сведения о свойствах уникального соединения, по которому получен запрос.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>Аргументы  
*Свойство*  
Свойство соединения. *Свойство* может принимать одно из следующих значений.
  
|Значение|Тип данных|Description|  
|---|---|---|
|net_transport|**nvarchar(40)**|Возвращает описание физического транспортного протокола, используемого данным соединением. Не допускает значение NULL.<br /><br /> Возвращаемые значения: **HTTP**, **именованных каналов**, **сеанса**, **общей памяти**, **SSL**, **TCP**, и **VIA**.<br /><br /> Примечание: Всегда возвращает **сеанса** при соединение имеет несколько активных результирующих наборов (MARS) включен, и пул соединений включен.|  
|protocol_type|**nvarchar(40)**|Возвращает тип протокола передачи полезных данных. В настоящее время различаются протоколы TDS (TSQL) и SOAP. Допускает значение NULL.|  
|auth_scheme|**nvarchar(40)**|Возвращает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схему проверки подлинности для подключения. Схема проверки подлинности предусматривает использование проверки подлинности Windows (NTLM, KERBEROS, DIGEST, BASIC, NEGOTIATE) либо проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значение NULL.|  
|local_net_address|**varchar(48)**|Возвращает IP-адрес сервера, с которым установлено данное соединение. Доступен только для соединений, которые в качестве транспорта данных используют протокол TCP. Допускает значение NULL.|  
|local_tcp_port|**int**|Возвращает TCP-порт сервера, с которым установлено соединение, если для соединения используется протокол TCP. Допускает значение NULL.|  
|client_net_address|**varchar(48)**|Запрашивает адрес клиента, устанавливающего соединение с данным сервером. Допускает значение NULL.|  
|physical_net_transport|**nvarchar(40)**|Возвращает описание физического транспортного протокола, используемого данным соединением. Возвращает точные данные, если для соединения включен режим MARS.|  
|\<Любая другая строка >||Возвращает значение NULL при недопустимости входных данных.|  
  
## <a name="remarks"></a>Замечания  
**local_net_address** и **local_tcp_port** вернуть значение NULL в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
Возвращаемые значения совпадают с параметрами, показанными для соответствующих столбцов в [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) динамическое административное представление. Например:
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>См. также:
[sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
