---
title: Функция SQLNativeSql | Документы Microsoft
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
ms.topic: article
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
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d0a18b6575d403c44fb8aa546a4ce90d3a99e6b5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlnativesql-function"></a>Функция SQLNativeSql
**Соответствия**  
 Появился в версии: Полное соответствие стандартам 1.0 ODBC: ODBC  
  
 **Сводка**  
 **SQLNativeSql** возвращает строку SQL измененного драйвера. **SQLNativeSql** не выполняет инструкцию SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Вход] Текстовая строка SQL нужно перевести.  
  
 *TextLength1*  
 [Вход] Длина в символах **InStatementText* текстовую строку.  
  
 *OutStatementText*  
 [Выход] Указатель на буфер, в котором для возврата переведенных строк SQL.  
  
 Если *OutStatementText* имеет значение NULL, *TextLength2Ptr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфер Указывает *OutStatementText*.  
  
 *BufferLength*  
 [Вход] Число символов в \* *OutStatementText* буфера. Если возвращаемое значение в  *\*InStatementText* строка в Юникоде (при вызове **SQLNativeSqlW**), *BufferLength* аргумент должен быть четным числом.  
  
 *TextLength2Ptr*  
 [Выход] Указатель на буфер, в который возвращается общее число символов (за исключением конечное значение null), доступных для возврата в \* *OutStatementText*. Если количество символов вернуть больше или равно *BufferLength*, преобразовать строку SQL в \* *OutStatementText* усекается до  *BufferLength* за вычетом длины символ конечное значение null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLNativeSql** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* установленным в значение sql_handle_stmt и *обработки* из *ConnectionHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLNativeSql** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Буфер \* *OutStatementText* не был достаточно велик, чтобы вернуть всю строку SQL, поэтому SQL строка была усечена. Длина строки неусеченный SQL возвращается в **TextLength2Ptr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|08003|Соединение не открыто|*ConnectionHandle* не находился в подключенном состоянии.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|22007|Формат недопустимые даты и времени|**InStatementText* содержится предложение escape с недопустимым значением даты, времени или отметки времени.|  
|24000|Недопустимое состояние курсора|Курсор в инструкции называется был установлен перед началом результирующего набора, или в конце результирующего набора. Эта ошибка не могут быть возвращены драйвером, имеющий собственную реализацию курсора СУБД.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недопустимое использование пустого указателя|(DM) **InStatementText* является пустым указателем.|  
|HY010|Ошибка последовательности функций|(DM) был вызван асинхронно выполняемой функции для *ConnectionHandle* и все еще выполняется, при вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) аргумент *TextLength1* было меньше, чем 0, но не равно SQL_NTS.|  
|||(DM) аргумент *BufferLength* был меньше 0 и аргумента *OutStatementText* не является пустым указателем.|  
|HY109|Недопустимое положение курсора|Текущей строки курсора была удалена или не была получена. Эта ошибка не могут быть возвращены драйвером, имеющий собственную реализацию курсора СУБД.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *ConnectionHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Ниже приведены примеры того, что **SQLNativeSql** может возвращать следующие входной строки SQL, содержащий скалярные функции CONVERT. Предположим, что empid столбец имеет тип INTEGER в источнике данных:  
  
```  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Драйвер для Microsoft SQL Server может возвращать следующие переведенных строк SQL:  
  
```  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Драйвер для ORACLE Server может возвращать следующие переведенных строк SQL:  
  
```  
SELECT to_number (empid) FROM employee  
```  
  
 Драйвер для Ingres могут возвращать следующие переведенных строк SQL:  
  
```  
SELECT int2 (empid) FROM employee  
```  
  
 Дополнительные сведения см. в разделе [прямое выполнение](../../../odbc/reference/develop-app/direct-execution-odbc.md) и [подготовленных](../../../odbc/reference/develop-app/prepared-execution-odbc.md).  
  
## <a name="related-functions"></a>Связанные функции  
 Нет.  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
