---
title: "@@CONNECTIONS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs: TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: "32"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8422da0d4e550c99fac6c9659f771ab98196cb4a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;СОЕДИНЕНИЯ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Возвращает количество попыток соединения — успешных или неуспешных — с момента запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
@@CONNECTIONS  
```  
  
## <a name="return-types"></a>Возвращаемые типы
**integer**
  
## <a name="remarks"></a>Замечания  
Соединения пользователей бывают разными. Приложения, например, могут открывать несколько соединений с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] незаметно для пользователя.
  
Чтобы отобразить отчет, содержащий ряд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] статистику, включая попытки соединений, запустите **sp_monitor**.
  
@@MAX_CONNECTIONS — максимальное число соединений, разрешенных одновременно на сервер. @@CONNECTIONS увеличивается с попытками входа, поэтому @@CONNECTIONS может быть больше, чем @@MAX_CONNECTIONS .
  
## <a name="examples"></a>Примеры  
Следующий пример возвращает число попыток входа в систему на текущую дату и время.
  
```sql
SELECT GETDATE() AS 'Today''s Date and Time',   
@@CONNECTIONS AS 'Login Attempts';  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
  
Today's Date and Time  Login Attempts  
---------------------- --------------  
12/5/2006 10:32:45 AM  211023         
```  
  
## <a name="see-also"></a>См. также:
[Системные статистические функции &#40;Transact-SQL&#41;#41;](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[sp_monitor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  
