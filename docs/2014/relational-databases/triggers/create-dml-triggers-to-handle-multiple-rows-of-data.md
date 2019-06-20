---
title: Создание триггеров DML для обработки нескольких строк данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- multiple row DML triggers
- UPDATE statement [SQL Server], DML triggers
- DELETE statement [SQL Server], DML triggers
- multirow DML triggers [SQL Server]
- INSERT statement [SQL Server], DML triggers
- DML triggers, multirow
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d960ae015bb2e52daa183e1f55d6ff119f234b18
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62676461"
---
# <a name="create-dml-triggers-to-handle-multiple-rows-of-data"></a>Создание триггеров DML для обработки нескольких строк данных
  При написании кода для триггера DML следует учитывать, что инициирующая триггер отдельная инструкция может влиять на несколько строк, а не на одну строку данных. Такой режим работы является стандартным для триггеров UPDATE и DELETE, поскольку эти инструкции зачастую касаются нескольких строк, и в меньшей степени распространен для триггеров INSERT, поскольку базовая инструкция INSERT добавляет только одну строку. Тем не менее, так как допускается запуск триггера инструкцией INSERT INTO (*table_name*) SELECT, вставка множества строк может привести к вызову одного триггера.  
  
 Учет особенностей работы с несколькими строками особенно важен в случаях, когда функция триггера DML автоматически пересчитывает сводные значения из одной таблицы и помещает результаты в другую таблицу для временных итогов.  
  
> [!NOTE]  
>  Не рекомендуется использовать курсоры в триггерах, поскольку они потенциально могут приводить к снижению производительности. Чтобы создать триггер, влияющий на несколько строк, вместо курсоров следует использовать логику, основанную на наборах строк.  
  
## <a name="examples"></a>Примеры  
 Триггеры DML в нижеприведенных примерах предназначены для хранения промежуточных итогов по столбцу в другой таблице образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
### <a name="a-storing-a-running-total-for-a-single-row-insert"></a>A. Сохранение промежуточных итогов при вставке одной строки  
 Первая версия триггера DML подходит для вставки одной строки данных, которая загружается в таблицу `PurchaseOrderDetail` . Инструкция INSERT активирует триггер DML, и новая строка добавляется в таблицу **inserted** на время выполнения триггера. Инструкция `UPDATE` считывает значение столбца `LineTotal` по строке и добавляет его к текущему значению в столбце `SubTotal` таблицы `PurchaseOrderHeader` . Предложение `WHERE` служит для проверки того, что обновленная строка в таблице `PurchaseOrderDetail` соответствует столбцу `PurchaseOrderID` строки в таблице **inserted** .  
  
```  
-- Trigger is valid for single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID ;  
```  
  
### <a name="b-storing-a-running-total-for-a-multirow-or-single-row-insert"></a>Б. Сохранение промежуточных итогов при вставке нескольких строк или одной строки  
 При вставке нескольких строк триггер DML в примере A может завершаться ошибкой; выражение справа от выражения присваивания в инструкции UPDATE (`SubTotal` + `LineTotal`) может быть только одним значением, а не списком значений. Следовательно, триггер должен извлечь значение из любой отдельной строки таблицы **inserted** и добавить его к текущему значению `SubTotal` таблицы `PurchaseOrderHeader` для конкретного значения `PurchaseOrderID` . Эта операция может не иметь ожидаемого эффекта, если отдельное значение `PurchaseOrderID` встречается несколько раз в таблице **inserted** .  
  
 Для правильного обновления таблицы `PurchaseOrderHeader` триггер должен поддерживать работу с несколькими строками в таблице **inserted** . Этого можно добиться с помощью функции `SUM` , которая вычисляет итог `LineTotal` по группе строк таблицы **inserted** для каждого значения `PurchaseOrderID`. Функция `SUM` включена в коррелированный вложенный запрос (инструкцию `SELECT` в круглых скобках). Этот вложенный запрос возвращает одно значение для каждого значения `PurchaseOrderID` таблицы **inserted** , которое соответствует или коррелирует со значением `PurchaseOrderID` таблицы `PurchaseOrderHeader` .  
  
```  
-- Trigger is valid for multirow and single-row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail2  
ON Purchasing.PurchaseOrderDetail  
AFTER INSERT AS  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted);  
```  
  
 Этот триггер также правильно выполняется при вставке одной строки, при этом сумма столбца значений `LineTotal` является суммой одной строки. Однако при работе с этим триггером требуется дополнительная обработка средствами `IN` коррелированного вложенного запроса и оператора `WHERE` , используемого в предложении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это необязательно для вставки одной строки.  
  
### <a name="c-storing-a-running-total-based-on-the-type-of-insert"></a>В. Сохранение промежуточных итогов в зависимости типа вставки  
 В триггер можно вносить изменения для подбора способа, оптимального при работе с несколькими строками. Например, в логике триггера можно использовать функцию `@@ROWCOUNT` , чтобы различать вставку одной и нескольких строк.  
  
```  
-- Trigger valid for multirow and single row inserts  
-- and optimal for single row inserts.  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER NewPODetail3  
ON Purchasing.PurchaseOrderDetail  
FOR INSERT AS  
IF @@ROWCOUNT = 1  
BEGIN  
   UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal + LineTotal  
   FROM inserted  
   WHERE PurchaseOrderHeader.PurchaseOrderID = inserted.PurchaseOrderID  
END  
ELSE  
BEGIN  
      UPDATE Purchasing.PurchaseOrderHeader  
   SET SubTotal = SubTotal +   
      (SELECT SUM(LineTotal)  
      FROM inserted  
      WHERE PurchaseOrderHeader.PurchaseOrderID  
       = inserted.PurchaseOrderID)  
   WHERE PurchaseOrderHeader.PurchaseOrderID IN  
      (SELECT PurchaseOrderID FROM inserted)  
END;  
```  
  
## <a name="see-also"></a>См. также  
 [Триггеры DML](dml-triggers.md)  
  
  
