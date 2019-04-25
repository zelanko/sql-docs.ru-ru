---
title: Пакеты инструкций SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC]
- SQL statements [ODBC], batches
- batches [ODBC], about batches
ms.assetid: 766488cc-450c-434c-9c88-467f6c57e17c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09805ab73af76bc55890222fc1ffd0e1857d0f33
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62447392"
---
# <a name="batches-of-sql-statements"></a>Пакеты инструкций SQL
Пакет инструкций SQL является группой из двух или более инструкций SQL или отдельной инструкции SQL, который имеет тот же эффект, как группа из двух или более инструкций SQL. В некоторых реализациях инструкция весь пакет выполняется, прежде чем результаты будут доступны. Это часто более эффективен, чем отправка инструкций по, в том случае, так как часто можно сократить сетевой трафик и источника данных иногда может оптимизировать выполнение пакета инструкций SQL. В других реализациях вызова **SQLMoreResults** вызывает выполнение следующей инструкции в пакете. ODBC поддерживает следующие типы пакетов:  
  
-   **Явные пакетов** *явные пакета* имеет два или несколько инструкций SQL, разделенных точкой с запятой (;). Например следующий пакет инструкций SQL, откроется новый заказ на продажу. Для этого Вставка строк в таблицы заказов и строк. Обратите внимание, что после последней инструкции не точкой с запятой.  
  
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
  
-   **Процедуры** Если процедура содержит более одной инструкции SQL, он считается пакет инструкций SQL. Например следующая инструкция связанные с SQL Server создает процедуру, которая возвращает результирующий набор, содержащий сведения о клиенте и результирующий набор со списком всех открытых заказов на продажу для этого клиента:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     **CREATE PROCEDURE** самой инструкции не пакет инструкций SQL. Однако процедуру, которую он создает является пакет инструкций SQL. Без точки с запятой разделения двух **ВЫБЕРИТЕ** инструкций поскольку **CREATE PROCEDURE** инструкция относится только к SQL Server и SQL Server не требует точки с запятой для разделения нескольких инструкций в  **CREATE PROCEDURE** инструкции.  
  
-   **Массивы параметров** массивы параметров можно использовать с параметризованную инструкцию SQL, как эффективный способ выполнения массовых операций. Например, можно использовать массивы параметров со следующими **вставить** инструкцию, чтобы вставить несколько строк в таблицу строки при выполнении только одну инструкцию SQL:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Если источник данных не поддерживает массивы параметров, драйвер их можно эмулировать, выполнив инструкцию SQL один раз для каждого набора параметров. Дополнительные сведения см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md) и [массивы значений параметров](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)далее в этом разделе.  
  
 Различные типы пакетов нельзя комбинировать с возможностью. То есть способ определения результат выполнения явных пакетной службы, который включает процедуру вызывает, явные пакетной службы, который использует массивы параметров, и вызова процедуры, которая использует массивы параметров драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции, возвращающие и не возвращающие результаты](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Выполнение пакетов](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Ошибки и пакеты](../../../odbc/reference/develop-app/errors-and-batches.md)
