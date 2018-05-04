---
title: Функция SQLSetCursorName | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLSetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetCursorName
helpviewer_keywords:
- SQLSetCursorName function [ODBC]
ms.assetid: 4e055946-12d4-4589-9891-41617a50f34e
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c9c8ffbcd8c53054bfc3ce1638aa0f5f1bec8c4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetcursorname-function"></a>Функция SQLSetCursorName
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLSetCursorName** связывает имя курсора с активным оператором. Если приложение не вызывает **SQLSetCursorName**, драйвер создает имена курсоров, необходимые для обработки инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *CursorName*  
 [Вход] Имя курсора. Для эффективной обработки имя курсора не следует указывать все начальные и конечные пробелы в имени курсора, и если имя курсора включает идентификатор с разделителем, разделителя должна быть расположена в качестве первого символа в имени курсора.  
  
 *NameLength*  
 [Вход] Длина в символах **CursorName*.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetCursorName** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обработки* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLSetCursorName** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Имя курсора превысило максимальный предел, поэтому было использовано только максимальное разрешенное число знаков.|  
|24000|Недопустимое состояние курсора|Инструкции, соответствующий *StatementHandle* уже был в состоянии выполнения или курсор располагается.|  
|34000|Недопустимое имя курсора|Имя курсора, указанные в **CursorName* недопустим, так как оно превышает максимальную длину, в соответствии с определением драйвер или начиналась с «SQLCUR» или «SQL_CUR».|  
|3C000|Повторяющееся имя курсора|Имя курсора, указанные в **CursorName* уже существует.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *CursorName* является пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *StatementHandle*. Выполняется при этом функция aynchronous **SQLSetCursorName** была вызвана функция.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) аргумент *NameLength* было меньше, чем 0, но не равно SQL_NTS.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированного обновления и удаления инструкций (например, **обновление** *имя таблицы* ... **WHERE CURRENT OF** *имя курсора*). Дополнительные сведения см. в разделе [располагается обновление и удаление операторов](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Если приложение не вызывает **SQLSetCursorName** для определения имени курсора, при выполнении инструкции запроса, драйвер создает имя, которое начинается с буквы SQL_CUR и не превышает 18 символов.  
  
 Все имена курсоров в соединении, должны быть уникальными. Максимальная длина имени курсора определяется с помощью драйвера. Для максимальной совместимости рекомендуется ограничить что приложений имена курсоров, не более 18 символов. В ODBC 3 *.x*, если имя курсора является заключенный в кавычки идентификатор, он обрабатывается в режиме с учетом регистра и может содержать символы, что синтаксис SQL не позволяет рассматривал специально, таких как пробелы или зарезервированные ключевые слова. Если имя курсора должны обрабатываться в виде с учетом регистра, его должны передаваться как заключенный в кавычки идентификатор.  
  
 Задайте имя курсора, который задается явно или неявно остается до удаления инструкции, с которым он связан с помощью **SQLFreeHandle**. **SQLSetCursorName** можно вызвать, чтобы переименовать курсора в инструкции до тех пор, пока курсор находится в состоянии выделенный или подготовленной.  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение использует **SQLSetCursorName** для задания имени курсора для инструкции. Затем этот оператор используется для получения результатов из таблицы CUSTOMERS. Наконец выполняется позиционированное обновление, чтобы изменить номер телефона John Smith. Обратите внимание, что приложение использует другой инструкции дескрипторы для **ВЫБЕРИТЕ** и **обновление** инструкции.  
  
 Еще один пример кода см. в разделе [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```  
#define NAME_LEN 50  
#define PHONE_LEN 10  
  
SQLHSTMT     hstmtSelect,  
SQLHSTMT     hstmtUpdate;  
SQLRETURN    retcode;  
SQLHDBC      hdbc;  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   cbName, cbPhone;  
  
/* Allocate the statements and set the cursor name. */  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtSelect);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtUpdate);  
SQLSetCursorName(hstmtSelect, "C1", SQL_NTS);  
  
/* SELECT the result set and bind its columns to local buffers. */  
  
SQLExecDirect(hstmtSelect,  
      "SELECT NAME, PHONE FROM CUSTOMERS",  
      SQL_NTS);  
SQLBindCol(hstmtSelect, 1, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
SQLBindCol(hstmtSelect, 2, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);  
  
/* Read through the result set until the cursor is */  
/* positioned on the row for John Smith. */  
  
do  
 retcode = SQLFetch(hstmtSelect);  
while ((retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) &&  
   (strcmp(szName, "Smith, John") != 0));  
  
/* Perform a positioned update of John Smith's name. */  
  
if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
   SQLExecDirect(hstmtUpdate,  
   "UPDATE EMPLOYEE SET PHONE=\"2064890154\" WHERE CURRENT OF C1",  
   SQL_NTS);  
}  
```  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Выполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнения подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращает имя курсора|[Функция SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Параметр прокрутки параметры курсора|[Функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
