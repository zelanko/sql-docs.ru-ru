---
title: Функция SQLGetDescRec | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c737a9dfd6e7a33b5e160b3d952fac0b354148b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538193"
---
# <a name="sqlgetdescrec-function"></a>Функция SQLGetDescRec
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLGetDescRec** возвращает текущие параметры или значения нескольких полей в записи дескриптора. Поля, возвращаемые описывают имя, тип данных и хранение данных столбца или параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLGetDescRec(  
      SQLHDESC        DescriptorHandle,  
      SQLSMALLINT     RecNumber,  
      SQLCHAR *       Name,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLSMALLINT *   TypePtr,  
      SQLSMALLINT *   SubTypePtr,  
      SQLLEN *        LengthPtr,  
      SQLSMALLINT *   PrecisionPtr,  
      SQLSMALLINT *   ScalePtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *DescriptorHandle*  
 [Вход] Дескриптор.  
  
 *RecNumber*  
 [Вход] Указывает запись дескриптора, из которого приложение ищет сведения. Записи дескриптора нумеруются от 1, записей номером 0 является записи закладки. *RecNumber* аргумент должен быть меньше или равно значению SQL_DESC_COUNT. Если *RecNumber* меньше или равно SQL_DESC_COUNT, но строка не содержит данных для столбца или параметра, вызов **SQLGetDescRec** будет возвращать значения по умолчанию для поля. (Дополнительные сведения см. в разделе «Инициализация поля дескриптора» в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Name*  
 [Выход] Указатель на буфер, в которую будет возвращен поля SQL_DESC_NAME для записи дескриптора.  
  
 Если *имя* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее число символов (включая знак завершения null для символьных данных) для возврата в буфере, на которые указывают  *Имя*.  
  
 *BufferLength*  
 [Вход] Длина **имя* буфера в символах.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращен количество символов для данных, доступных для возврата в \* *имя* буфера, за исключением знака завершения null. Если количество символов было больше или равно *BufferLength*, данные в \* *имя* усекается до *BufferLength* минус длина знак завершения NULL и заканчивается нулевым байтом драйвером.  
  
 *TypePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение поле SQL_DESC_TYPE для записи дескриптора.  
  
 *SubTypePtr*  
 [Выход] Для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL это указатель на буфер, в которую будет возвращено значение SQL_DESC_DATETIME_INTERVAL_CODE поля.  
  
 *LengthPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение поля SQL_DESC_OCTET_LENGTH для записи дескриптора.  
  
 *PrecisionPtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение SQL_DESC_PRECISION поля для записи дескриптора.  
  
 *ScalePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение поля SQL_DESC_SCALE для записи дескриптора.  
  
 *NullablePtr*  
 [Выход] Указатель на буфер, в которую будет возвращено значение поля SQL_DESC_NULLABLE для записи дескриптора.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA, or SQL_INVALID_HANDLE.  
  
 Будет возвращено значение SQL_NO_DATA, если *RecNumber* больше, чем текущее количество записей дескриптора.  
  
 Будет возвращено значение SQL_NO_DATA, если *DescriptorHandle* является дескриптором IRD и инструкция находится в состоянии подготовленных или выполненных, но возникла без открытого курсора, связанные с ней.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetDescRec** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обрабатывать* из *DescriptorHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые при помощи **SQLGetDescRec** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Усечение данных строки справа|Буфер \* *имя* не был достаточно большим, чтобы вернуть весь дескриптор поля. Таким образом поля были усечены. Длина поля дескриптора неусеченный возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|*FieldIdentifier* аргумент был поле записи, *RecNumber* аргумент присвоено значение 0 и *DescriptorHandle* аргумент был дескриптор IPD.<br /><br /> (DM) *RecNumber* аргумент присвоено значение 0, и атрибут инструкции SQL_ATTR_USE_BOOKMARKS было присвоено SQL_UB_OFF и *DescriptorHandle* аргумент был дескриптор IRD.<br /><br /> *RecNumber* аргумента меньше 0.|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, которая необходима для поддержки выполнения или завершения функции.|  
|HY007|Связанная инструкция не подготовлена|*DescriptorHandle* был связан с IRD, а соответствующий оператор дескриптор не был в состоянии подготовленных или выполненных.|  
|HY010|Ошибка последовательности функций|(DM) *DescriptorHandle* был связан с параметром *StatementHandle* которого асинхронно выполняемой функции (не вот) был вызван и еще выполнялась при вызове этой функции.<br /><br /> (DM) *DescriptorHandle* был связан с параметром *StatementHandle* для которого **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, или **SQLSetPos** был вызван и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *DescriptorHandle*. Если по-прежнему выполнении асинхронной функции **SQLGetDescRec** был вызван.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *DescriptorHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Приложение может вызвать **SQLGetDescRec** для извлечения значений из следующих полей дескриптора для одного столбца или параметра:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** не получить значения для поля заголовка.  
  
 Приложения можно предотвратить возвращение параметр поля, задав аргумент, который соответствует полю в пустой указатель.  
  
 Если приложение вызывает **SQLGetDescRec** для получения значения поля, не определено для конкретного дескриптора типа, функция возвращает значение SQL_SUCCESS, но не определено значение, возвращаемое для поля. Например, вызов **SQLGetDescRec** для поля SQL_DESC_NAME или SQL_DESC_NULLABLE APD или Отменить возвращает SQL_SUCCESS, но неопределенное значение для поля.  
  
 Если приложение вызывает **SQLGetDescRec** для получения значения поля, которое определено для конкретного дескриптора типа, но нет значения по умолчанию и еще не был установлен, функция возвращает значение SQL_SUCCESS, но возвращаемое значение для поле не определено. Дополнительные сведения см. в разделе «Инициализация поля дескриптора» в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Значения полей также можно получить по отдельности с помощью вызова **SQLGetDescField**. Описание поля заголовка дескриптора или записи, см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Дополнительные сведения о дескрипторах, см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка столбца|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Привязка параметра|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Получение поля дескриптора|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
