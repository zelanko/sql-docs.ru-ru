---
title: '@@CONNECTIONS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@CONNECTIONS'
- '@@CONNECTIONS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CONNECTIONS function'
- connections [SQL Server], number of
- connections [SQL Server], attempted
- number of connection attempts
- attempted connections
ms.assetid: c59836a8-443c-4b9a-8b96-8863ada97ac7
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 39767751186028fd5cd8b93621d7465094d99264
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNECTIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Эта функция возвращает число попыток подключения (успешных или неуспешных) с момента последнего запуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
@@CONNECTIONS  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных
**integer**
  
## <a name="remarks"></a>Remarks  
Соединения пользователей бывают разными. Приложение, например, может открывать несколько подключений с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] незаметно для пользователя.
  
Чтобы отобразить отчет, содержащий ряд статистических данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая попытки соединения, выполните процедуру **sp_monitor**.
  
@@MAX_CONNECTIONS — это максимальное допустимое число параллельных соединений с сервером. Значение @@CONNECTIONS увеличивается при каждой попытке входа в систему, поэтому значение @@CONNECTIONS может превышать значение @@MAX_CONNECTIONS.
  
## <a name="examples"></a>Примеры  
Этот пример возвращает данные о попытках входа в систему для текущего времени и даты.
  
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
  
## <a name="see-also"></a>См. также раздел
[Системные статистические функции (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
[sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)
  
  
