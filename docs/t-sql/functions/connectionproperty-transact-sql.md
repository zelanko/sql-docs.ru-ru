---
title: CONNECTIONPROPERTY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
caps.latest.revision: 25
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 95c95ad472c5b5d4cb5420fa3b0da8f88053c0c5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
*property*  
Свойство соединения. Аргумент *property* может иметь одно из перечисленных ниже значений.
  
|Значение|Тип данных|Description|  
|---|---|---|
|net_transport|**nvarchar(40)**|Возвращает описание физического транспортного протокола, используемого данным соединением. Не допускает значение NULL.<br /><br /> Возвращаемые значения: **HTTP**, **Named pipe**, **Session**, **Shared memory**, **SSL**, **TCP** и **VIA**.<br /><br /> Примечание. Всегда возвращает значение **Session**, если в соединении включен режим "множественный активный результирующий набор" (MARS), а также включено использование пулов соединений.|  
|protocol_type|**nvarchar(40)**|Возвращает тип протокола передачи полезных данных. В настоящее время различаются протоколы TDS (TSQL) и SOAP. Допускает значение NULL.|  
|auth_scheme|**nvarchar(40)**|Возвращает схему проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для соединения. Схема проверки подлинности предусматривает использование проверки подлинности Windows (NTLM, KERBEROS, DIGEST, BASIC, NEGOTIATE) либо проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Не допускает значение NULL.|  
|local_net_address|**varchar(48)**|Возвращает IP-адрес сервера, с которым установлено данное соединение. Доступен только для соединений, которые в качестве транспорта данных используют протокол TCP. Допускает значение NULL.|  
|local_tcp_port|**int**|Возвращает TCP-порт сервера, с которым установлено соединение, если для соединения используется протокол TCP. Допускает значение NULL.|  
|client_net_address|**varchar(48)**|Запрашивает адрес клиента, устанавливающего соединение с данным сервером. Допускает значение NULL.|  
|physical_net_transport|**nvarchar(40)**|Возвращает описание физического транспортного протокола, используемого данным соединением. Возвращает точные данные, если для соединения включен режим MARS.|  
|\<любая другая строка>||Возвращает значение NULL при недопустимости входных данных.|  
  
## <a name="remarks"></a>Remarks  
**local_net_address** и **local_tcp_port** возвращают значение NULL в [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].
  
Возвращаемые значения совпадают с параметрами, показанными для соответствующих столбцов в динамическом административном представлении [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md). Пример:
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>См. также раздел
[sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
