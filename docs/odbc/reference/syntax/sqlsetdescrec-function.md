---
title: Функция SQLSetDescRec | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetDescRec
helpviewer_keywords:
- SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cee1f41c76a79edf1d78d8b94b07107c3c2771e0
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793163"
---
# <a name="sqlsetdescrec-function"></a>Функция SQLSetDescRec
**Соответствие стандартам**  
 Представленные версии: ODBC 3.0 стандартов соответствия: ISO-92  
  
 **Сводка**  
 **SQLSetDescRec** функция задает несколько поля дескриптора, которые определяют тип данных, а буфер к столбца или параметра данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLSetDescRec(  
      SQLHDESC      DescriptorHandle,  
      SQLSMALLINT   RecNumber,  
      SQLSMALLINT   Type,  
      SQLSMALLINT   SubType,  
      SQLLEN        Length,  
      SQLSMALLINT   Precision,  
      SQLSMALLINT   Scale,  
      SQLPOINTER    DataPtr,  
      SQLLEN *      StringLengthPtr,  
      SQLLEN *      IndicatorPtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *DescriptorHandle*  
 [Вход] Дескриптор. Это не должно быть дескриптор IRD.  
  
 *RecNumber*  
 [Вход] Указывает запись дескриптора, который содержит поля, чтобы задать. Записи дескриптора нумеруются от 0, записи номером 0 является записи закладки. Этот аргумент должен быть равным или больше 0. Если *RecNumber* больше, чем значение SQL_DESC_COUNT, изменен на значение SQL_DESC_COUNTis *RecNumber*.  
  
 *Тип*  
 [Вход] Значение, которое требуется задать поле SQL_DESC_TYPE для записи дескриптора.  
  
 *Подтип*  
 [Вход] Для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL это значение, которое требуется задать поле SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *Длина*  
 [Вход] Значение, которое требуется задать поле SQL_DESC_OCTET_LENGTH для записи дескриптора.  
  
 *Точность*  
 [Вход] Значение, которое требуется задать поле SQL_DESC_PRECISION для записи дескриптора.  
  
 *Масштаб*  
 [Вход] Значение, которое требуется задать поле SQL_DESC_SCALE для записи дескриптора.  
  
 *DataPtr*  
 [Отложенные входные или выходные данные] Значение, которое требуется задать поле для записи дескриптора SQL_DESC_DATA_PTR. *DataPtr* можно присвоить указатель null.  
  
 *DataPtr* аргумент может быть присвоено на указатель null значение SQL_DESC_DATA_PTR поле является пустым указателем. Если дескриптор в *DescriptorHandle* аргумент связан с Отменить, это отменяется привязка значения столбца.  
  
 *StringLengthPtr*  
 [Отложенные входные или выходные данные] Значение, которое требуется задать поле SQL_DESC_OCTET_LENGTH_PTR для записи дескриптора. *StringLengthPtr* можно присвоить указатель null присвоено поле SQL_DESC_OCTET_LENGTH_PTR значение является пустым указателем.  
  
 *IndicatorPtr*  
 [Отложенные входные или выходные данные] Значение, которое требуется задать поле SQL_DESC_INDICATOR_PTR для записи дескриптора. *IndicatorPtr* можно присвоить указатель null присвоено поле SQL_DESC_INDICATOR_PTR является пустым указателем.  
  
## <a name="returns"></a>Возвращает  
 Значение SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetDescRec** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, а связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обрабатывать* из *DescriptorHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLSetDescRec** и объясняется каждый из них в контексте этой функции; описания SQLSTATE, возвращаемых диспетчером драйверов предшествует обозначение «(DM)». Возвращается связанный с каждого значения SQLSTATE значение SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Специфические для драйвера информационное сообщение. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|*RecNumber* аргумент присвоено значение 0 и *DescriptorHandle* ссылается на дескриптор IPD.<br /><br /> *RecNumber* аргумента меньше 0.<br /><br /> *RecNumber* аргумент поданных единиц превысил максимальное количество столбцов или параметров, поддерживаемых источником данных, и *DescriptorHandle* аргумент было APD, IPD или Отменить.<br /><br /> *RecNumber* аргумент, равное 0 и *DescriptorHandle* аргумент называется неявно выделенные APD. (Эта ошибка возникает с дескриптор явно выделенные приложений так, как ничего не известно дескриптор явно выделенные приложений может быть APD и Отменить до выполнения.)|  
|08S01|Отказ канала связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет конкретных SQLSTATE и SQLSTATE не зависящие от реализации, который был определен. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйвер не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) *DescriptorHandle* был связан с параметром *StatementHandle* которого асинхронно выполняемой функции (не вот) был вызван и еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* с помощью которого *DescriptorHandle* был связанные и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров данных времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, связанный с *DescriptorHandle*. Выполняется при данная функция aynchronous **SQLSetDescRec** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *DescriptorHandle* и возвращается SQL_PARAM_DATA_AVAILABLE. Прежде чем данные были получены для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как базовые объекты памяти оказываются недоступны, возможно из-за нехватки памяти.|  
|HY016|Не удается изменить дескриптор строки реализации|*DescriptorHandle* аргумент был связан с IRD.|  
|HY021|Несовместимые сведения дескриптора|*Типа* поля или любое другое поле, связанное с этим SQL_DESC_TYPE в дескрипторе, не был допустимым или регулярный характер.<br /><br /> Сведения о дескрипторе проверяется в ходе проверки согласованности не согласован. (См. в разделе «Проверка целостности» далее в этом разделе.)|  
|HY090|Недопустимая длина строки или буфера|(DM) драйвер был ODBC *2.x* драйвера, дескриптор был Отменить *ColumnNumber* аргумент имеет значение 0, а значение, указанное для аргумента *BufferLength* был не равно 4.|  
|HY117|Подключение будет приостановлена из-за состояние транзакции неизвестно. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки, см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания подключения истекло раньше, чем ответил на запрос источника данных. Период времени ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *DescriptorHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Приложение может вызвать **SQLSetDescRec** задать следующие поля для одного столбца или параметра:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Если в вызове **SQLSetDescRec** содержимое запись дескриптора, определяемый в случае сбоя *RecNumber* аргумент не определены.  
  
 При привязке столбца или параметра, **SQLSetDescRec** позволяет изменять несколько полей, влияющие на привязку без вызова **SQLBindCol** или **SQLBindParameter** или несколько обращений к **SQLSetDescField**. **SQLSetDescRec** можно установить поля на дескриптор, который в настоящее время не связанные с инструкцией. Обратите внимание, что **SQLBindParameter** задает больше полей, чем **SQLSetDescRec**, можно установить поля в APD и IPD в одном вызове и не требует дескриптора.  
  
