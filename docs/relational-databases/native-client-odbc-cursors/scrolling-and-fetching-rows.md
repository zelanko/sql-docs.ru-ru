---
title: "Прокрутка и выборка строк | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
caps.latest.revision: "34"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 272d7824230c8caa67f8ff1bdd60a8f40c836655
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="scrolling-and-fetching-rows"></a>Прокрутка и выборка строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Чтобы можно было использовать прокручиваемый курсор в приложение ODBC, необходимо выполнить следующие действия.  
  
-   Задать возможности курсора с помощью [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Открытие курсора с помощью **SQLExecute** или **SQLExecDirect**.  
  
-   Выполнить прокрутку и выборку строк с помощью **SQLFetch** или [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Оба **SQLFetch** и **SQLFetchSroll** можно извлекать блоки строк за один раз. Число строк, возвращенных задается с помощью **SQLSetStmtAttr** для параметра SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Приложения ODBC могут использовать **SQLFetch** производить выборку однонаправленный курсор.  
  
 **SQLFetchScroll** используется для прокрутки по курсору. **SQLFetchScroll** поддерживает выборку следующего, предыдущего, первого и последнего набора строк помимо относительной (набора строк,  *n*  строк от начала текущего набора строк) и абсолютной (fetch набор строк, начиная со строки  *n* ). Если  *n*  имеет отрицательное значение при абсолютной выборке, то строки отсчитываются с конца результирующего набора. Абсолютная выборка строки -1 означает, что будет возвращен набор строк, начинающийся с последней строки результирующего набора.  
  
 Приложения, использующие **SQLFetchScroll** только для своего блока возможности курсора, таких как отчеты, обычно просматривают результирующий набор только один раз, используя только параметр для получения следующего набора строк. На экране приложений, с другой стороны, можно воспользоваться преимуществами все возможности **SQLFetchScroll**. Если приложение задает размер набора строк на число строк, отображаемых на экране и привязывает буферы экранов к результирующему набору, оно может преобразовывать операции полосы прокрутки непосредственно в вызовы **SQLFetchScroll**.  
  
|Операция полосы прокрутки|Параметр прокрутки SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|На страницу вверх|SQL_FETCH_PRIOR|  
|На страницу вниз|SQL_FETCH_NEXT|  
|На строку вверх|SQL_FETCH_RELATIVE с FetchOffset, равным -1|  
|На строку вниз|SQL_FETCH_RELATIVE с FetchOffset, равным 1|  
|Ползунок вверх|SQL_FETCH_FIRST|  
|Ползунок вниз|SQL_FETCH_LAST|  
|Случайное положение ползунка|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание закладок строк в ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [С помощью курсоров &#40; ODBC &#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
