---
title: Переопределить передним и точность секунды для интервальных типов данных | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fdab9e6e60311aca4ce0ae35f92e38c45fdf3702
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63018479"
---
# <a name="overriding-default-leading-and-seconds-precision-for-interval-data-types"></a>Переопределение заданной по умолчанию точности ведущего значения и точности значения долей секунды для интервальных типов данных
Если поле SQL_DESC_TYPE Отменить присвоено C тип datetime или интервал, с помощью вызова **SQLBindCol** или **SQLSetDescField**, поле SQL_DESC_PRECISION (который содержит интервал в секундах следующие значения по умолчанию имеет значение точности):  
  
-   6 для отметки времени и все типы данных интервала с второй компонент.  
  
-   0 для всех других типов данных.  
  
 Для всех типов данных интервала SQL_DESC_DATETIME_INTERVAL_PRECISION поля дескриптора, который содержит начальные поля, точность интервал, присваивается значение по умолчанию 2.  
  
 Если поле SQL_DESC_TYPE в APD присвоено C тип datetime или интервал, с помощью вызова **SQLBindParameter** или **SQLSetDescField**, SQL_DESC_PRECISION и SQL_DESC_DATETIME_INTERVAL_ Точность полей в дескрипторе параметра приложения устанавливаются по умолчанию, представленные ранее. Это справедливо для входных параметров, но не для ввода вывода или выходных параметров.  
  
 Вызов **SQLSetDescRec** задает точности интервала по умолчанию, но задает точность секунд интервал (в поле SQL_DESC_PRECISION) как значение его *точности* аргумент.  
  
 Если любой из заданного значения по умолчанию ранее неприемлем для приложения, приложение должно задать поле SQL_DESC_PRECISION или SQL_DESC_DATETIME_INTERVAL_PRECISION путем вызова **SQLSetDescField**.  
  
 Если приложение вызывает **SQLGetData** для возврата данных в даты и времени или интервал типа C, используются ведущим точность по умолчанию интервал и точность секунды интервала. Если значение умолчанию неприемлем, приложение должно вызвать **SQLSetDescField** настроить либо поле дескриптора, или **SQLSetDescRec** присвоить SQL_DESC_PRECISION. Вызов **SQLGetData** должны иметь *TargetType* из SQL_ARD_TYPE, чтобы использовать значения в полях дескриптора.  
  
 Когда **SQLPutData** называется интервалом начальные точности и интервал секунд точности считываются из поля записи дескриптора, которые соответствуют для данных времени выполнения параметр или столбец, являющиеся APD поля для вызовов Чтобы **SQLExecute** или **SQLExecDirect**, или Отменить поля для вызовов **SQLBulkOperations** или **SQLSetPos**.
