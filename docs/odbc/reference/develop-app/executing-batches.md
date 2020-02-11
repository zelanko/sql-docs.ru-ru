---
title: Исполнение пакетов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 84d3cf65284d767d437987c8ff2b21793466106e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67901262"
---
# <a name="executing-batches"></a>Выполнение пакетов
Перед выполнением пакета инструкций приложение должно сначала проверить, поддерживаются ли они. Для этого приложение вызывает **SQLGetInfo** с параметрами SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS и SQL_PARAM_ARRAY_SELECTS. Первый параметр возвращает информацию о том, поддерживаются ли в явных пакетах и процедурах инструкции создания и создания результирующих наборов строк, а два последних параметра возвращают сведения о доступности количества строк и результирующих наборов в параметризованном виде. InstancePersistenceCommand.  
  
 Пакеты инструкций выполняются с помощью **SQLExecute** или **SQLExecDirect**. Например, следующий вызов выполняет явный пакет инструкций, чтобы открыть новый заказ на продажу.  
  
```  
SQLCHAR *BatchStmt =  
   "INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)"  
      "VALUES (2002, 1001, {fn CURDATE()}, 'Garcia', 'OPEN');"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 1, 1234, 10);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 2, 987, 8);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 3, 566, 17);"  
   "INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (2002, 4, 412, 500)";  
  
SQLExecDirect(hstmt, BatchStmt, SQL_NTS);  
```  
  
 При выполнении пакета инструкций, создающих результаты, возвращается одно или несколько строк или результирующих наборов. Сведения о том, как их получить, см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Если пакет инструкций включает маркеры параметров, они нумеруются в порядке возрастания порядка параметров, как и в любой другой инструкции. Например, в следующем пакете инструкций есть параметры с номерами от 1 до 21; в первой инструкции **INSERT** нумерация выполняется с 1 до 5, а в последней инструкции **INSERT** — с 18 до 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Дополнительные сведения [о параметрах см.](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.
