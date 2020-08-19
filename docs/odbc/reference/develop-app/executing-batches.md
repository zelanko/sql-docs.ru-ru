---
description: Выполнение пакетов
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b3bb923f95dfcfb731d472aad8ead7ff35053171
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424646"
---
# <a name="executing-batches"></a>Выполнение пакетов
Перед выполнением пакета инструкций приложение должно сначала проверить, поддерживаются ли они. Для этого приложение вызывает **SQLGetInfo** с параметрами SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS и SQL_PARAM_ARRAY_SELECTS. Первый параметр возвращает информацию о том, поддерживаются ли в явных пакетах и процедурах инструкции создания и создания результирующих наборов строк, а последние два параметра возвращают сведения о доступности количества строк и результирующих наборов в параметризованном выполнении.  
  
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
