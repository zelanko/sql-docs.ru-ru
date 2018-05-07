---
title: Позиционированные обновления (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-odbc-cursors
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 6393902a8b9a24ecac4df3ffbfff95fdac2ea686
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="positioned-updates-odbc"></a>Позиционированное обновление (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC поддерживает два метода выполнения позиционированных обновлений в курсоре:  
  
-   **SQLSetPos**  
  
-   предложение WHERE CURRENT OF.  
  
 Наиболее распространенным подходом является использование **SQLSetPos**. Она имеет следующие параметры.  
  
 SQL_POSITION  
 Позиционирует курсор в определенной строке в текущем наборе строк.  
  
 SQL_REFRESH  
 Обновляет программные переменные, привязанные к столбцам результирующего набора, присваивая им новые значения из строки, в которой в настоящий момент позиционирован курсор.  
  
 SQL_UPDATE  
 Обновляет текущую строку в курсоре значениями, хранимыми в программных переменных, которые привязаны к столбцам результирующего набора.  
  
 SQL_DELETE  
 Удаляет текущую строку в курсоре.  
  
 **SQLSetPos** может использоваться с любым результирующим набором, если атрибуты курсора дескриптора инструкции, настроены на использование серверных курсоров инструкции. Столбцы результирующего набора должны быть привязаны к переменным программы. Как только приложение получило строку вызывает **SQLSetPos**(SQL_POSTION) для позиционирования курсора в строке. Затем приложение может вызвать функцию SQLSetPos(SQL_DELETE) для удаления текущей строки или изменить значения привязанных переменных программы и вызвать функцию SQLSetPos(SQL_UPDATE) для обновления текущей строки.  
  
 Приложения могут обновлять или удалять любую строку набора строк с **SQLSetPos**. Вызов **SQLSetPos** является удобной альтернативой созданию и выполнению инструкции SQL. **SQLSetPos** работает с текущим набором строк и может использоваться только после вызова [SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md).  
  
 Размер набора строк устанавливается вызовом [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с аргументом атрибута SQL_ATTR_ROW_ARRAY_SIZE. **SQLSetPos** использует новый размер набора строк, но только после вызова **SQLFetch** или **SQLFetchScroll**. Например, если изменяется размер набора строк **SQLSetPos** вызывается и затем **SQLFetch** или **SQLFetchScroll** вызывается. Вызов **SQLSetPos** используется старый размер набора строк, но **SQLFetch** или **SQLFetchScroll** использует новый размер набора строк.  
  
 Первая строка в наборе строк имеет номер 1. Аргумент RowNumber в **SQLSetPos** должен определять строку в наборе строк; то есть его значение должно быть в диапазоне от 1 до номера строк, которые недавно были извлечены. Оно может быть меньше размера набора строк. Если аргумент RowNumber имеет значение 0, то операция применяется к каждой строке набора строк.  
  
 Операция удаления из **SQLSetPos** позволяет удалить один или несколько выбранных строк таблицы источника данных. Для удаления строк с **SQLSetPos**, приложение вызывает **SQLSetPos** с операциями, значение SQL_DELETE и RowNumber, установленным номер строки для удаления. Если аргумент RowNumber имеет значение 0, то из набора строк удаляются все строки.  
  
 После **SQLSetPos** возвращает удаленную строку текущей строки с состоянием SQL_ROW_DELETED. Строка не может использоваться в любой дополнительных операциях позиционирования, например вызовы [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) или **SQLSetPos**.  
  
 При удалении всех строк набора строк (аргумент RowNumber равен 0), приложение может предотвратить драйвер удаление определенных строк с помощью массива операций строк так же, как для операций обновления **SQLSetPos**.  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения заполняются выборкой, а массив состояния строк сохраняется, то значения каждой из этих позиций строк не должны иметь значение SQL_ROW_DELETED, SQL_ROW_ERROR, или SQL_ROW_NOROW.  
  
 Позиционированные обновления также можно выполнить с помощью предложения WHERE CURRENT OF инструкций UPDATE, DELETE и INSERT. WHERE CURRENT OF необходимо имя курсора, которое ODBC сформирует при [SQLGetCursorName](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) вызывается функция или можно указать путем вызова метода **SQLSetCursorName**. Для обновления с помощью предложения WHERE CURRENT OF в предложении ODBC используются следующие основные шаги.  
  
-   Вызовите **SQLSetCursorName** для задания имени курсора для дескриптора инструкции.  
  
-   Создайте инструкцию SELECT с предложением FOR UPDATE OF и выполните ее.  
  
-   Вызовите **SQLFetchScroll** для извлечения набора строк или **SQLFetch** для извлечения строки.  
  
-   Вызовите **SQLSetPos** (SQL_POSITION) для позиционирования курсора в строке.  
  
-   Построение и выполнение инструкции UPDATE с предложением WHERE CURRENT OF, используя имя курсора, заданное с **SQLSetCursorName**.  
  
 Кроме того, можно вызвать **SQLGetCursorName** после выполнения инструкции SELECT, вместо вызова метода **SQLSetCursorName** перед выполнением инструкции SELECT. **SQLGetCursorName** возвращает имя курсора по умолчанию, назначенное ODBC, если не задано имя курсора с помощью **SQLSetCursorName**.  
  
 **SQLSetPos** предпочтительнее предложения WHERE CURRENT OF при использовании серверных курсоров. Если используется статический обновляемый курсор с библиотекой курсоров ODBC, то данная библиотека реализует обновления предложения WHERE CURRENT OF путем добавления предложения WHERE с ключевыми значениями базовой таблицы. Это может вызвать непреднамеренные обновления, если ключи в таблице не являются уникальными.  
  
## <a name="see-also"></a>См. также  
 [С помощью курсоров & #40; ODBC & #41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
