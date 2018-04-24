---
title: '@@LOCK_TIMEOUT (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/19/2017
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
- '@@LOCK_TIMEOUT'
- '@@LOCK_TIMEOUT_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- timeout options [SQL Server], locks
- '@@LOCK_TIMEOUT function'
- current lock time-out setting
- locking [SQL Server], time-outs
ms.assetid: 6bf8bf97-60b8-40c1-b89d-8f5a00bcae2e
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 4bcd7703d4e03a6b41320d3b539bb7cade1907b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="x40x40locktimeout-transact-sql"></a>&#x40;&#x40;LOCK_TIMEOUT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает значение времени ожидания блокировки в миллисекундах для текущего сеанса.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@LOCK_TIMEOUT  
```  
  
## <a name="return-types"></a>Типы возвращаемых данных  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 Инструкция SET LOCK_TIMEOUT позволяет установить в приложении максимальное время ожидания заблокированного ресурса. Если ожидание длится дольше значения LOCK_TIMEOUT, инструкция автоматически отменяется, а приложению возвращается сообщение об ошибке.  
  
 Функция @@LOCK_TIMEOUT возвращает значение –1 в случае, если в текущем сеансе этот параметр еще не был задан с помощью вызова SET LOCK_TIMEOUT.  
  
## <a name="examples"></a>Примеры  
 Данный пример иллюстрирует содержимое результирующего набора в случае не установленного заранее значения LOCK_TIMEOUT.  
  
```  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Результирующий набор:  
  
```  
Lock Timeout  
------------  
-1  
```  
  
 В приведенном ниже примере значение LOCK_TIMEOUT устанавливается равным 1800 миллисекундам, после чего вызывается функция @@LOCK_TIMEOUT.  
  
```  
SET LOCK_TIMEOUT 1800;  
SELECT @@LOCK_TIMEOUT AS [Lock Timeout];  
GO  
```  
  
 Результирующий набор:  
  
```  
Lock Timeout  
------------  
1800          
```  
  
## <a name="see-also"></a>См. также:  
 [Функции настройки (Transact-SQL)](../../t-sql/functions/configuration-functions-transact-sql.md)   
 [SET LOCK_TIMEOUT (Transact-SQL)](../../t-sql/statements/set-lock-timeout-transact-sql.md)  
  
  
