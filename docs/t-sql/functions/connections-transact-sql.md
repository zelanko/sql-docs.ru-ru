---
title: '@@CONNECTIONS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 26da6bd0224941773c91dda8703015e4200f5552
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882004"
---
# <a name="x40x40connections-transact-sql"></a>&#x40;&#x40;CONNECTIONS (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
  
Чтобы отобразить отчет, содержащий ряд статистических данных **, включая попытки соединения, выполните процедуру** sp_monitor[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
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
  
  
