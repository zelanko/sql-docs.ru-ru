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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d68ea1c13655ca7c57ba076823f461a4b2e22055
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81283514"
---
# <a name="batches-of-sql-statements"></a>Пакеты инструкций SQL
Пакет инструкций SQL — это группа из двух или более инструкций SQL или одна инструкция SQL, которая имеет тот же результат, что и группа из двух или более инструкций SQL. В некоторых реализациях выполняется вся Пакетная инструкция, прежде чем будут доступны все результаты. Это часто более эффективно, чем отправка инструкций по отдельности, так как сетевой трафик часто сокращается, а источник данных может оптимизировать выполнение пакета инструкций SQL. В других реализациях вызов **SQLMoreResults** активирует выполнение следующего оператора в пакете. ODBC поддерживает следующие типы пакетов:  
  
-   **Явные пакеты** *Явный пакет* состоит из двух или более инструкций SQL, разделенных точкой с запятой (;). Например, следующий пакет инструкций SQL открывает новый заказ на продажу. Для этого необходимо вставить строки в таблицы Orders и Lines. Обратите внимание, что после последней инструкции отсутствует точка с запятой.  
  
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
  
-   **Процедуры** Если процедура содержит более одной инструкции SQL, она считается пакетом инструкций SQL. Например, следующая SQL Server инструкция создает процедуру, которая возвращает результирующий набор, содержащий сведения о клиенте, и результирующий набор, перечисляющий все открытые заказы на продажу для этого клиента:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Сама инструкция **CREATE PROCEDURE** не является пакетом инструкций SQL. Однако создаваемая им процедура является пакетом инструкций SQL. Две инструкции **SELECT** не разделяются точкой с запятой, так как инструкция **CREATE PROCEDURE** относится только к SQL Server, а SQL Server не требует точки с запятой для разделения нескольких инструкций в инструкции **CREATE PROCEDURE** .  
  
-   **Массивы параметров** Массивы параметров можно использовать с параметризованной инструкцией SQL как эффективный способ выполнения массовых операций. Например, массивы параметров можно использовать со следующей инструкцией **INSERT** для вставки нескольких строк в таблицу Lines при выполнении только одной инструкции SQL:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Если источник данных не поддерживает массивы параметров, драйвер может эмулировать их, выполняя инструкцию SQL один раз для каждого набора параметров. Дополнительные сведения см. в подразделе [параметры инструкций](../../../odbc/reference/develop-app/statement-parameters.md) и [массивы значений параметров](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)далее в этом подразделе.  
  
 Разные типы пакетов не могут быть смешаны в режиме взаимодействия. То есть, как приложение определяет результат выполнения явного пакета, включающего в себя вызовы процедур, явный пакет, использующий массивы параметров, и вызов процедуры, использующий массивы параметров, зависит от драйвера.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции, возвращающие и не возвращающие результаты](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Выполнение пакетов](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Ошибки и пакеты](../../../odbc/reference/develop-app/errors-and-batches.md)
