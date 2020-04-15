---
title: Функция S'LNativeSql Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9666bc767affb3b6bb624c416614079193d4b921
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304725"
---
# <a name="sqlnativesql-function"></a>Функция SQLNativeSql
**Соответствия**  
 Версия Введена: Соответствие стандартам ODBC 1.0: ODBC  
  
 **Сводка**  
 **SLNativeSql** возвращает строку S'L в качестве измененной драйвером. **СЗЛНатиЯКзл** не выполняет выписку по S'L.  
  
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
 *ПодключениеРучка*  
 [Input] Дескриптор подключения  
  
 *InStatementТекст*  
 (Вход) Текстовая строка S'L, которая будет переведена.  
  
 *TextLength1*  
 (Вход) Длина в символах текстовой строки*InStatementText.*  
  
 *OutStatementТекст*  
 (Выход) Указатель на буфер, в котором можно вернуть переведенную строку S'L.  
  
 Если *OutStatementText* является NULL, *TextLength2Ptr* по-прежнему возвращает общее количество символов (за исключением символа с нулевым прекращением для данных символов), доступных для возврата в буфере, на который указывает *OutStatementText.*  
  
 *BufferLength*  
 (Вход) Количество символов в \*буфере *OutStatementText.* Если значение, возвращенное в * \*InStatementText,* является строкой Unicode (при вызове **S'LNativeSllW),** аргумент *BufferLength* должен быть четным числом.  
  
 *TextLength2Ptr*  
 (Выход) Указатель на буфер, в котором можно вернуть общее количество символов (за \*исключением нулевого прекращения), доступных для возврата в *OutStatementText.* Если количество символов, доступных для возврата, больше или равно *строке BufferLength,* переведенная строка S'L в \* *OutStatementText* усечена до *BufferLength* минус длина персонажа с нулевым прекращением.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LNativeSl** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью handleType* of SQL_HANDLE_DBC и *ручки* *ConnectionHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LNativeSl,** и приведены в контексте этой функции. нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|Буфер \* *OutStatementText* не был достаточно большим, чтобы вернуть всю строку S'L, поэтому строка S'L была усечена. Длина непросаженной строки S'L возвращается в*textLength2Ptr*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08003|Подключение не открыто|*ConnectionHandle* не находился в подключенном состоянии.|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|22007|Недействительный формат дата-времени|**InStatementText* содержал оговорку о побеге с недействительной датой, временем или значением метки времени.|  
|24 000|Недопустимое состояние курсора|Курсор, упомянутый в заявлении, был расположен до начала набора результатов или после окончания набора результатов. Эта ошибка не может быть возвращена драйвером, осуществляемым с реализацией нативного курсора DBMS.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY009|Недействительное использование нулевой указатель|(DM)*- InStatementText* был нулевым указателем.|  
|HY010|Ошибка последовательности функций|(DM) Асинхронно выполнение функции был вызван для *ConnectionHandle* и по-прежнему выполнения, когда эта функция была вызвана.|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY090|Недействительная длина строки или буфера|(DM) Аргумент *TextLength1* был меньше, чем 0, но не равен SQL_NTS.|  
|||(DM) Аргумент *BufferLength* был меньше, чем 0 и аргумент *OutStatementText* не был нулевым указателем.|  
|HY109|Положение недействительного курсора|Текущий ряд курсора был удален или не был извлечен. Эта ошибка не может быть возвращена драйвером, осуществляемым с реализацией нативного курсора DBMS.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *ConnectionHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Ниже приведены примеры того, что **S'LNativeSsl** может вернуться на следующую строку ввода S'L, содержащую функцию масштабирования CONVERT. Предположим, что столбец empid имеет тип INTEGER в источнике данных:  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Драйвер для сервера Microsoft S'L может вернуть следующую переведенную строку S'L:  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 Драйвер для ORACLE Server может вернуть следующую переведенную строку S'L:  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Драйвер для Ingres может вернуть следующую переведенную строку S'L:  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 Для получения дополнительной информации [Prepared Execution](../../../odbc/reference/develop-app/prepared-execution-odbc.md) [см.](../../../odbc/reference/develop-app/direct-execution-odbc.md)  
  
## <a name="related-functions"></a>Связанные функции  
 Отсутствует.  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
