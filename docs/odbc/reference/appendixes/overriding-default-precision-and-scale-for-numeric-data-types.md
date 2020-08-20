---
description: Переопределение заданных по умолчанию точности и шкалы для числовых типов данных
title: Переопределение точности и масштаба по умолчанию для числовых типов данных | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 798e607ff6584bde27791a29e4b20aeb1d7bb3cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466086"
---
# <a name="overriding-default-precision-and-scale-for-numeric-data-types"></a>Переопределение заданных по умолчанию точности и шкалы для числовых типов данных
Если поле SQL_DESC_TYPE в АРД имеет значение SQL_C_NUMERIC, вызывая либо **SQLBindCol** , либо **SQLSetDescField**, поле SQL_DESC_SCALE в АРД имеет значение 0, а в поле SQL_DESC_PRECISION задана точность по умолчанию, определенная драйвером. Это также справедливо, если поле SQL_DESC_TYPE в APD имеет значение SQL_C_NUMERIC, вызывая либо **SQLBindParameter** , либо **SQLSetDescField**. Это справедливо для входных, входных и выходных параметров.  
  
 Если одно из описанных выше значений по умолчанию неприемлемо для приложения, приложение должно задать SQL_DESC_SCALE или SQL_DESC_PRECISION поле, вызвав **SQLSetDescField** или **SQLSetDescRec**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в структуру SQL_C_NUMERIC, используются поля SQL_DESC_SCALE и SQL_DESC_PRECISION по умолчанию. Если значения по умолчанию неприемлемы, приложение должно вызвать **SQLSetDescRec** или **SQLSetDescField** , чтобы задать поля, а затем вызвать **SQLGetData** с *TargetType* SQL_ARD_TYPE для использования значений в полях дескриптора.  
  
 При вызове **SQLPutData** в вызове используются поля SQL_DESC_SCALE и SQL_DESC_PRECISION записи дескриптора, которые соответствуют параметру или столбцу, который используется для данных во время выполнения, которые являются полями APD для вызовов **SQLExecute** или **SQLExecDirect**или поля АРД для вызовов **SQLBulkOperations** или **SQLSetPos**.
