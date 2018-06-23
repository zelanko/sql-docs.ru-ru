---
title: Использование привязки наборов строк (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
caps.latest.revision: 16
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: bfbf7807e9c754e8358264239acf5d172f7d3591
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087121"
---
# <a name="use-rowset-binding-odbc"></a>Использование привязки наборов строк (ODBC)
    
### <a name="to-use-column-wise-binding"></a>Использование привязки на уровне столбца  
  
1.  Для каждого привязанного столбца выполните следующие действия.  
  
    -   Выделите массив из R (или больше) буферов столбцов для хранения значений данных, где R — это число строк в наборе строк.  
  
    -   При необходимости выделите массив из R (или больше) буферов столбцов для хранения длин данных.  
  
    -   Вызовите [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) чтобы связать значение данных столбца и массивы длин данных со столбцом набора строк.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Задайте число строк в наборе строк (R) в атрибуте SQL_ATTR_ROW_ARRAY_SIZE.  
  
    -   Задайте значение SQL_ATTR_ROW_BIND_TYPE, равное SQL_BIND_BY_COLUMN.  
  
    -   Задайте значение атрибута SQL_ATTR_ROWS_FETCHED_PTR, которое указывает на переменную SQLUINTEGER, предназначенную для хранения количества извлеченных строк.  
  
    -   Задайте значение SQL_ATTR_ROW_STATUS_PTR, которое указывает на массив array[R] переменных SQLUSSMALLINT, в котором будут храниться признаки состояния строк.  
  
3.  Выполните инструкцию.  
  
4.  Каждый вызов [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) или [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) извлекает строки R и передача данных в привязанные столбцы.  
  
### <a name="to-use-row-wise-binding"></a>Использование привязки на уровне строки  
  
1.  Выделите массив array[R] структур, где R — это число строк в наборе строк. Структура должна иметь по одному элементу для каждого столбца, а каждый элемент должен состоять из двух частей:  
  
    -   первая часть — это переменная подходящего типа данных, в которой будут храниться данные столбца;  
  
    -   вторая часть — это переменная SQLINTEGER, в которой будет храниться признак состояния столбца.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Задайте число строк в наборе строк (R) в атрибуте SQL_ATTR_ROW_ARRAY_SIZE.  
  
    -   В атрибуте SQL_ATTR_ROW_BIND_TYPE задайте размер структуры, выделенной в шаге 1.  
  
    -   Задайте значение атрибута SQL_ATTR_ROWS_FETCHED_PTR, которое указывает на переменную SQLUINTEGER, предназначенную для хранения количества извлеченных строк.  
  
    -   В атрибуте SQL_ATTR_PARAMS_STATUS_PTR задайте указатель на массив array[R] из переменных SQLUSSMALLINT, в котором будут храниться признаки состояния строк.  
  
3.  Для каждого столбца в результирующем наборе, вызовите [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) чтобы связать значение данных и указатель на длину данных столбца с соответствующими им переменными в первом элементе массива структур, выделенных на шаге 1.  
  
4.  Выполните инструкцию.  
  
5.  Каждый вызов [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) или [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) извлекает строки R и передача данных в привязанные столбцы.  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций по курсорам &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md)   
 [Способы реализации курсоров](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Использование курсоров &#40;ODBC&#41;](use-cursors-odbc.md)  
  
  