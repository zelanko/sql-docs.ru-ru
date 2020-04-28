---
title: Переопределить точность в начале и в секундах для типов данных интервала | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1e60d5d8fc696ad8e2bd4cfb0c082ff214e066d0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303605"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных
Если поле SQL_DESC_TYPE АРД имеет значение типа DateTime или Interval C, вызывая либо **SQLBindCol** , либо **SQLSetDescField**, то в поле SQL_DESC_PRECISION (которое содержит точность в секундах) задается следующее значение по умолчанию:  
  
-   6 для меток времени и всех типов данных интервала со вторым компонентом.  
  
-   значение 0 для всех остальных типов данных.  
  
 Для всех типов данных интервалов поле дескриптора SQL_DESC_DATETIME_INTERVAL_PRECISION, которое содержит начальную точность поля, равно значению по умолчанию 2.  
  
 Если поле SQL_DESC_TYPE в APD имеет значение типа DateTime или Interval C, вызывая либо **SQLBindParameter** , либо **SQLSetDescField**, то SQL_DESC_PRECISION и SQL_DESC_DATETIME_INTERVAL_PRECISION поля в APD задаются по умолчанию, заданному ранее. Это справедливо для входных параметров, но не для входных, выходных или выходных параметров.  
  
 Вызов **SQLSetDescRec** устанавливает для интервала начальную точность по умолчанию, но устанавливает точность в секундах (в поле SQL_DESC_PRECISION) на значение аргумента *точности* .  
  
 Если какое-либо значение по умолчанию, заданное ранее, неприемлемо для приложения, приложение должно задать SQL_DESC_PRECISION или SQL_DESC_DATETIME_INTERVAL_PRECISION поле, вызвав **SQLSetDescField**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в тип DateTime или Interval C, используются значения интервала в начале и в секундах, равные интервалу по умолчанию. Если значение по умолчанию не приемлемо, приложение должно вызвать **SQLSetDescField** , чтобы задать либо поле дескриптора, либо **SQLSetDescRec** , чтобы задать SQL_DESC_PRECISION. Вызов **SQLGetData** должен иметь *TargetType* SQL_ARD_TYPE для использования значений в полях дескриптора.  
  
 При вызове **SQLPutData** значение интервала с начальной точностью и интервалом в секундах считывается из полей записи дескриптора, которая соответствует параметру или столбцу, представляющему данные во время выполнения, которые являются полями APD для вызовов **SQLExecute** или **SQLExecDirect**или поля АРД для вызовов **SQLBulkOperations** или **SQLSetPos**.
