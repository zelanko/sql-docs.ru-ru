---
title: Позиционированные обновления (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 52495f670986638cac02661240e349713424256e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305334"
---
# <a name="positioned-updates-odbc"></a>Позиционированное обновление (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC поддерживает два метода выполнения позиционированных обновлений в курсоре:  
  
-   **функция SQLSetPos;**  
  
-   предложение WHERE CURRENT OF.  
  
 Более распространенным подходом является использование **S'LSetPos**. Она имеет следующие параметры.  
  
 SQL_POSITION  
 Позиционирует курсор в определенной строке в текущем наборе строк.  
  
 SQL_REFRESH  
 Обновляет программные переменные, привязанные к столбцам результирующего набора, присваивая им новые значения из строки, в которой в настоящий момент позиционирован курсор.  
  
 SQL_UPDATE  
 Обновляет текущую строку в курсоре значениями, хранимыми в программных переменных, которые привязаны к столбцам результирующего набора.  
  
 SQL_DELETE  
 Удаляет текущую строку в курсоре.  
  
 **SLSetPos** может использоваться с любым набором результатов оператора, когда атрибуты курсора обработки оператора настроены на использование курсоров сервера. Столбцы результирующего набора должны быть привязаны к переменным программы. Как только приложение получило строку, он вызывает **S'LSetPos**(SQL_POSTION), чтобы позиционировать курсор на строке. Затем приложение может вызвать функцию SQLSetPos(SQL_DELETE) для удаления текущей строки или изменить значения привязанных переменных программы и вызвать функцию SQLSetPos(SQL_UPDATE) для обновления текущей строки.  
  
 Приложения могут обновлять или удалять любую строку в строке с **помощью S'LSetPos.** Вызов **S'LSetPos** является удобной альтернативой построению и исполнинию оператора S'L. **SLSetPos** работает на текущем наборе строк и может быть использован только после звонка в [S'LFetchScroll.](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)  
  
 Размер Rowset устанавливается вызовом в [S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с аргументом атрибута SQL_ATTR_ROW_ARRAY_SIZE. **SLSetPos** использует новый размер строки, но только после звонка в **S'LFetch** или **S'LFetchScroll.** Например, если размер строки изменен, то называется **S'LSetPos,** а затем — **S'LFetch** или **S'LFetchScroll.** В вызове к **S'LSetPos** используется старый размер рядового набора, но **s'LFetch** или **S'LFetchScroll** использует новый размер строки.  
  
 Первая строка в наборе строк имеет номер 1. Аргумент RowNumber в **S'LSetPos** должен определить строку в строке; то есть, его значение должно находиться в диапазоне между 1 и число строк, которые были совсем недавно принес. Оно может быть меньше размера набора строк. Если аргумент RowNumber имеет значение 0, то операция применяется к каждой строке набора строк.  
  
 Операция удаления **S'LSetPos** заставляет источник данных удалять один или несколько выбранных строк таблицы. Для удаления строк с **помощью S'LSetPos**приложение вызывает **S'LSetPos** с операцией, установленной для SQL_DELETE и RowNumber устанавливается на номер строки для удаления. Если аргумент RowNumber имеет значение 0, то из набора строк удаляются все строки.  
  
 После возвращения **S'LSetPos** удаленная строка — это текущая строка, а ее статус SQL_ROW_DELETED. Строка не может быть использована в любых дополнительных операциях, расположенных, таких как вызовы на [S'LGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) или **S'LSetPos.**  
  
 При удалении всех строк строк строки (RowNumber равен 0), приложение может предотвратить удаление драйвера определенных строк, используя массив работы строки так же, как для операции обновления **S'LSetPos.**  
  
 Каждая удаляемая строка должна существовать в результирующем наборе. Если буферы приложения заполняются выборкой, а массив состояния строк сохраняется, то значения каждой из этих позиций строк не должны иметь значение SQL_ROW_DELETED, SQL_ROW_ERROR, или SQL_ROW_NOROW.  
  
 Позиционированные обновления также можно выполнить с помощью предложения WHERE CURRENT OF инструкций UPDATE, DELETE и INSERT. ГДЕ CURRENT OF требует имя курсора, которое ODBC будет генерировать при вызове функции [S'LGetCursorName,](../../relational-databases/native-client-odbc-api/sqlgetcursorname.md) или которую вы можете указать, позвонив по **s'LSetCursorName.** Для обновления с помощью предложения WHERE CURRENT OF в предложении ODBC используются следующие основные шаги.  
  
-   Позвоните в **S'LSetCursorName,** чтобы установить имя курсора для ручки оператора.  
  
-   Создайте инструкцию SELECT с предложением FOR UPDATE OF и выполните ее.  
  
-   Позвоните **в S'LFetchScroll,** чтобы получить набор строк или **S'LFetch,** чтобы получить строку.  
  
-   Позвоните в **S'LSetPos** (SQL_POSITION), чтобы расположить курсор на строке.  
  
-   Создайте и выполните заявление UPDATE с положением WHERE CURRENT of, используя набор имен курсора с **s'LSetCursorName.**  
  
 Кроме того, вы можете вызвать **s'LGetCursorName** после выполнения оператора SELECT вместо вызова **s'LSetCursorName** перед выполнением оператора SELECT. **S'LGetCursorName** возвращает имя курсора по умолчанию, назначенное ODBC, если вы не установите имя курсора с помощью **S'LSetCursorName.**  
  
 **При** использовании серверных курсоров предпочтительнее, чем где CURRENT OF. Если используется статический обновляемый курсор с библиотекой курсоров ODBC, то данная библиотека реализует обновления предложения WHERE CURRENT OF путем добавления предложения WHERE с ключевыми значениями базовой таблицы. Это может вызвать непреднамеренные обновления, если ключи в таблице не являются уникальными.  
  
## <a name="see-also"></a>См. также:  
 [Использование курсоров &#40;&#41;ODBC](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
