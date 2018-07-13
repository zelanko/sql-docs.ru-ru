---
title: Создание вложенных триггеров | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- DML triggers, nested
- triggers [SQL Server], nested
- direct recursion [SQL Server]
- triggers [SQL Server], recursive
- DML triggers, recursive
- RECURSIVE_TRIGGERS option
- indirect recursion [SQL Server]
- nested DML triggers
ms.assetid: cd522dda-b4ab-41b8-82b0-02445bdba7af
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 5c063df615f5023c71cbff8700cfddb67aa60b57
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37420763"
---
# <a name="create-nested-triggers"></a>Создание вложенных триггеров
  При выполнении триггером действия, инициирующего другой триггер, триггеры DML и DDL становятся вложенными. Эти действия могут инициировать другие триггеры и т.д. Вложенность триггеров DML и DDL может составлять до 32 уровней. Можно разрешать или запрещать вложенность триггеров AFTER с помощью параметра конфигурации сервера **nested triggers** . Вложенность триггеров INSTEAD OF (только триггеры DML могут быть триггерами INSTEAD OF) не зависит от этого параметра.  
  
> [!NOTE]  
>  Любая ссылка на управляемый код из триггера [!INCLUDE[tsql](../../includes/tsql-md.md)] считается одним уровнем (предел вложенности равен 32 уровням). Методы, вызываемые из управляемого кода, под это ограничение не подпадают.  
  
 Если вложенные триггеры разрешены и триггер в цепочке начинает бесконечный цикл, это превышает предел уровней вложенности и триггер завершается.  
  
 Можно использовать вложенные триггеры для выполнения полезных функций по обслуживанию, например для сохранения резервной копии строк, затронутых предыдущим триггером. Например, можно создать триггер для таблицы `PurchaseOrderDetail` , который будет сохранять резервную копию строк `PurchaseOrderDetail` , удаленных триггером `delcascadetrig` . Если действует триггер `delcascadetrig` , удаление `PurchaseOrderID` 1965 из таблицы `PurchaseOrderHeader` также повлечет удаление соответствующей строки или строк из таблицы `PurchaseOrderDetail`. Чтобы сохранить данные, можно создать триггер DELETE для таблицы `PurchaseOrderDetail` , который запишет удаленные данные в другую, отдельно созданную таблицу `del_save`. Например:  
  
```  
CREATE TRIGGER Purchasing.savedel  
   ON Purchasing.PurchaseOrderDetail  
FOR DELETE  
AS  
   INSERT del_save;  
   SELECT * FROM deleted;  
```  
  
 Не рекомендуется использовать вложенные триггеры в последовательностях, зависящих от порядка следования. Используйте отдельные триггеры для каскадной модификации данных.  
  
> [!NOTE]  
>  Так как триггеры исполняются в пределах транзакции, сбой на любом уровне набора вложенных триггеров приведет к отмене всей транзакции, а также будет выполнен откат всех изменений данных. Включите инструкции PRINT в триггеры, чтобы определить, где происходит сбой.  
  
## <a name="recursive-triggers"></a>Рекурсивные триггеры  
 Триггер AFTER не вызывает самого себя рекурсивно, если только не установлен параметр базы данных RECURSIVE_TRIGGERS.  
  
 Существует два типа рекурсии.  
  
-   Прямая рекурсия  
  
     Такая рекурсия происходит, когда триггер срабатывает и выполняет действие, вызывающее повторное срабатывание того же триггера. Например, приложение обновляет таблицу **T3**; это вызывает срабатывание триггера **Trig3** . Триггер**Trig3** снова обновляет таблицу **T3** , при этом триггер **Trig3** срабатывает еще раз.  
  
     Прямая рекурсия может также возникать, когда повторно вызывается тот же триггер, но лишь после того, как вызван триггер другого типа (AFTER или INSTEAD OF). Другими словами, прямая рекурсия триггера INSTEAD OF может возникать, когда один и тот же триггер INSTEAD OF вызывается второй раз, даже если между двумя его вызовами вызывается один или несколько триггеров AFTER. Аналогичным образом прямая рекурсия триггера AFTER может возникать, когда один и тот же триггер AFTER вызывается второй раз, даже если между двумя его вызовами вызывается один или несколько триггеров INSTEAD OF. Например, пусть приложение использует таблицу **T4**. Данное обновление приводит к срабатыванию триггера **Trig4** типа INSTEAD OF. **Trig4** обновляет таблицу **T5**. Данное обновление приводит к срабатыванию триггера **Trig5** типа AFTER. **Trig5** обновляет таблицу **T4**, и это обновление приводит к повторному срабатыванию триггера **Trig4** типа INSTEAD OF. Данная цепь событий считается прямой рекурсией триггера **Trig4**.  
  
