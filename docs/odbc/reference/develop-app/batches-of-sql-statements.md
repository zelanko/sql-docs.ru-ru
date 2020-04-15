---
title: Пакеты заявлений s'L Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283514"
---
# <a name="batches-of-sql-statements"></a>Пакеты инструкций SQL
Пакет заявлений s'L — это группа из двух или более заявлений, которые имеют одиночный эффект, что и группа из двух или более заявлений. В некоторых реализациях вся выписка пакетов выполняется до того, как будут получены какие-либо результаты. Это часто более эффективно, чем отправка отчетов по отдельности, поскольку сетевой трафик часто может быть уменьшен, а источник данных иногда может оптимизировать выполнение пакета инструкций S'L. В других реализациях вызов **S'LMoreResults** запускает выполнение следующего оператора в пакете. ODBC поддерживает следующие типы партий:  
  
-   **Явные пакеты** *Явная партия* — это две или более инструкций, разделенных запятым (;). Например, следующая серия заявлений s'L открывает новый заказ на продажу. Для этого необходимо вставлять строки в таблицы ордеров и линий. Обратите внимание, что после последнего заявления запятой не существует.  
  
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
  
-   **Процедуры** Если процедура содержит более одного оператора S'L, она считается пакетом выписок S'L. Например, в следующем заявлении, конкретном сервере S'L, создается процедура, которая возвращает набор результатов, содержащий информацию о клиенте, и набор результатов, перечисляющий все открытые заказы на продажу для этого клиента:  
  
    ```  
    CREATE PROCEDURE GetCustInfo (@CustomerID INT) AS  
       SELECT * FROM Customers WHERE CustID = @CustomerID  
       SELECT OrderID FROM Orders  
          WHERE CustID = @CustomerID AND Status = 'OPEN'  
    ```  
  
     Заявление **CREATE PROCEDURE** само по себе не является пакетом заявлений S'L. Тем не менее, процедура, которая она создает, представляет собой пакет заявлений s'L. Нет запятых, разделяя две операторы **SELECT,** потому что оператор **CREATE PROCEDURE** специфичен для сервера S'L Server, а сервер S'L Server не требует, чтобы запятые разделяли несколько инструкций в заявлении **CREATE PROCEDURE.**  
  
-   **Массивы параметров** Массивы параметров могут быть использованы с параметризированной выпиской S'L как эффективный способ выполнения оптовых операций. Например, массивы параметров могут быть использованы со следующим заявлением **INSERT** для вставки нескольких строк в таблицу Линий при выполнении только одного оператора S'L:  
  
    ```  
    INSERT INTO Lines (OrderID, Line, PartID, Quantity)  
       VALUES (?, ?, ?, ?)  
    ```  
  
     Если источник данных не поддерживает массивы параметров, драйвер может подражать им, выполнив выписку по s-L один раз для каждого набора параметров. Для получения дополнительной [информации](../../../odbc/reference/develop-app/statement-parameters.md) смотрите параметры оператора и [массивы параметров значений](../../../odbc/reference/develop-app/arrays-of-parameter-values.md), позже в этом разделе.  
  
 Различные типы партий не могут быть смешаны в совместимой манере. То есть, как приложение определяет результат выполнения явной партии, которая включает в себя вызовы процедуры, явная партия, использующий массивы параметров, и вызов процедуры, который использует массивы параметров, специфичен для драйверов.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Инструкции, возвращающие и не возвращающие результаты](../../../odbc/reference/develop-app/result-generating-and-result-free-statements.md)  
  
-   [Выполнение пакетов](../../../odbc/reference/develop-app/executing-batches.md)  
  
-   [Ошибки и пакеты](../../../odbc/reference/develop-app/errors-and-batches.md)
