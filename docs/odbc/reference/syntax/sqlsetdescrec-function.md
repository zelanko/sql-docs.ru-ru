---
title: "Функция SQLSetDescRec | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLSetDescRec
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLSetDescRec
helpviewer_keywords: SQLSetDescRec function [ODBC]
ms.assetid: bf55256c-7eb7-4e3f-97ef-b0fee09ba829
caps.latest.revision: "22"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: dda8ecdee1830805c51b5e795f91ff4025218260
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="sqlsetdescrec-function"></a>SQLSetDescRec, функция
**Соответствия**  
 Появился в версии: ODBC 3.0 нормативных требований: ISO-92  
  
 **Сводка**  
 **SQLSetDescRec** функция задает несколько поля дескриптора, которые определяют тип данных, а буфер к столбца или параметра данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
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
 [Вход] Указывает дескриптор запись, которая содержит поля, которые необходимо задать. Дескриптор записи нумеруются от 0, записи номером 0 является записи закладки. Этот аргумент должен быть равен или больше 0. Если *RecNumber* больше, чем значение SQL_DESC_COUNT присвоено значение SQL_DESC_COUNTis *RecNumber*.  
  
 *Тип*  
 [Вход] Значение, для которого требуется задать поле SQL_DESC_TYPE для записи дескриптора.  
  
 *Подтип*  
 [Вход] Для записей, тип которого равно SQL_DATETIME или SQL_INTERVAL это значение, которое требуется задать для поля SQL_DESC_DATETIME_INTERVAL_CODE.  
  
 *Длина*  
 [Вход] Значение, которое требуется задать для поля SQL_DESC_OCTET_LENGTH для записи дескриптора.  
  
 *Точность*  
 [Вход] Значение, которое требуется задать для поля SQL_DESC_PRECISION для записи дескриптора.  
  
 *Масштаб*  
 [Вход] Значение, которое требуется задать для поля SQL_DESC_SCALE для записи дескриптора.  
  
 *DataPtr*  
 [Отложенные ввода или вывода] Значение, которое требуется задать для поля для записи дескриптора SQL_DESC_DATA_PTR. *DataPtr* можно задать указатель null.  
  
 *DataPtr* аргумент может быть присвоено на указатель null для поля SQL_DESC_DATA_PTR установите указатель null. Если дескриптор в *DescriptorHandle* аргумент не связана с Отменить, это отменяется привязка значения столбца.  
  
 *StringLengthPtr*  
 [Отложенные ввода или вывода] Значение, которое требуется задать для поля SQL_DESC_OCTET_LENGTH_PTR для записи дескриптора. *StringLengthPtr* можно присвоить значение задайте в поле SQL_DESC_OCTET_LENGTH_PTR значение пустой указатель на указатель null.  
  
 *IndicatorPtr*  
 [Отложенные ввода или вывода] Значение, которое требуется задать для поля SQL_DESC_INDICATOR_PTR для записи дескриптора. *IndicatorPtr* можно присвоить значение поля SQL_DESC_INDICATOR_PTR установите указатель null на указатель null.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, значение SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLSetDescRec** возвращает значение SQL_ERROR или SQL_SUCCESS_WITH_INFO, соответствующее значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *HandleType* из SQL_ HANDLE_DESC и *обработки* из *DescriptorHandle*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые **SQLSetDescRec** и описание каждого из них в контексте этой функции; нотации «(DM)» предшествует описания SQLSTATE, возвращаемых диспетчером драйверов. Код возврата, связанные с каждым из значений SQLSTATE — это SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение, относящиеся к драйверу. (Функция возвращает значение SQL_SUCCESS_WITH_INFO).|  
|07009|Недопустимый индекс дескриптора|*RecNumber* аргумент было задано значение 0 и *DescriptorHandle* называют дескриптор IPD.<br /><br /> *RecNumber* аргумент был меньше 0.<br /><br /> *RecNumber* аргумент был больше, чем максимальное количество столбцов или параметров, которые источник данных может поддерживать, и *DescriptorHandle* аргумент был APD, IPD или Отменить.<br /><br /> *RecNumber* аргумент, равное 0 и *DescriptorHandle* аргумент называют неявным образом выделенный APD. (Эта ошибка возникает с дескриптором явно выделенного приложения, так как неизвестно, является ли дескриптор явно выделенного приложения APD или Отменить до времени выполнения.)|  
|08S01|Сбой связи|Сбой в канале связи между драйвером и источника данных, к которому был подключен драйвер перед обработкой функции было завершено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой было нет определенных SQLSTATE и для которого был определен SQLSTATE не зависит от реализации. Сообщение об ошибке, возвращенные **SQLGetDiagRec** в  *\*MessageText* буфера описывает ошибку и его причины.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY010|Ошибка последовательности функций|(DM) *DescriptorHandle* была связана с *StatementHandle* для которой асинхронного выполнения функции, (не это один) был вызван и все еще выполняется, при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**, или **SQLSetPos** был вызван для  *StatementHandle* с помощью которого *DescriptorHandle* был связанные и возвращается значение SQL_NEED_DATA. Эта функция был вызван перед отправкой данных для всех параметров с данными времени выполнения или столбцов.<br /><br /> (DM) был вызван асинхронно выполняемой функции для дескриптора соединения, с которым связан *DescriptorHandle*. Выполняется при этом функция aynchronous **SQLSetDescRec** была вызвана функция.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, или **SQLMoreResults** был вызван для одного из дескрипторов инструкций, связанных с *DescriptorHandle* и возвращается SQL_PARAM_DATA_AVAILABLE. До получения данных для всех параметров потоковой вызове этой функции.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, поскольку базовые объекты памяти будет недоступен, возможно из-за нехватки памяти.|  
|HY016|Не удается изменить дескриптор строки реализации|*DescriptorHandle* аргумент был связан с IRD.|  
|HY021|Неправильные сведения о дескрипторе|*Типа* поля или любого другого поля, связанные с этим полем SQL_DESC_TYPE в дескрипторе, не был допустимым или согласованной.<br /><br /> Сведения о дескрипторе проверяется в ходе проверки согласованности не согласован. (См. «Проверка целостности» далее в этом разделе).|  
|HY090|Недопустимая длина строки или буфера|(DM) был драйвер ODBC 2*.x* драйвера, дескриптор был Отменить *ColumnNumber* аргумент было задано значение 0 и значения, указанного в аргументе *BufferLength* был не равно 4.|  
|HY117|Соединение будет приостановлена из-за неизвестной транзакции состояния. Только отключиться и разрешены функции, доступные только для чтения.|(DM) Дополнительные сведения о состоянии приостановки см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания соединения истекло|Время ожидания соединения истекло раньше, чем ответил на запрос источника данных. Время ожидания задается с помощью **SQLSetConnectAttr**, sql_attr_connection_timeout не учитывается.|  
|IM001|Драйвер не поддерживает эту функцию|Драйвер (DM), связанные с *DescriptorHandle* не поддерживает функцию.|  
  
