---
title: Функция SQLSetCursorName | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a976d7caad790c80b15c17d65686ee1f6308f415
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65536750"
---
# <a name="sqlsetcursorname-function"></a>Функция SQLSetCursorName
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: ISO-92  
  
 **Сводка**  
 **SQLSetCursorName** связывает имя курсора с активным оператором. Если приложение не вызывает **SQLSetCursorName**, драйвер создает имена курсоров, необходимые для обработки инструкции SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Аргументы  
 *StatementHandle*  
 [Вход] Дескриптор инструкции.  
  
 *cursorName*  
 [Вход] Имя курсора. Для эффективной обработки имя курсора не следует включать любые начальные или конечные пробелы в имени курсора, и если имя курсора включает идентификатор с разделителем, разделитель должен быть размещен в качестве первого символа в имени курсора.  
  
 *NameLength*  
 [Вход] Длина в символах **CursorName*.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetCursorName** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из Значение SQL_HANDLE_STMT и *обрабатывать* из *StatementHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLSetCursorName** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Имя курсора превысило максимальный предел, поэтому было использовано только максимальное допустимое количество символов.|  
|24000|Недопустимое состояние курсора|Инструкции, соответствующий *StatementHandle* уже был в состоянии выполнении или положение курсора.|  
|34000|Недопустимое имя курсора|Имя курсора, указанные в **CursorName* недопустим, так как он превышена максимальная длина в соответствии с определением драйвер или начиналась с «SQLCUR» или «SQL_CUR.»|  
|3C000|Повторяющееся имя курсора|Имя курсора, указанные в **CursorName* уже существует.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *CursorName* был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *StatementHandle*. Выполняется при данная функция aynchronous **SQLSetCursorName** была вызвана функция.<br /><br /> (DM) был вызван асинхронно выполняемой функции для *StatementHandle* и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) аргумент *NameLength* меньше, чем 0, но не равно SQL_NTS.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *StatementHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированного обновления и удаления инструкций (например, **обновление** _имя таблицы_ ... **WHERE CURRENT OF** _имя курсора_). Дополнительные сведения см. в разделе [расположен обновления и удаления инструкций](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Если приложение не вызывает **SQLSetCursorName** для определения имени курсора, при выполнении инструкции запроса, драйвер выдает имя, которое начинается с букв SQL_CUR и не превышает 18 символов.  
  
 Все имена курсоров в соединении, должны быть уникальными. Максимальная длина имени курсора определяется с помощью драйвера. Для максимальной совместимости рекомендуется, чтобы приложения ограничивал имена курсоров для не более 18 символов. В ODBC 3 *.x*, если имя курсора является заключенный в кавычки идентификатор, он обрабатывается регистра и может содержать символы, синтаксис SQL не позволяет или будет рассматривать специально, такие как пробелы или зарезервированные ключевые слова. Если имя курсора должно рассматриваться в регистр, он должны передаваться как заключенный в кавычки идентификатор.  
  
 Задайте имя курсора, который имеет значение либо явно или неявно остается до удаления инструкции, с которым он связан, с помощью **SQLFreeHandle**. **SQLSetCursorName** можно вызвать, чтобы переименовать курсора в инструкции до тех пор, пока курсор находится в состоянии выделением или подготовленной.  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение использует **SQLSetCursorName** для задания имени курсора для инструкции. Затем этот оператор используется для получения результатов из таблицы CUSTOMERS. Наконец выполняется позиционированное обновление, чтобы изменить номер телефона John Smith. Обратите внимание на то, что приложение использует маркеры другой инструкции для **ВЫБЕРИТЕ** и **обновления** инструкций.  
  
 Другой пример кода см. в разделе [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```cpp  
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
|Выполнении подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращает имя курсора|[Функция SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Настройка параметров прокручивание курсора|[Функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
