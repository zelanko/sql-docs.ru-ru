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
ms.openlocfilehash: 842d21bc36b9360826b4b85aa7da2798782995c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68092991"
---
# <a name="sqlsetcursorname-function"></a>Функция SQLSetCursorName
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLSetCursorName** связывает имя курсора с активной инструкцией. Если приложение не вызывает **SQLSetCursorName**, драйвер создает имена курсоров, необходимые для обработки инструкций SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *курсорнаме*  
 Входной Имя курсора. Для эффективной обработки имя курсора не должно содержать начальные или конечные пробелы в имени курсора, а если имя курсора содержит идентификатор с разделителями, разделитель должен быть установлен в качестве первого символа в имени курсора.  
  
 *намеленгс*  
 Входной Длина в символах **курсорнаме*.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetCursorName** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLSetCursorName** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, усеченные справа|Длина имени курсора превысила максимальное значение, поэтому использовалось только максимально допустимое количество символов.|  
|24 000|Недопустимое состояние курсора|Инструкция, соответствующая *статеменсандле* , уже находится в выполненном или позиционированном состоянии.|  
|34000|Недопустимое имя курсора|Имя курсора, указанное в **курсорнаме* , недопустимо, так как оно превысило максимальную длину, определенную драйвером, или оно было запущено с "склкур" или "SQL_CUR".|  
|3C000|Повторяющееся имя курсора|Имя курсора, указанное в **курсорнаме* , уже существует.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недопустимое использование пустого указателя|(DM) аргумент *курсорнаме* был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта функция айнчронаус все еще выполнялась при вызове функции **SQLSetCursorName** .<br /><br /> (DM) была вызвана асинхронно исполняемая функция для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) аргумент *намеленгс* был меньше 0, но не равен SQL_NTS.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированных инструкциях UPDATE и Delete (например, **Обновление** _Table-name_ ... **Где текущее** _имя курсора_). Дополнительные сведения см. в разделе [позиционированные обновления и инструкции DELETE](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md). Если приложение не вызывает **SQLSetCursorName** для определения имени курсора, при выполнении инструкции запроса драйвер создает имя, которое начинается с букв SQL_CUR и не превышает 18 символов.  
  
 Все имена курсоров в соединении должны быть уникальными. Максимальная длина имени курсора определяется драйвером. Для обеспечения максимальной совместимости приложения рекомендуется, чтобы длина имен курсоров не превышала 18 символов. В ODBC 3 *. x*, если имя курсора представляет собой заключенный в кавычки идентификатор, оно обрабатывается с учетом регистра и может содержать символы, которые синтаксис SQL не разрешает или будет обрабатывать специально, например пустые или зарезервированные ключевые слова. Если имя курсора должно обрабатываться с учетом регистра, оно должно передаваться в виде заключенного в кавычки идентификатора.  
  
 Имя курсора, которое задается явно или неявно, остается установленным до тех пор, пока инструкция, с которой он связан, не будет удалена с помощью **SQLFreeHandle**. **SQLSetCursorName** можно вызвать для переименования курсора в инструкции, если курсор находится в выделенном или подготовленном состоянии.  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение использует **SQLSetCursorName** для задания имени курсора для инструкции. Затем она использует эту инструкцию для получения результатов из таблицы CUSTOMERs. Наконец, он выполняет позиционированное обновление, чтобы изменить номер телефона Джон Смит. Обратите внимание, что приложение использует разные дескрипторы операторов для инструкций **SELECT** и **Update** .  
  
 Еще один пример кода см. в разделе [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
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
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Исполнение инструкции SQL|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Исполнение подготовленной инструкции SQL|[Функция SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращение имени курсора|[Функция SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Задание параметров прокрутки курсора|[Функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
