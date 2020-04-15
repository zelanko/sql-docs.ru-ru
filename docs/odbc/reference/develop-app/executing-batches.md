---
title: Выполнение batches (ru) Документы Майкрософт
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
ms.openlocfilehash: 0ce0c043fcfad41a624ad129a757a047d2c87fb6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305735"
---
# <a name="executing-batches"></a>Выполнение пакетов
Перед тем, как приложение выполняет пакет инструкций, оно должно сначала проверить, поддерживаются ли они. Для этого приложение вызывает **s'LGetInfo** с SQL_BATCH_SUPPORT, SQL_PARAM_ARRAY_ROW_COUNTS и SQL_PARAM_ARRAY_SELECTS опций. Первый вариант возвращает вопрос о том, поддерживаются ли генерирующие строки и генерирующие результаты операторы в явных пакетах и процедурах, в то время как последние два варианта возвращают информацию о наличии количества строк и в параметризированном исполнении.  
  
 Пакеты выписок выполняются с помощью **S'LExecute** или **S'LExecDirect**. Например, следующий вызов выполняет явную партию инструкций для открытия нового заказа на продажу.  
  
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
  
 При выполнении пакета генерирующих результатов инструкций возвращается один или несколько строк или наборов результатов. Для получения информации о том, как получить их, [см.](../../../odbc/reference/develop-app/multiple-results.md)  
  
 Если партия утверждений включает параметры маркеров, они пронумерованы в порядке увеличения параметра, как и в любом другом операторе. Например, следующая серия заявлений имеет параметры, пронумерованные от 1 до 21; те, в первом заявлении **INSERT** пронумерованы от 1 до 5, а те, в последнем заявлении **INSERT** пронумерованы от 18 до 21.  
  
```  
INSERT INTO Orders (OrderID, CustID, OpenDate, SalesPerson, Status)  
   VALUES (?, ?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
INSERT INTO Lines (OrderID, Line, PartID, Quantity) VALUES (?, ?, ?, ?);  
```  
  
 Для получения дополнительной информации о параметрах [см.](../../../odbc/reference/develop-app/statement-parameters.md)
