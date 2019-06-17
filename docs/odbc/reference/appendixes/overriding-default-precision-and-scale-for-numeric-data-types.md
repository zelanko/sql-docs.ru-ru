---
title: Переопределение по умолчанию точность и масштаб для числовых типов данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- numeric data type [ODBC], precision and scale
- precision [ODBC], numeric data types
- data types [ODBC], numeric data types
- numeric data type [ODBC]
- numeric literals [ODBC]
ms.assetid: 84292334-0e33-4a1b-84de-8c018dd787f3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5f071cf4391c760f7d269382537c3cd4f2b758c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63278312"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Переопределение заданных по умолчанию точности и шкалы для числовых типов данных
Если поле SQL_DESC_TYPE в Отменить присвоено SQL_C_NUMERIC, с помощью вызова **SQLBindCol** или **SQLSetDescField**, поле SQL_DESC_SCALE в Отменить имеет значение 0, и поле SQL_DESC_PRECISION установлено с точностью до драйвера по умолчанию. Это также имеет значение true, если поле SQL_DESC_TYPE в APD присвоено SQL_C_NUMERIC, с помощью вызова **SQLBindParameter** или **SQLSetDescField**. Это справедливо для входных данных, ввода вывода или выходные параметры.  
  
 Если любой из стандартных параметров, описанных ранее недопустимы для приложения, приложение должно задать поле SQL_DESC_SCALE или SQL_DESC_PRECISION путем вызова **SQLSetDescField** или **SQLSetDescRec**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в структуру SQL_C_NUMERIC, используются поля SQL_DESC_SCALE и SQL_DESC_PRECISION по умолчанию. Если значения по умолчанию не являются допустимыми, то приложение должно вызвать **SQLSetDescRec** или **SQLSetDescField** задать поля, а затем вызвать **SQLGetData** с *TargetType* из SQL_ARD_TYPE, чтобы использовать значения в полях дескриптора.  
  
 При **SQLPutData** является именем, вызов использует SQL_DESC_SCALE и SQL_DESC_PRECISION поля дескриптора записи, которая соответствует данных во время выполнения параметра или столбца, которые являются APD поля для вызовов  **SQLExecute** или **SQLExecDirect**, или Отменить поля для вызовов **SQLBulkOperations** или **SQLSetPos**.
