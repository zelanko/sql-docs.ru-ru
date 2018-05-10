---
title: '@@FETCH_STATUS (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: t-sql|functions
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- '@@FETCH_STATUS'
- '@@FETCH_STATUS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- FETCH statement
- status information [SQL Server], FETCH
- '@@FETCH_STATUS function'
ms.assetid: 93659193-e4ff-4dfb-9043-0c4114921b91
caps.latest.revision: 39
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 46b6c72283ab0ead6aad871f3801fb3ed967f8f4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="x40x40fetchstatus-transact-sql"></a>&#x40;&#x40;FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает состояние последней инструкции FETCH, вызванной в любом курсоре, открытом в данном соединении.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
@@FETCH_STATUS  
```  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 **integer**  
  
## <a name="return-value"></a>Возвращаемое значение  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|Инструкция FETCH была выполнена успешно.|  
|-1|Выполнение инструкции FETCH завершилось неудачно или строка оказалась вне пределов результирующего набора.|  
|-2|Выбранная строка отсутствует.|
|–9|Курсор не выполняет операцию выборки.|  
  
## <a name="remarks"></a>Remarks  
 Поскольку @@FETCH_STATUS является глобальным для всех курсоров в соединении, используйте @@FETCH_STATUS тщательно. После выполнения инструкции FETCH следует произвести тест с помощью функции @@FETCH_STATUS, прежде чем любая другая инструкция FETCH будет выполнена применительно к другому курсору. Значение функции @@FETCH_STATUS не определено до проведения какой-либо выборки в подключении.  
  
 Например, пользователь выполняет инструкцию FETCH из одного курсора, а затем вызывает хранимую процедуру, которая открывает и обрабатывает результаты из другого курсора. Когда управление возвращается от вызванной хранимой процедуры, функция @@FETCH_STATUS отражает результаты последней инструкции FETCH, выполненной в хранимой процедуре, а не результаты инструкции FETCH, выполненной прежде, чем была вызвана хранимая процедура.  
  
 Чтобы получить состояние последней выборки конкретного курсора, запросите столбец **fetch_status** функции динамического управления **sys.dm_exec_cursors**.  
  
## <a name="examples"></a>Примеры  
 В следующем примере используется переменная `@@FETCH_STATUS` для управления действиями курсора в цикле `WHILE`.  
  
```  
DECLARE Employee_Cursor CURSOR FOR  
SELECT BusinessEntityID, JobTitle  
FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Функции работы с курсорами (Transact-SQL)](../../t-sql/functions/cursor-functions-transact-sql.md)   
 [FETCH (Transact-SQL)](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  
