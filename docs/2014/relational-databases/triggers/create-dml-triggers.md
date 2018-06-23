---
title: Создание триггеров DML | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-dml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- encryption [SQL Server], DML triggers
- deferred name resolution, DML triggers
- WITH ENCRYPTION clause
- IF UPDATE
- SET statement, DML triggers
- DML triggers, programming
- testing column changes
- results [SQL Server], DML triggers
ms.assetid: b2b52258-642b-462e-8e0f-18c09d2eccf4
caps.latest.revision: 30
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9fdbff3f7bc6957a72c4bfb674552f6a213e41d6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188435"
---
# <a name="create-dml-triggers"></a>Создание триггеров DML
  В этом разделе описано, как создать триггер DML [!INCLUDE[tsql](../../includes/tsql-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER.  
  
##  <a name="Top"></a> Перед началом  
  
### <a name="limitations-and-restrictions"></a>Ограничения  
 Список ограничений, связанных с созданием триггеров DML, см. в разделе [CREATE TRIGGER (Transact-SQL)](/sql/t-sql/statements/create-trigger-transact-sql).  
  
###  <a name="Permissions"></a> Permissions  
 Требует разрешения ALTER на таблицу или представление, на которых создается триггер.  
  
##  <a name="Procedures"></a> Как создать триггер DML  
 Можно использовать один из следующих способов:  
  
-   [Среда SQL Server Management Studio](#SSMSProcedure)  
  
-   [Transact-SQL](#TsqlProcedure)  
  
###  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] и разверните его.  
  
2.  Разверните узел **Базы данных**, разверните базу данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] , разверните узел **Таблицы** , а затем таблицу **Purchasing.PurchaseOrderHeader**.  
  
3.  Правой кнопкой мыши щелкните элемент **Триггеры**, а затем выберите пункт **Создать триггер**.  
  
4.  В меню **Запрос** выберите пункт **Указать значения для параметров шаблона**. Можно также нажать клавиши CTRL-SHIFT-M, чтобы открыть диалоговое окно **Задание значений для параметров шаблона** .  
  
5.  В диалоговом окне **Задание значений для параметров шаблона** введите для показанных параметров следующие значения.  
  
    |Параметр|Значение|  
    |---------------|-----------|  
    |Автор|*Ваше имя*|  
    |Дата создания|*Сегодняшняя дата*|  
    |Описание|Проверяет кредитоспособность поставщика, прежде чем позволить вставить новый заказ на покупку от этого поставщика.|  
    |Имя_схемы|Purchasing|  
    |Имя_триггера|NewPODetail2|  
    |Имя_таблицы|PurchaseOrderDetail|  
    |Команда_изменения_данных|Удаление инструкций UPDATE и DELETE из списка.|  
  
6.  Нажмите кнопку **ОК**.  
  
7.  В **редакторе запросов**замените комментарий `-- Insert statements for trigger here` следующей инструкцией:  
  
    ```tsql  
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
  
8.  Чтобы проверить синтаксис, в меню **Запрос** выберите пункт **Синтаксический анализ**. Если появится сообщение об ошибке, сравните эту инструкцию с вышеуказанной информацией, внесите исправления и повторите этот шаг.  
  
9. Чтобы создать триггер DML, в меню **Запрос** нажмите **Выполнить**. Триггер DML создается как объект в базе данных.  
  
10. Чтобы увидеть этот триггер DML в обозревателе объектов, щелкните правой кнопкой мыши элемент **Триггеры** и выберите пункт **Обновить**.  
  
 [Перед началом](#Top)  
  
###  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)] и разверните его.  
  
2.  В меню **Файл** выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере создается такой же хранимый триггер DML, как показано выше.  
  
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
  
##  <a name="PowerShellProcedure"></a> [Перед началом](#Top)  
  
  
