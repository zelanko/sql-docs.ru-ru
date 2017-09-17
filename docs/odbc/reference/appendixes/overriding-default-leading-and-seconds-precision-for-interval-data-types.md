---
title: "Переопределение начальные и точность секунды для типа данных Interval | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types [ODBC], interval data types
- precision [ODBC], interval data types
- seconds precision [ODBC]
- interval data type [ODBC], precision
- interval leading precision [ODBC]
- interval precision [ODBC]
ms.assetid: 3d65493f-dce7-4d29-9f59-c63a4e47918c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1ce549be1e3222f41615e5935418cf3e02e767a4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Переопределение первое значение по умолчанию и точность секунды для типа данных Interval
Если поле SQL_DESC_TYPE Отменить равно C тип datetime или интервал, с помощью вызова **SQLBindCol** или **SQLSetDescField**, поле SQL_DESC_PRECISION (который содержит интервал в секундах следующие значения по умолчанию задано точность):  
  
-   6 для отметки времени и все типы данных интервала с секунды.  
  
-   0 для всех других типов данных.  
  
 Для всех типов данных интервала поле дескриптора SQL_DESC_DATETIME_INTERVAL_PRECISION содержит начальные поля, точность интервала, присваивается значение по умолчанию 2.  
  
 Если поле SQL_DESC_TYPE в APD равно C тип datetime или интервал, с помощью вызова **SQLBindParameter** или **SQLSetDescField**, SQL_DESC_PRECISION и SQL_DESC_DATETIME_INTERVAL_ Точность поля в дескрипторе параметра приложения, присваивается значение по умолчанию, заданного ранее. Это справедливо и для входных параметров, но не для ввода вывода или выходных параметров.  
  
 Вызов **SQLSetDescRec** задает точности интервала по умолчанию, но задает точность секунд интервал (в поле SQL_DESC_PRECISION) как значение его *точности* аргумент.  
  
 Если одно из значений по умолчанию с заданным ранее неприемлем для приложения, приложение должно задать поле SQL_DESC_PRECISION или SQL_DESC_DATETIME_INTERVAL_PRECISION путем вызова **SQLSetDescField**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в тип datetime или тип C интервал, используются начальные точность по умолчанию интервал и интервал секунды. Если либо по умолчанию не является допустимым, то приложение должно вызвать **SQLSetDescField** для установки либо поле дескриптора или **SQLSetDescRec** для задания SQL_DESC_PRECISION. Вызов **SQLGetData** должен иметь *TargetType* из SQL_ARD_TYPE, чтобы использовать значения в поля дескриптора.  
  
 Когда **SQLPutData** вызывается интервала точности и интервал секунд точности считываются из поля записи дескриптора, которые соответствуют параметру данных во время выполнения или столбец, являющиеся APD поля для вызовов Чтобы **SQLExecute** или **SQLExecDirect**, или Отменить поля для вызовов **SQLBulkOperations** или **SQLSetPos**.
