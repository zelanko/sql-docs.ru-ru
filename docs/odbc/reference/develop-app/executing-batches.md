---
title: Выполнение пакетов | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 22c034d4be28ca8c3212fad4ee1493cb0a22d915
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="executing-batches"></a>Выполнение пакетов
Прежде чем приложение выполняет пакет инструкций, ему следует связаться ли они поддерживаются. Чтобы сделать это, приложение вызывает **SQLGetInfo** с параметрами SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS и SQL_PARAM_ARRAY_SELECTS. Возвращает первый вариант параметризацию генерации число строк и результирующий набор генерации инструкций поддерживаются в явной пакеты и процедуры, при последнем два варианта, задает возвращают сведения о доступности из результатов и количество строк в выполнение.  
  
 Пакеты инструкций выполняются через **SQLExecute** или **SQLExecDirect**. Например следующий вызов выполняет явное пакет инструкций, чтобы открыть новый заказ на продажу.  
  
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
  
 Когда пакет создания результат выполнения инструкции, возвращает одно или больше количества строк или результат задает. Сведения о том, как получить эти см [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Если пакет инструкций содержит маркеры параметров, они нумеруются по возрастанию параметра, как и в любой другой инструкции. Например следующий пакет инструкций имеет параметры, которые нумеруются от 1 до 21; в первом **вставить** инструкции являются пронумерованные 1 по 5, так и за последние **вставить** инструкции являются пронумерованные 18 до 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Дополнительные сведения о параметрах см. в разделе [параметров инструкции](../../../odbc/reference/develop-app/statement-parameters.md)далее в этом разделе.
