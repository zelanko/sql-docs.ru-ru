---
title: "Пакеты инструкций SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: d2ae8d60d6e41536bc67bd14f9252c372fdeaa5c
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="batches-of-sql-statements"></a>Пакеты инструкций SQL
Пакет инструкций SQL является группой из двух или более инструкций SQL или отдельной инструкции SQL, который имеет тот же эффект, как группа из двух или более инструкций SQL. В некоторых реализациях инструкцию весь пакет выполняется перед доступны все результаты. Это часто более эффективен, чем отправка инструкций по одной, так как часто можно сократить сетевой трафик и источник данных иногда может оптимизировать выполнение пакетных инструкций SQL. В других реализациях вызов **SQLMoreResults** вызывает выполнение следующей инструкции в пакете. ODBC поддерживает следующие типы пакетов:  
  
-   **Явные пакетов** *явные пакета* имеет два или несколько инструкций SQL, разделенных точкой с запятой (;). Например следующий пакет инструкций SQL открывает новый заказ на продажу. Для этого необходимо вставить строки в таблицы заказов и строк. Обратите внимание, что точка с запятой после последней инструкции.  
  
    ```  
    INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
       VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 1, 1234, 10);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 2, 987, 8);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 3, 566, 17);  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (2002, 4, 412, 500)  
    ```  
  
-   **Процедуры** Если процедура содержит более одной инструкции SQL, он считается пакет инструкций SQL. Например следующая инструкция характерные для SQL Server создает процедуру, которая возвращает результирующий набор, содержащий сведения о клиенте и результирующий набор со списком всех открытых заказов на продажу для этого клиента:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     **CREATE PROCEDURE** не самой инструкции пакета инструкций SQL. Однако процедура, на которую он создает является пакет инструкций SQL. Без точки с запятой разделять их **ВЫБЕРИТЕ** инструкции из-за **CREATE PROCEDURE** инструкция относится только к SQL Server и SQL Server не требуется точка с запятой для разделения нескольких инструкций в  **CREATE PROCEDURE** инструкции.  
  
-   **Массивы параметров** массивы параметров можно использовать с параметризованную инструкцию SQL как эффективный способ выполнения массовых операций. Например, можно использовать массивы параметров со следующими **вставить** инструкции для вставки нескольких строк в таблицу строки при выполнении только одну инструкцию SQL:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Если источник данных не поддерживает массивы параметров, драйвер эмуляции их, выполнив инструкцию SQL один раз для каждого набора параметров. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md) и [массивы значений параметров](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)далее в этом разделе.  
  
 Взаимодействие невозможно комбинировать различные типы пакетов. Т. е как приложение определяет результат выполнения явного пакет, который включает процедура вызывает явную пакета, в котором используется массив параметров, и вызова процедуры, которая использует массивы параметров зависит от конкретного драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции, возвращающие и не возвращающие результаты](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Выполнение пакетов](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Ошибки и пакеты](../../../odbc/reference/develop-app/errors-and-batches.md)
