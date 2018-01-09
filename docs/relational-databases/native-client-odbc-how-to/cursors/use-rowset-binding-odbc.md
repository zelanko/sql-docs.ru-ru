---
title: "Использование привязки наборов строк (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dd9305eccd49f8ec7277b2285d56a439f7cb776d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="use-rowset-binding-odbc"></a>Использование привязки наборов строк (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

    
### <a name="to-use-column-wise-binding"></a>Использование привязки на уровне столбца  
  
1.  Для каждого привязанного столбца выполните следующие действия.  
  
    -   Выделите массив из R (или больше) буферов столбцов для хранения значений данных, где R — это число строк в наборе строк.  
  
    -   При необходимости выделите массив из R (или больше) буферов столбцов для хранения длин данных.  
  
    -   Вызовите [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) чтобы связать значение данных столбца и массивы длин данных со столбцом набора строк.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Задайте число строк в наборе строк (R) в атрибуте SQL_ATTR_ROW_ARRAY_SIZE.  
  
    -   Задайте значение SQL_ATTR_ROW_BIND_TYPE, равное SQL_BIND_BY_COLUMN.  
  
    -   Задайте значение атрибута SQL_ATTR_ROWS_FETCHED_PTR, которое указывает на переменную SQLUINTEGER, предназначенную для хранения количества извлеченных строк.  
  
    -   Задайте значение SQL_ATTR_ROW_STATUS_PTR, которое указывает на массив array[R] переменных SQLUSSMALLINT, в котором будут храниться признаки состояния строк.  
  
3.  Выполните инструкцию.  
  
4.  Каждый вызов [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) или [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) извлекает строки R и передача данных в привязанные столбцы.  
  
### <a name="to-use-row-wise-binding"></a>Использование привязки на уровне строки  
  
1.  Выделите массив array[R] структур, где R — это число строк в наборе строк. Структура должна иметь по одному элементу для каждого столбца, а каждый элемент должен состоять из двух частей:  
  
    -   первая часть — это переменная подходящего типа данных, в которой будут храниться данные столбца;  
  
    -   вторая часть — это переменная SQLINTEGER, в которой будет храниться признак состояния столбца.  
  
2.  Вызовите функцию [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) , чтобы задать следующие атрибуты.  
  
    -   Задайте число строк в наборе строк (R) в атрибуте SQL_ATTR_ROW_ARRAY_SIZE.  
  
    -   В атрибуте SQL_ATTR_ROW_BIND_TYPE задайте размер структуры, выделенной в шаге 1.  
  
    -   Задайте значение атрибута SQL_ATTR_ROWS_FETCHED_PTR, которое указывает на переменную SQLUINTEGER, предназначенную для хранения количества извлеченных строк.  
  
    -   В атрибуте SQL_ATTR_PARAMS_STATUS_PTR задайте указатель на массив array[R] из переменных SQLUSSMALLINT, в котором будут храниться признаки состояния строк.  
  
3.  Для каждого столбца в результирующем наборе, вызовите [SQLBindCol](../../../relational-databases/native-client-odbc-api/sqlbindcol.md) чтобы связать значение данных и указатель на длину данных столбца с соответствующими им переменными в первом элементе массива структур, выделенных на шаге 1.  
  
4.  Выполните инструкцию.  
  
5.  Каждый вызов [SQLFetch](http://go.microsoft.com/fwlink/?LinkId=58401) или [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) извлекает строки R и передача данных в привязанные столбцы.  
  
## <a name="see-also"></a>См. также:  
 [С помощью инструкций по курсорам &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/cursors/using-cursors-how-to-topics-odbc.md)   
 [Способы реализации курсоров](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)   
 [Использование курсоров &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/cursors/use-cursors-odbc.md)  
  
  
