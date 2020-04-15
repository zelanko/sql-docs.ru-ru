---
title: Функция S'LGetDescrecRec Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 87d7b971b379f19f8451e924932a5e699e9b9983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285489"
---
# <a name="sqlgetdescrec-function"></a>Функция SQLGetDescRec
**Соответствия**  
 Представлена версия: Соответствие стандартам ODBC 3.0: ISO 92  
  
 **Сводка**  
 **S'LGetDescCRec** возвращает текущие параметры или значения нескольких полей записи дескриптора. Возвращающиеся поля описывают имя, тип данных и хранение данных столбца или параметров.  
  
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
 (Вход) Ручка дескриптора.  
  
 *RecNumber*  
 (Вход) Указывает запись дескриптора, с которой приложение ищет информацию. Записи дескриптора пронумероированы из 1, при этом запись закладки является рекордным номером. Аргумент *RecNumber* должен быть меньше или равен стоимости SQL_DESC_COUNT. Если *RecNumber* меньше или равен SQL_DESC_COUNT но строка не содержит данных для столбца или параметра, вызов в **S'LGetDescRec** вернет значения полей по умолчанию. (Для получения дополнительной информации, см. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 *имя*;  
 (Выход) Указатель на буфер, в котором можно вернуть поле SQL_DESC_NAME для записи дескриптора.  
  
 Если *имя* NULL, *StringLengthPtr* по-прежнему возвращает общее количество символов (за исключением символа с нулевым прекращением для данных символов), доступного для возврата в буфере, на который указывает *Name.*  
  
 *BufferLength*  
 (Вход) Длина буфера*имен* в символах.  
  
 *СтрунныйДлинПтр*  
 (Выход) Указатель на буфер, в котором можно вернуть количество символов данных, доступных для возврата в \*буфере *Имен,* исключая символ нулевого прекращения. Если количество символов было больше или равно *BufferLength* \*, данные в *имя* усечены до *BufferLength* минус длина символа с нулевым прекращением, и является недействительным водителем.  
  
 *TypePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение SQL_DESC_TYPE поле для дескриптора записи.  
  
 *SubTypePtr*  
 (Выход) Для записей, тип которых SQL_DATETIME или SQL_INTERVAL, это указатель на буфер, в котором можно вернуть значение SQL_DESC_DATETIME_INTERVAL_CODE поля.  
  
 *ДлинаПтр*  
 (Выход) Указатель на буфер, в котором можно вернуть значение SQL_DESC_OCTET_LENGTH поля для записи дескриптора.  
  
 *PrecisionPtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение SQL_DESC_PRECISION поля для записи дескриптора.  
  
 *ScalePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение SQL_DESC_SCALE поле для записи дескриптора.  
  
 *NullablePtr*  
 (Выход) Указатель на буфер, в котором можно вернуть значение SQL_DESC_NULLABLE поле для записи дескриптора.  
  
## <a name="returns"></a>Результаты  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_ERROR, SQL_NO_DATA или SQL_INVALID_HANDLE.  
  
 SQL_NO_DATA возвращается, если *RecNumber* больше, чем текущее количество записей дескриптора.  
  
 SQL_NO_DATA возвращается, если *DescriptorHandle* является iRD-ручкой и заявление находится в подготовленном или выполненном состоянии, но с ним не было связано открытое курсора.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **S'LGetDesccRec** возвращается SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное с этим значение S'LSTATE можно получить, позвонив по **телефону S'LGetDiagRec** с *помощью handleType* SQL_HANDLE_DESC и *ручки* *DescriptorHandle.* В следующей таблице перечислены значения S'LSTATE, обычно возвращаемые **S'LGetDescRec,** и разъясняется каждая из них в контексте этой функции; нотация "(DM)" предшествует описаниям S'LSTATEs, возвращенным менеджером драйвера. Код возврата, связанный с каждым значением S'LSTATE, является SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Error|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, конкретное для водителя. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, правые усеченные|\* *Название* буфера не было достаточно большим, чтобы вернуть все поле дескриптора. Поэтому поле было усечено. Длина непросеченного дескриптора возвращается в*строке StringLengthPtr*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07009|Недействительный индекс дескриптора|Аргумент *FieldIdentifier* был рекордным полем, аргумент *RecNumber* был установлен на 0, а аргумент *DescriptorHandle* был ручкой IPD.<br /><br /> (DM) Аргумент *RecNumber* был установлен на 0, и атрибут SQL_ATTR_USE_BOOKMARKS оператора был установлен на SQL_UB_OFF, и аргумент *DescriptorHandle* был ручкой IRD.<br /><br /> Аргумент *RecNumber* был меньше, чем 0.|  
