---
title: Функция S'LSetCursorName (англ.) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a3bcd07a39401d49be04d141e50c671179efb16
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287344"
---
# <a name="sqlsetcursorname-function"></a>Функция SQLSetCursorName
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 1.0: ISO 92  
  
 **Сводка**  
 **SLSetCursorName** связывает имя курсора с активным заявлением. Если приложение не вызывает **s'LSetCursorName,** драйвер генерирует имена курсоров по мере необходимости для обработки оператора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>Аргументы  
 *Обработка заявления*  
 (Вход) Ручка оператора.  
  
 *КурсорНамь*  
 (Вход) Имя курсора. Для эффективной обработки имя курсора не должно включать в имя курсора какие-либо передние или задние пространства, и если имя курсора содержит делимитированный идентификатор, то делимитер должен быть позиционирован как первый символ в имени курсора.  
  
 *NameLength*  
 (Вход) Длина в символах :*CursorName*.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LSetCursorName** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью handleType* SQL_HANDLE_STMT и *ручки* *выписки.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LSetCursorName,** и приведены в изъяны каждое из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Имя курсора превысило максимальный предел, поэтому было использовано только максимально допустимое количество символов.|  
|24 000|Недопустимое состояние курсора|Заявление, соответствующее *StatementHandle,* уже находилось в состоянии, выполненном или расположенном курсором.|  
|34000|Недопустимое имя курсора|Имя курсора, указанное в z*CursorName,* было недействительным, поскольку оно превышало максимальную длину, установленную водителем, или начиналось с «S'LCUR» или «SQL_CUR».|  
|3C000|Двойное имя курсора|Имя курсора, указанное в q*CursorName,* уже существует.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недействительное использование нулевой указатель|(DM) Аргумент *CursorName* был нулевой указатель.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *StatementHandle.* Эта аинхронная функция по-прежнему исполнялась, когда была вызвана функция **S'LSetCursorName.**<br /><br /> (DM) Асинхронно выполнение функции был вызван для *StatementHandle* и по-прежнему выполнения, когда эта функция была вызвана.<br /><br /> (DM) **S'LExecute**, **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван для *statementHandle* и вернулся SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|(DM) Аргумент *NameLength* был меньше, чем 0, но не равна SQL_NTS.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *StatementHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Имена курсоров используются только в позиционированных обновлениях и удалениях (например, _название таблицы_ **UPDATE** ... **ГДЕ CURRENT Of** _курсор-имя_). Для получения дополнительной [информации см.](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md) Если приложение не вызывает **s'LSetCursorName** для определения имени курсора, при выполнении оператора запроса драйвер генерирует имя, которое начинается с букв SQL_CUR и не превышает 18 символов в длину.  
  
 Все имена курсоров в рамках соединения должны быть уникальными. Максимальная длина имени курсора определяется водителем. Для максимальной совместимости рекомендуется ограничить имена курсоров не более чем 18 символами. В ODBC 3 *.x*, если имя курсора является цитируемым идентификатором, оно рассматривается в случае чувствительной образом, и он может содержать символы, что синтаксис S'L не позволит или будет рассматривать специально, такие как пробелы или зарезервированные ключевые слова. Если имя курсора должно рассматриваться в чувствительном к делу порядке, оно должно быть передано в качестве цитируемого идентификатора.  
  
 Имя курсора, которое устанавливается либо явно, либо косвенно, остается установленным до тех пор, пока не будет удалено заявление, с которым оно связано, с помощью **S'LFreeHandle.** **SLSetCursorName** можно вызвать для переименования курсора в выписке, пока курсор находится в выделенном или подготовленном состоянии.  
  
## <a name="code-example"></a>Пример кода  
 В следующем примере приложение использует **sLSetCursorName** для установки имени курсора для оператора. Затем он использует это заявление для получения результатов из таблицы CUSTOMERS. Наконец, он выполняет позиционированное обновление, чтобы изменить номер телефона Джона Смита. Обратите внимание, что приложение использует различные ручки оператора для заявлений **SELECT** и **UPDATE.**  
  
 Для другого примера кода [см.](../../../odbc/reference/syntax/sqlsetpos-function.md)  
  
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
|Выполнение оператора S'L|[Функция SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|Выполнение подготовленного заявления по S'L|[Функция «СЗЛВы»](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|Возвращение имени курсора|[Функция SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|Настройка параметров прокрутки курсора|[Функция SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
