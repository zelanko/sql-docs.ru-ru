---
title: Функция SQLGetCursorName | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4017ed07681a74da4832db2db3aeabddf22edb19
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68020334"
---
# <a name="sqlgetcursorname-function"></a>Функция SQLGetCursorName
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetCursorName** возвращает имя курсора, связанного с указанной инструкцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *cursorName*  
 [Выход] Указатель на буфер, в которую будет возвращено имя курсора.  
  
 Если *CursorName* имеет значение NULL, *NameLengthPtr* по-прежнему возвращает общее число символов (включая знак завершения null для символьных данных) для возврата в буфере, на которые указывают *CursorName*.  
  
 *BufferLength*  
 [Вход] Длина \* *CursorName*, в символах. Если значение в  *\*CursorName* строка в Юникоде (при вызове **SQLGetCursorNameW**), *BufferLength* аргумент должен быть четным числом.  
  
 *NameLengthPtr*  
 [Выход] Указатель на область памяти, в которую будет возвращено общее число символов (за исключением знака завершения null) для возврата в \* *CursorName*. Если количество символов, доступных для возврата больше или равно *BufferLength*, имя курсора в \* *CursorName* усекается до *BufferLength*минус длина знак завершения null.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetCursorName** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, можно получить путем вызова связанного значения SQLSTATE **SQLGetDiagRec** с *HandleType*значение SQL_HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetCursorName** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Буфер \* *CursorName* не достаточно для возврата имени всего курсора, поэтому имя курсора был усечен. Длина имени курсора неусеченный возвращается в **NameLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Если по-прежнему выполнении асинхронной функции **SQLGetCursorName** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ДОСТУПНО. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY015|Имена курсоров недоступны|(DM) драйвер был ODBC 2 *.x* драйвера, не открытый курсор на инструкцию, и имя курсора не было значение с **SQLSetCursorName**.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, заданное в аргументе *BufferLength* меньше 0.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированного обновления и удаления инструкций (например, **обновление** _имя таблицы_ ... **WHERE CURRENT OF** _имя курсора_). Дополнительные сведения см. в разделе [расположен обновления и удаления инструкций](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Если приложение не вызывает **SQLSetCursorName** для определения имени курсора, драйвер создает имя. Это имя начинается с букв SQL_CUR.  
  
> [!NOTE]
>  В ODBC 2 *.x*, когда возникла без открытого курсора, и имя не было значение путем вызова **SQLSetCursorName**, вызов **SQLGetCursorName** возвращается SQLSTATE HY015 (имена курсоров доступна). В ODBC 3 *.x*, это больше не true; независимо от того, когда **SQLGetCursorName** является именем, драйвер возвращает имя курсора.  
  
 **SQLGetCursorName** возвращает имя курсора, создан ли имя явно или неявно. Имя курсора создается неявно в том случае, если **SQLSetCursorName** не вызывается. **SQLSetCursorName** можно вызвать, чтобы переименовать курсора в инструкции до тех пор, пока курсор находится в состоянии выделением или подготовленной.  
  
 Имя курсора, который может быть задан явно или неявно остается установленным до *StatementHandle* с которым он связан удаляется, с помощью **SQLFreeHandle** с *HandleType* значение SQL_HANDLE_STMT.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнении подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка инструкции к выполнению|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Задав имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