|08S01|Сбой связи|Связь между драйвером и источником данных, к которому был подключен драйвер, не сработала до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, в соответствии с которой не было конкретного S'LSTATE и для которой не было определено конкретное осуществление СЗЛСТАТ. Сообщение об ошибке, возвращенное **S'LGetDiagRec** в * \*буфере MessageText,* описывает ошибку и ее причину.|  
|HY001|Ошибка распределения памяти|Водитель не смог выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY007|Связанное заявление не подготовлено|*DescriptorHandle* был связан с IRD, и связанная ручка оператора не находилась в подготовленном или выполненном состоянии.|  
|HY010|Ошибка последовательности функций|(DM) *DescriptorHandle* был связан с *statementHandle,* для которого была вызвана асинхронно исполнительная функция (не эта) и все еще исполнялась, когда эта функция была вызвана.<br /><br /> (DM) *DescriptorHandle* был связан с *выпиской,* для которой **s'L'LExecute,** **S'LExecDirect**, **S'LBulkOperations**, или **S'LSetPos** был вызван и возвращен SQL_NEED_DATA. Эта функция была вызвана до отправки данных для всех параметров или столбцов данных.<br /><br /> (DM) Асинхронно функция выполнения была вызвана для ручки соединения, которая связана с *DescriptorHandle.* Эта асинхронная функция по-прежнему исполнялась, когда был вызван **S'LGetDescCRec.**|  
|HY013|Ошибка управления памятью|Вызов функции не может быть обработан, поскольку основные объекты памяти не могут быть доступны, возможно, из-за низких условий памяти.|  
|HY117|Подключение приостанавливается из-за неизвестного состояния транзакции. Разрешены только отключить и прочитать только функции.|(DM) Для получения дополнительной информации о приостановленном состоянии, [см.](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|HYT01|Срок истечения времени подключения|Период тайм-аута соединения истек до того, как источник данных ответил на запрос. Период тайм-аута соединения устанавливается через **S'LSetConnectAttr,** SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) Драйвер, связанный с *DescriptorHandle,* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Приложение может вызвать **S'LGetDescCRec** для получения значений следующих полей дескриптора для одного столбца или параметра:  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (для записей, тип которых SQL_DATETIME или SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **S'LGetDescRec** не получает значения для полей заголовка.  
  
 Приложение может предотвратить возвращение настройки поля, установив аргумент, соответствующий поле, на нулевой указатель.  
  
 Когда приложение вызывает **S'LGetDesccRec** для получения значения поля, которое не определено для конкретного типа дескриптора, функция возвращается SQL_SUCCESS но значение, возвращенное для поля, не определено. Например, вызов **S'LGetDesccRec** для SQL_DESC_NAME или SQL_DESC_NULLABLE области APD или ARD вернет SQL_SUCCESS, но неопределенное значение для поля.  
  
 Когда приложение вызывает **S'LGetDesccRec** для получения значения поля, которое определено для конкретного типа дескриптора, но не имеет значения по умолчанию и еще не установлено, функция возвращается SQL_SUCCESS но значение, возвращенное для поля, не определено. Для получения более подробной информации, см. [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)  
  
 Значения полей также могут быть получены индивидуально по вызову в **S'LGetDescField.** Для описания полей в заголовке или записи [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)дескриптора см. Для получения дополнительной информации о [Descriptors](../../../odbc/reference/develop-app/descriptors.md)дескрипторах см.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Связывание столбца|[SQLBindCol, функция](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Связывание параметра|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Получение дескриптора поля|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Установка нескольких полей дескриптора|[Функция SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справка aPI ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
