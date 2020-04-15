---
title: Прокрутка и извлечение строк Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ae9f1079f329951045d4b3f61b39c12efc153fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302500"
---
# <a name="scrolling-and-fetching-rows"></a>Прокрутка и выборка строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Чтобы можно было использовать прокручиваемый курсор в приложение ODBC, необходимо выполнить следующие действия.  
  
-   Установите возможности курсора с помощью [S'LSetStmtAttr.](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)  
  
-   Откройте курсор с помощью **S'LExecute** или **S'LExecDirect**.  
  
-   Прокрутка и получение строк с помощью **S'LFetch** или [S'LFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Как **S'LFetch,** так и **S'LFetchSroll** могут одновременно получать блоки строк. Количество возвращенных строк указывается с помощью **S'LSetStmtAttr** для установки SQL_ATTR_ROW_ARRAY_SIZE параметра.  
  
 Приложения ODBC могут использовать **S'LFetch** для получения с помощью форвардного курсора.  
  
 Для прокрутки курсора используется **s'LFetchScroll.** **SLFetchScroll** поддерживает получение следующего, предварительного, первого и последнего рядов в дополнение к относительному извлечению (получение *строки n* строки от начала текущего rowset) и абсолютной извлечения (получить rowset, начиная с строки *n*). Если *n* отрицательный в абсолютном извлечении, строки отсчитываются из конца набора результатов. Абсолютная выборка строки -1 означает, что будет возвращен набор строк, начинающийся с последней строки результирующего набора.  
  
 Приложения, использующие **S'LFetchScroll** только для своих возможностей блок-курсора, например отчетов, скорее всего, пройдут через набор результатов в один раз, используя только возможность получить следующий набор строк. С другой стороны, приложения на основе экрана могут воспользоваться всеми возможностями **S'LFetchScroll.** Если приложение устанавливает размер строки к количеству строк, отображаемых на экране, и связывает буферы экрана с набором результатов, оно может переводить операции строки прокрутки непосредственно на вызовы в **S'LFetchScroll.**  
  
|Операция полосы прокрутки|Параметр прокрутки SQLFetchScroll|  
|--------------------------|-------------------------------------|  
|На страницу вверх|SQL_FETCH_PRIOR|  
|На страницу вниз|SQL_FETCH_NEXT|  
|На строку вверх|SQL_FETCH_RELATIVE с FetchOffset равна -1|  
|На строку вниз|SQL_FETCH_RELATIVE с FetchOffset, равным 1|  
|Ползунок вверх|SQL_FETCH_FIRST|  
|Ползунок вниз|SQL_FETCH_LAST|  
|Случайное положение ползунка|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Создание закладок строк в ODBC](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Использование курсоров &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
