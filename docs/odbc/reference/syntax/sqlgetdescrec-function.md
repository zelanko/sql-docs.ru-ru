---
title: Функция SQLGetDescRec | Документы Microsoft
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
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f38ea81cf7eac8d670548382d8ffb4c0b79d503b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlgetdescrec-function"></a>Функция SQLGetDescRec
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLGetDescRec** возвращает текущие параметры или значения нескольких полей в записи дескриптора. Полях, возвращаемых описывают имя, тип данных и хранения данных столбца или параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Вход] Указывает запись дескриптора, из которой приложение ищет сведения. Дескриптор записи нумеруются от 1, с номер записи 0 представляет записи закладки. *RecNumber* аргумент должен быть меньше или равно значению SQL_DESC_COUNT. Если *RecNumber* меньше или равно SQL_DESC_COUNT, но строки не содержит данных для столбца или параметра, вызов **SQLGetDescRec** будет возвращать значения по умолчанию для поля. (Дополнительные сведения см. в разделе «Инициализация поля дескриптора» в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
 *Название*  
 [Выход] Указатель на буфер, в которой возвращаются поля SQL_DESC_NAME записи в дескриптор.  
  
 Если *имя* имеет значение NULL, *StringLengthPtr* по-прежнему возвращает общее число символов (за исключением символа конечное значение null, символьные данные) для возврата в буфере, на который указывает  *Имя*.  
  
 *BufferLength*  
 [Вход] Длина **имя* буфера в символах.  
  
 *StringLengthPtr*  
 [Выход] Указатель на буфер, в который возвращается количество символов для данных, доступных для возврата в \* *имя* буфера, за исключением знака конечное значение null. Если количество символов, была больше или равно *BufferLength*, данные в \* *имя* усекается до *BufferLength* за вычетом длины знак завершения NULL и завершается нулевым байтом драйвером.  
  
 *TypePtr*  
 [Выход] Указатель на буфер, в котором для возвращения значения поле SQL_DESC_TYPE для записи дескриптора.  
  
 *SubTypePtr*  
 [Выход] Для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL это указатель на буфер, в котором для возвращения значения поля SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *LengthPtr*  
 [Выход] Указатель на буфер, в котором для возвращения значения поля SQL_DESC_OCTET_LENGTH записи в дескриптор.  
  
 *PrecisionPtr*  
 [Выход] Указатель на буфер, в котором для возвращения значения поля SQL_DESC_PRECISION записи в дескриптор.  
  
 *ScalePtr*  
 [Выход] Указатель на буфер, в котором для возвращения значения поля SQL_DESC_SCALE записи в дескриптор.  
  
 *NullablePtr*  
 [Выход] Указатель на буфер, в котором для возвращения значения поля SQL_DESC_NULLABLE записи в дескриптор.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA или SQL_INVALID_HANDLE.  
  
 Если возвращается значение SQL_NO_DATA *RecNumber* больше, чем текущее число записей дескриптора.  
  
 Если возвращается значение SQL_NO_DATA *DescriptorHandle* является дескриптором IRD и инструкция находится в состоянии подготовленных или выполненных, но был не открытый курсор, связанный с ним.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLGetDescRec** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обработки* из *DescriptorHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLGetDescRec** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|01004|Строка справа усечение данных|Буфер \* *имя* не достаточно для получения всей дескриптора поля. Таким образом поля были усечены. Длина поля дескриптора неусеченный возвращается в **StringLengthPtr*. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|*FieldIdentifier* аргумент был поле записи, *RecNumber* аргумент было задано значение 0 и *DescriptorHandle* аргумент был дескриптор IPD.<br /><br /> (DM) *RecNumber* аргумент имеет значение 0, и атрибут инструкции SQL_ATTR_USE_BOOKMARKS задано значение SQL_UB_OFF и *DescriptorHandle* аргумент был дескриптор IRD.<br /><br /> *RecNumber* аргумент был меньше 0.|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, которая необходима для поддержки выполнения или завершения функции.|  
|HY007|Нужная инструкция не подготовлена|*DescriptorHandle* был связан с IRD и дескриптор нужная инструкция не находилась в состоянии подготовленных или выполненных.|  
|HY010|Ошибка последовательности функций|(DM) *DescriptorHandle* была связана с *StatementHandle* для которой асинхронного выполнения функции, (не это один) был вызван и все еще выполняется, при вызове этой функции.<br /><br /> (DM) *DescriptorHandle* была связана с *StatementHandle* которого **SQLExecute**, **SQLExecDirect**,  **SQLBulkOperations**, или **SQLSetPos** был вызван и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *DescriptorHandle*. Выполняется при этом асинхронной функция **SQLGetDescRec** был вызван.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *DescriptorHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Приложение может вызвать **SQLGetDescRec** для извлечения значений из указанных ниже полей дескриптора для одного столбца или параметра:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (для записи, тип которого равно SQL_DATETIME или SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec** не извлекает значения для поля заголовка.  
  
 Приложение может предотвратить возвращение настройки «поле», задав аргумент, который соответствует поле на указатель null.  
  
 Если приложение вызывает **SQLGetDescRec** для получения значения поля, которое не определено для конкретного дескриптора типа, функция возвращает значение SQL_SUCCESS, но значение, возвращаемое в поле не определено. Например, вызов **SQLGetDescRec** для поля SQL_DESC_NAME или SQL_DESC_NULLABLE APD или Отменить возвращает SQL_SUCCESS, а неопределенное значение для поля.  
  
 Если приложение вызывает **SQLGetDescRec** для получения значения поля, которое определено для конкретного дескриптора типа, но нет значения по умолчанию и еще не был установлен, функция возвращает значение SQL_SUCCESS, но для возвращаемое значение поле не определено. Дополнительные сведения см. в разделе «Инициализация поля дескриптора» в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).  
  
 Значения полей, также можно получить по отдельности с помощью вызова **SQLGetDescField**. Описание поля заголовка дескриптора или записи, см. в разделе [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md). Дополнительные сведения о дескрипторах см. в разделе [дескрипторы](../../../odbc/reference/develop-app/descriptors.md).  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка столбца|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Привязка параметра|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Получение дескриптора поля|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Задание нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