-   Косвенная рекурсия  
  
     Косвенная рекурсия возникает, когда триггер срабатывает и выполняет действие, которое вызывает срабатывание другого триггера того же типа (AFTER или INSTEAD OF). Второй триггер выполняет действие, вызывающее повторное срабатывание исходного триггера. Другими словами, косвенная рекурсия может возникать, когда триггер INSTEAD OF вызывается второй раз, но лишь после того, как между этими двумя вызовами вызывается другой триггер того же типа INSTEAD OF. Аналогичным образом косвенная рекурсия может возникать, когда триггер AFTER вызывается второй раз, но лишь после того, как между этими двумя вызовами вызывается другой триггер того же типа AFTER. Например, пусть приложение использует таблицу **T1**. Данное обновление приводит к срабатыванию триггера **Trig1** типа AFTER. Триггер**Trig1** обновляет таблицу **T2**; при этом обновлении срабатывает триггер **Trig2** типа AFTER. Триггер**Trig2** , в свою очередь, обновляет таблицу **T1** , что приводит к повторному срабатыванию триггера **Trig1** типа AFTER.  
  
 Когда для параметра базы данных RECURSIVE_TRIGGERS устанавливается значение OFF, предотвращается только прямая рекурсия триггеров AFTER. Чтобы отключить косвенную рекурсию триггеров AFTER, присвойте параметру сервера **nested triggers** значение **0**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует использование рекурсивных триггеров для разрешения ссылающейся на себя связи (также называемой транзитивным закрытием). Например, таблица `emp_mgr` определяет:  
  
-   сотрудника (`emp`) компании;  
  
-   менеджера каждого сотрудника (`mgr`);  
  
-   общее число сотрудников в организационном дереве, отправляющих отчеты каждому сотруднику (`NoOfReports`).  
  
 Рекурсивный триггер UPDATE можно использовать для поддержания столбца `NoOfReports` в актуальном состоянии при добавлении новых записей сотрудников. Триггер INSERT обновляет столбец `NoOfReports` записи менеджера, что приводит к рекурсивному обновлению столбца `NoOfReports` других записей, находящихся выше по иерархии менеджмента.  
  
```  
USE AdventureWorks2012;  
GO  
-- Turn recursive triggers ON in the database.  
ALTER DATABASE AdventureWorks2012  
   SET RECURSIVE_TRIGGERS ON;  
GO  
CREATE TABLE dbo.emp_mgr (  
   emp char(30) PRIMARY KEY,  
    mgr char(30) NULL FOREIGN KEY REFERENCES emp_mgr(emp),  
    NoOfReports int DEFAULT 0  
);  
GO  
CREATE TRIGGER dbo.emp_mgrins ON dbo.emp_mgr  
FOR INSERT  
AS  
DECLARE @e char(30), @m char(30);  
DECLARE c1 CURSOR FOR  
   SELECT emp_mgr.emp  
   FROM   emp_mgr, inserted  
   WHERE emp_mgr.emp = inserted.mgr;  
  
OPEN c1;  
FETCH NEXT FROM c1 INTO @e;  
WHILE @@fetch_status = 0  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Add 1 for newly  
   WHERE emp_mgr.emp = @e ;                           -- added employee.  
  
   FETCH NEXT FROM c1 INTO @e;  
END  
CLOSE c1;  
DEALLOCATE c1;  
GO  
-- This recursive UPDATE trigger works assuming:  
--   1. Only singleton updates on emp_mgr.  
--   2. No inserts in the middle of the org tree.  
CREATE TRIGGER dbo.emp_mgrupd ON dbo.emp_mgr FOR UPDATE  
AS  
IF UPDATE (mgr)  
BEGIN  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports + 1 -- Increment mgr's  
   FROM inserted                            -- (no. of reports) by  
   WHERE emp_mgr.emp = inserted.mgr;         -- 1 for the new report.  
  
   UPDATE dbo.emp_mgr  
   SET emp_mgr.NoOfReports = emp_mgr.NoOfReports - 1 -- Decrement mgr's  
   FROM deleted                             -- (no. of reports) by 1  
   WHERE emp_mgr.emp = deleted.mgr;          -- for the new report.  
END  
GO  
-- Insert some test data rows.  
INSERT dbo.emp_mgr(emp, mgr) VALUES  
    ('Harry', NULL)  
    ,('Alice', 'Harry')  
    ,('Paul', 'Alice')  
    ,('Joe', 'Alice')  
    ,('Dave', 'Joe');  
GO  
SELECT emp,mgr,NoOfReports  
FROM dbo.emp_mgr;  
GO  
-- Change Dave's manager from Joe to Harry  
UPDATE dbo.emp_mgr SET mgr = 'Harry'  
WHERE emp = 'Dave';  
GO  
SELECT emp,mgr,NoOfReports FROM emp_mgr;  
  
GO  
```  
  
 Результаты до обновления.  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Joe                            0  
Harry                          NULL                           1  
Joe                            Alice                          1  
Paul                           Alice                          0  
```  
  
 Результаты после обновления.  
  
```  
emp                            mgr                           NoOfReports  
------------------------------ ----------------------------- -----------  
Alice                          Harry                          2  
Dave                           Harry                          0  
Harry                          NULL                           2  
Joe                            Alice                          0  
Paul                           Alice                          0  
```  
  
 **Установка параметра nested triggers**  
  
-   [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
 **Установка параметра базы данных RECURSIVE_TRIGGERS**  
  
-   [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>См. также  
 [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql)   
 [Настройка конфигурации сервера nested triggers](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md)  
  
  
