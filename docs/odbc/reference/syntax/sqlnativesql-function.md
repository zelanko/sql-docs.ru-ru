---
title: Функция SQLNativeSql | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNativeSql
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNativeSql
helpviewer_keywords:
- SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9f58d262f133fc242592e62e0bb5a4152877adf6
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2019
ms.locfileid: "65536533"
---
# <a name="sqlnativesql-function"></a>Функция SQLNativeSql
**Соответствие стандартам**  
 Представленные версии: Соответствие стандартам 1.0 ODBC: интерфейс ODBC  
  
 **Сводка**  
 **SQLNativeSql** возвращает строку SQL, как измененный с помощью драйвера. **SQLNativeSql** не выполняет инструкцию SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *ConnectionHandle*  
 [Вход] Дескриптор соединения.  
  
 *InStatementText*  
 [Вход] Текстовая строка SQL для перевода.  
  
 *TextLength1*  
 [Вход] Длина в символах **InStatementText* текстовую строку.  
  
 *OutStatementText*  
 [Выход] Указатель на буфер, в котором для возврата переведенных строк SQL.  
  
 Если *OutStatementText* имеет значение NULL, *TextLength2Ptr* по-прежнему возвращает общее число символов (включая знак завершения null для символьных данных) для возврата в буфере Указывает *OutStatementText*.  
  
 *BufferLength*  
 [Вход] Число символов в \* *OutStatementText* буфера. Если возвращаемое значение в  *\*InStatementText* строка в Юникоде (при вызове **SQLNativeSqlW**), *BufferLength* аргумент должен быть четным числом.  
  
 *TextLength2Ptr*  
 [Выход] Указатель на буфер, в которую будет возвращено общее число символов (исключая конечное значение null), доступных для возврата в \* *OutStatementText*. Если количество символов, доступных для возврата больше или равно *BufferLength*, преобразовать строку SQL в \* *OutStatementText* усекается до  *BufferLength* минус длина знак завершения null.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLNativeSql** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, можно получить путем вызова связанного значения SQLSTATE **SQLGetDiagRec** с *HandleType* из SQL_HANDLE_DBC и *обрабатывать* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLNativeSql** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Буфер \* *OutStatementText* не был достаточно велик для того, чтобы вернуть всю строку SQL, поэтому SQL строка была усечена. Длина неусеченный строки SQL возвращается в **TextLength2Ptr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|*ConnectionHandle* не находился в подключенном состоянии.|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|22007|Формат недопустимые даты и времени|**InStatementText* содержится предложение escape с недопустимым значением даты, времени или метки времени.|  
|24000|Недопустимое состояние курсора|Курсор в заявлении был установлен перед началом результирующего набора или в конце результирующего набора. Эта ошибка не могут быть возвращены драйвером, наличие собственную реализацию курсора СУБД.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недопустимое использование пустого указателя|(DM) **InStatementText* был пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для *ConnectionHandle* и еще выполнялась при вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) аргумент *TextLength1* меньше, чем 0, но не равно SQL_NTS.|  
|||(DM) аргумент *BufferLength* был меньше 0 и аргумент *OutStatementText* не был пустым указателем.|  
|HY109|Недопустимое положение курсора.|Текущей строки курсора была удалена или не была получена. Эта ошибка не могут быть возвращены драйвером, наличие собственную реализацию курсора СУБД.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *ConnectionHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Ниже приведены примеры того, что **SQLNativeSql** могут возвращать для следующих входная строка SQL, содержащая скалярной функции CONVERT. Предположим, что empid столбец имеет тип INTEGER в источнике данных:  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Драйвер Microsoft SQL Server может возвращать следующие переведенная строка SQL:  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Драйвер ORACLE Server может возвращать следующие переведенная строка SQL:  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Драйвер Ingres могут возвращать следующие переведенная строка SQL:  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Дополнительные сведения см. в разделе [прямое выполнение](../../../odbc/reference/develop-app/direct-execution-odbc.md) и [подготовленных](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Нет.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
