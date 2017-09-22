---
title: "@@FETCH_STATUS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c6ea46c5187f00190cb39ba9a502b3ecb6a28bc6
ms.openlocfilehash: 61e209f7cf2a3a654b33979129e9500d3734fe64
ms.contentlocale: ru-ru
ms.lasthandoff: 09/19/2017

---
# <a name="x40x40fetchstatus-transact-sql"></a>& #x 40; & #x 40; FETCH_STATUS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

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
|-9|Курсор не выполняет операции выборки.|  
  
## <a name="remarks"></a>Замечания  
 Поскольку @@FETCH_STATUS является глобальной для всех курсоров в соединении, используйте @@FETCH_STATUS внимательно. После выполнения инструкции FETCH следует произвести тест для @@FETCH_STATUS прежде, чем любая другая инструкция FETCH выполняется в отношении другого курсора. Значение @@FETCH_STATUS до любой выборки произошли на соединение.  
  
 Например, пользователь выполняет инструкцию FETCH из одного курсора, а затем вызывает хранимую процедуру, которая открывает и обрабатывает результаты из другого курсора. Когда управление возвращается от вызванной хранимой процедуры, @@FETCH_STATUS отражает последней ВЫБОРКИ, выполненной в хранимой процедуре, а не инструкции FETCH, выполненной прежде, чем была вызвана хранимая процедура.  
  
 Чтобы получить состояние последней выборки конкретного курсора, запросите **fetch_status** столбец **sys.dm_exec_cursors** функции динамического управления.  
  
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
 [FETCH &#40; Transact-SQL &#41;](../../t-sql/language-elements/fetch-transact-sql.md)  
  
  