> [!NOTE]  
>  Атрибут инструкции SQL_ATTR_USE_BOOKMARKS всегда должны устанавливаться перед вызовом **SQLSetDescRec** с *RecNumber* аргумент 0, чтобы задать поля закладки. Хотя это не обязательно, настоятельно рекомендуется.  
  
## <a name="consistency-checks"></a>Проверка согласованности  
 Проверка согласованности выполняется с помощью драйвера автоматически каждый раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD. Если поля не согласуется с другими полями **SQLSetDescRec** вернет SQLSTATE HY021 (несовместимые сведения дескриптора).  
  
 Всякий раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD, драйвер проверяет, что значение поля SQL_DESC_TYPE и значения, применяемые к этому полю SQL_DESC_TYPE правильны и согласуются. Такая проверка всегда является выполняемой при **SQLBindParameter** или **SQLBindCol** вызывается или когда **SQLSetDescRec** вызывается для APD, Отменить или IPD. Проверка согласованности включает в себя следующие проверки в поля дескриптора:  
  
-   Поле SQL_DESC_TYPE должно быть одно из допустимых C ODBC или типы SQL или типом специфические для драйвера SQL. Поле SQL_DESC_CONCISE_TYPE должно быть одно из допустимых типов ODBC C или SQL или специфические для драйвера C или SQL тип, включая краткие типы даты и времени и интервала.  
  
-   Если поле записи SQL_DESC_TYPE равно SQL_DATETIME или SQL_INTERVAL, поле SQL_DESC_DATETIME_INTERVAL_CODE должно быть одно из допустимые дату и время или интервал коды. (См. в описании поля SQL_DESC_DATETIME_INTERVAL_CODE в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Если поле SQL_DESC_TYPE указывает числового типа, поля SQL_DESC_PRECISION и SQL_DESC_SCALE проверяются был допустимым.  
  
-   Если поле SQL_DESC_CONCISE_TYPE является типом данных времени или метки времени, интервал тип компонента секунд или один из типов данных интервала с компонентом времени, проверяется поле SQL_DESC_PRECISION быть допустимым точностью.  
  
-   Если SQL_DESC_CONCISE_TYPE является типом данных интервал, поле SQL_DESC_DATETIME_INTERVAL_PRECISION будет проверена начальным значением точности допустимый интервал.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано; Тем не менее приложение может сделать это для принудительно выполнить проверку согласованности IPD полей. Невозможно выполнить проверку согласованности в IRD. Значение, которое присвоено поле SQL_DESC_DATA_PTR IPD фактически не сохраняются и не удается получить с помощью вызова **SQLGetDescField** или **SQLGetDescRec**; этот параметр устанавливается только для принудительного Проверка согласованности.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка столбца|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Привязка параметра|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Получение одного дескриптора поля|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Установка полей дескриптора единый|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
