---
title: Функция SQLGetCursorName | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69a0da5196c5724284c2da75dc6c7deb3c3cedcd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetcursorname-function"></a>Функция SQLGetCursorName
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLGetCursorName** возвращает имя курсора, связанные с указанной инструкцией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *CursorName*  
 [Выход] Указатель на буфер, в котором для возвращения имени курсора.  
  
 Если *CursorName* имеет значение NULL, *NameLengthPtr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфере, на который указывает *CursorName*.  
  
 *BufferLength*  
 [Вход] Длина \* *CursorName*, в символах. Если значение в  *\*CursorName* строка в Юникоде (при вызове **SQLGetCursorNameW**), *BufferLength* аргумент должен быть четным числом.  
  
 *NameLengthPtr*  
 [Выход] Указатель памяти, в которую возвращается общее число символов (за исключением знака завершения null) для возврата в \* *CursorName*. Если количество символов вернуть больше или равно *BufferLength*, имя курсора в \* *CursorName* усекается до *BufferLength*за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetCursorName** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType*значение sql_handle_stmt и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetCursorName** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Буфер \* *CursorName* не был достаточно велик, чтобы возвращать имя всего курсора, поэтому имя курсора было усечено. Длина имени неусеченный курсора, возвращаемых в **NameLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом асинхронной функция **SQLGetCursorName** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для *StatementHandle* и возвращается SQL_PARAM_DATA_ ЭТОТ ПАРАМЕТР ДОСТУПЕН. До получения данных для всех параметров потоковой вызове этой функции.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY015|Имена курсоров недоступны|(DM) был драйвер ODBC 2*.x* драйвера, не открытый курсор на инструкцию, и имена курсоров ранее было задано с **SQLSetCursorName**.|  
|HY090|Недопустимая длина строки или буфера|Значение (DM), указанный в аргументе *BufferLength* был меньше 0.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированного обновления и удаления инструкций (например, **обновление** *имя таблицы* ... **WHERE CURRENT OF** *имя курсора*). Дополнительные сведения см. в разделе [располагается обновление и удаление операторов](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Если приложение не вызывает **SQLSetCursorName** для определения имени курсора, драйвер создает имя. Это имя начинается с буквы SQL_CUR.  
  
> [!NOTE]  
>  В ODBC 2*.x*, когда произошла нет открытого курсора, а не имя ранее было задано с помощью вызова **SQLSetCursorName**, вызов **SQLGetCursorName** возвращается SQLSTATE HY015 (имена курсоров Этот параметр доступен). В ODBC 3*.x*, это больше не имеет значение true; независимо от того, когда **SQLGetCursorName** является именем, драйвер возвращает имя курсора.  
  
 **SQLGetCursorName** возвращает имя курсора, создан ли имя явно или неявно. Имя курсора создается неявно, если **SQLSetCursorName** не вызывается. **SQLSetCursorName** можно вызвать, чтобы переименовать курсора в инструкции до тех пор, пока курсор находится в состоянии выделенный или подготовленной.  
  
 Имя курсора, который может быть задан явно или неявно остается установленным до *StatementHandle* с которым он связан удаляется, с помощью **SQLFreeHandle** с *HandleType* значение sql_handle_stmt.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Подготовка инструкции для выполнения|[Функция SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|Имя курсора|[Функция SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
