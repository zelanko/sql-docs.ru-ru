---
title: "Переопределение по умолчанию точность и масштаб для числовых типов данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 613ec65d838a525251b6682cca477c5c8d24a162
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Переопределение по умолчанию точность и масштаб для числовых типов данных
Если поле SQL_DESC_TYPE в Отменить равно SQL_C_NUMERIC, с помощью вызова **SQLBindCol** или **SQLSetDescField**, поле SQL_DESC_SCALE в Отменить имеет значение 0, и задано поле SQL_DESC_PRECISION с точностью по умолчанию, определяемым драйвером. Это также имеет значение true, если поле SQL_DESC_TYPE в APD равно SQL_C_NUMERIC, с помощью вызова **SQLBindParameter** или **SQLSetDescField**. Это верно для входных данных, ввода вывода или выходных параметров.  
  
 Если любой из стандартных параметров, описанных ранее не подходят для приложения, приложение должно задать поле SQL_DESC_SCALE или SQL_DESC_PRECISION путем вызова **SQLSetDescField** или **SQLSetDescRec**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в структуру SQL_C_NUMERIC, используются поля SQL_DESC_SCALE и SQL_DESC_PRECISION по умолчанию. Если значения по умолчанию не подходят, приложение должно вызвать **SQLSetDescRec** или **SQLSetDescField** для установите значения полей, а затем вызвать **SQLGetData** с *TargetType* из SQL_ARD_TYPE, чтобы использовать значения в поля дескриптора.  
  
 При **SQLPutData** — вызывается, при вызове функции используется SQL_DESC_SCALE и SQL_DESC_PRECISION поля дескриптора записи, которая соответствует данных времени выполнения параметр или столбец, являющиеся APD поля для вызовов  **SQLExecute** или **SQLExecDirect**, или Отменить поля для вызовов **SQLBulkOperations** или **SQLSetPos**.

