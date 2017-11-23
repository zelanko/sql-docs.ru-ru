---
title: "Выполнение пакетов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batches [ODBC], executing
- SQL statements [ODBC], batches
ms.assetid: f082c717-4f82-4820-a2fa-ba607d8fd872
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0ca3a769ca983cae0cb7a2bc629c366b184b067e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
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