## <a name="comments"></a>Комментарии  
 Приложение может вызвать **SQLSetDescRec** Чтобы установить следующие поля для одного столбца или параметра:  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (для записи, тип которого равно SQL_DATETIME или SQL_INTERVAL)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_DATA_PTR  
  
-   SQL_DESC_OCTET_LENGTH_PTR  
  
-   SQL_DESC_INDICATOR_PTR  
  
> [!NOTE]  
>  Если вызов **SQLSetDescRec** завершается ошибкой, то содержимое указанной записи дескриптора *RecNumber* аргумент не определены.  
  
 При привязке столбца или параметра, **SQLSetDescRec** позволяет изменять несколько полей, влияющие на привязку без вызова **SQLBindCol** или **SQLBindParameter** или несколько обращений **SQLSetDescField**. **SQLSetDescRec** можно установить поля на дескриптор, который в настоящее время не связанные с инструкцией. Обратите внимание, что **SQLBindParameter** задает больше полей, чем **SQLSetDescRec**, можно установить поля в APD и IPD в одном вызове и не требует дескриптора.  
  
> [!NOTE]  
>  Атрибут инструкции SQL_ATTR_USE_BOOKMARKS должен всегда быть установлен перед вызовом **SQLSetDescRec** с *RecNumber* аргумент 0, чтобы задать поля закладки. Хотя это не обязательно, настоятельно рекомендуется.  
  
## <a name="consistency-checks"></a>Проверка согласованности  
 Проверка согласованности выполняется драйвер автоматически каждый раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD. Если любое из полей не согласуется с другими полями **SQLSetDescRec** вернет SQLSTATE HY021 (неправильные сведения о дескрипторе).  
  
 Всякий раз, когда приложение задает поле SQL_DESC_DATA_PTR в APD, Отменить или IPD, драйвер проверяет, что значение поля SQL_DESC_TYPE и значения, применяемые к этому полю SQL_DESC_TYPE правильны и согласуются. Эта проверка не всегда выполняется при **SQLBindParameter** или **SQLBindCol** вызывается или когда **SQLSetDescRec** вызывается для APD, Отменить или IPD. Проверка согласованности включает в себя следующие проверки в поля дескриптора:  
  
-   Поле SQL_DESC_TYPE должно быть одним из допустимых ODBC C или типы SQL или типом специфические для драйвера SQL. Поле SQL_DESC_CONCISE_TYPE должно быть одним из допустимых типов ODBC C или SQL или драйвером C или SQL типом, включая четкими типы даты и времени и интервала.  
  
-   Если поле SQL_DESC_TYPE записи равно SQL_DATETIME или SQL_INTERVAL, SQL_DESC_DATETIME_INTERVAL_CODE поле должно быть одним из действительное значение datetime или коды интервал. (См. в описании поля SQL_DESC_DATETIME_INTERVAL_CODE в [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md).)  
  
-   Если поле SQL_DESC_TYPE указывает числового типа, проверка поля SQL_DESC_PRECISION и SQL_DESC_SCALE производится недействителен.  
  
-   Если поле SQL_DESC_CONCISE_TYPE является типом данных времени или timestamp, интервал тип с компонент секунд или один из типов данных интервала с компонентом времени, проверить поле SQL_DESC_PRECISION быть допустимым секунды.  
  
-   Если SQL_DESC_CONCISE_TYPE является тип интервала данных, поле SQL_DESC_DATETIME_INTERVAL_PRECISION будет проверена начальным значением точности допустимый интервал.  
  
 Поле SQL_DESC_DATA_PTR IPD обычно не задано; Однако приложение можно сделать, чтобы принудительно выполнить проверку согласованности IPD полей. Невозможно выполнить проверку согласованности на IRD. Значение, равное поле SQL_DESC_DATA_PTR IPD фактически не сохраняются и не удается получить с помощью вызова **SQLGetDescField** или **SQLGetDescRec**; задание осуществляется только для принудительного Проверка согласованности.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Сведения о|См.|  
|---------------------------|---------|  
|Привязка столбца|[Функция SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Привязка параметра|[Функция SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|Получение одного дескриптора поля|[Функция SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|Получение нескольких полей дескриптора|[Функция SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|Задание полей одного дескриптора|[Функция SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API-интерфейса ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
