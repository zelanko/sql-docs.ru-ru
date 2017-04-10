---
title: "Создание триггеров DML для обработки нескольких строк данных | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-dml"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "многострочные триггеры DML"
  - "инструкция UPDATE [SQL Server], триггеры DML"
  - "инструкция DELETE [SQL Server], триггеры DML"
  - "многострочные триггеры DML [SQL Server]"
  - "инструкция INSERT [SQL Server], триггеры DML"
  - "триггеры DML, многострочные"
ms.assetid: d476c124-596b-4b27-a883-812b6b50a735
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Создание триггеров DML для обработки нескольких строк данных
  При написании кода для триггера DML следует учитывать, что инициирующая триггер отдельная инструкция может влиять на несколько строк, а не на одну строку данных. Такой режим работы является стандартным для триггеров UPDATE и DELETE, поскольку эти инструкции зачастую касаются нескольких строк, и в меньшей степени распространен для триггеров INSERT, поскольку базовая инструкция INSERT добавляет только одну строку. Тем не менее, так как допускается запуск триггера инструкцией INSERT INTO (*table_name*) SELECT, вставка множества строк может привести к вызову одного триггера.  
  
 Учет особенностей работы с несколькими строками особенно важен в случаях, когда функция триггера DML автоматически пересчитывает сводные значения из одной таблицы и помещает результаты в другую таблицу для временных итогов.  
  
> [!NOTE]  
>  Не рекомендуется использовать курсоры в триггерах, поскольку они потенциально могут приводить к снижению производительности. Чтобы создать триггер, влияющий на несколько строк, вместо курсоров следует использовать логику, основанную на наборах строк.  
  
## Примеры  
 Триггеры DML в нижеприведенных примерах предназначены для хранения промежуточных итогов по столбцу в другой таблице образца базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
### A. Сохранение промежуточных итогов при вставке одной строки  
 Первая версия триггера DML подходит для вставки одной строки данных, которая загружается в таблицу `PurchaseOrderDetail`. Инструкция INSERT активирует триггер DML, и новая строка добавляется в таблицу **inserted** на время выполнения триггера. Инструкция `UPDATE` считывает значение столбца `LineTotal` по строке и добавляет его к текущему значению в столбце `SubTotal` таблицы `PurchaseOrderHeader` . Предложение `WHERE` служит для проверки того, что обновленная строка в таблице `PurchaseOrderDetail` соответствует столбцу `PurchaseOrderID` строки в таблице **inserted** .  
  
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
  
### Б. Сохранение промежуточных итогов при вставке нескольких строк или одной строки  
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
  
 Этот триггер также правильно выполняется при вставке одной строки, при этом сумма столбца значений `LineTotal` является суммой одной строки. Однако при работе с этим триггером требуется дополнительная обработка средствами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] коррелированного вложенного запроса и оператора `IN`, используемого в предложении `WHERE`. Это необязательно для вставки одной строки.  
  
### В. Сохранение промежуточных итогов в зависимости типа вставки  
 В триггер можно вносить изменения для подбора способа, оптимального при работе с несколькими строками. Например, в логике триггера можно использовать функцию `@@ROWCOUNT`, чтобы различать вставку одной и нескольких строк.  
  
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
  
## См. также:  
 [Триггеры DML](../../relational-databases/triggers/dml-triggers.md)  
  
  