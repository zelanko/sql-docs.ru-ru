---
title: Прокрутка и выборка строк | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a0c0f7f2cad7eaecc212e2283fab7fc7d69f2ee7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63207127"
---
# <a name="scrolling-and-fetching-rows"></a>Прокрутка и выборка строк
  Чтобы можно было использовать прокручиваемый курсор в приложение ODBC, необходимо выполнить следующие действия.  
  
-   Задать возможности курсора с помощью [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).  
  
-   Открытие курсора с помощью **SQLExecute** или **SQLExecDirect**.  
  
-   Прокрутку и выборку строк с помощью **SQLFetch** или [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).  
  
 Оба **SQLFetch** и **SQLFetchSroll** можно извлекать блоки строк за один раз. Число возвращаемых строк задается с помощью **SQLSetStmtAttr** установить параметр SQL_ATTR_ROW_ARRAY_SIZE.  
  
 Приложения ODBC могут использовать **SQLFetch** производить выборку однопроходный курсор.  
  
 **SQLFetchScroll** используется для прокрутки по курсору. **SQLFetchScroll** поддерживает выборку следующего, предыдущего, первого и последнего наборов строк, помимо относительной (набора строк, *n* строк с начала текущего набора строк) и абсолютной (fetch набор строк начиная со строки *n*). Если *n* имеет отрицательное значение в абсолютная выборка, строки отсчитываются с конца результирующего набора. Абсолютная выборка строки -1 означает, что будет возвращен набор строк, начинающийся с последней строки результирующего набора.  
  
 Приложения, использующие **SQLFetchScroll** только для своего блока возможности курсора, такие как отчеты, скорее всего для передачи из результирующего набора, один раз, только в режиме для получения следующего набора строк. На экране приложений, с другой стороны, можно воспользоваться преимуществами все возможности **SQLFetchScroll**. Если приложение задает размер набора строк, равное количеству строк, отображаемых на экране и привязывает буферы экранов к результирующему набору, то оно может преобразовывать операции полосы прокрутки непосредственно в вызовы **SQLFetchScroll**.  
  
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
  
-   [Создание закладок строк в ODBC](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  
