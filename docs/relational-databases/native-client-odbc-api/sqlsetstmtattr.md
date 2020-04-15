---
title: СЗЛСетстматтр Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetStmtAttr function
ms.assetid: 799c80fd-c561-4912-8562-9229076dfd19
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2fc3bf094504415cc2ec27c6c472cce747b53481
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301907"
---
# <a name="sqlsetstmtattr"></a>SQLSetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает смешанную (динамическую и с набором ключей) модель курсора. Попытки установить размер набора ключей с помощью атрибута SQL_ATTR_KEYSET_SIZE завершатся неудачей, если задаваемое значение не равно 0.  
  
 Приложение устанавливает SQL_ATTR_ROW_ARRAY_SIZE на все операторы, чтобы объявить количество строк, возвращенных на вызов функции **S'LFetch** или [S'LFetchScroll.](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md) Для инструкций, задающих серверный курсор, драйвер использует атрибут SQL_ATTR_ROW_ARRAY_SIZE, чтобы задать размер блока строк, которые создаются на сервере в ответ на запрос на выборку со стороны курсора. В пределах размера блока динамического курсора членство в строке и порядок не меняются, если уровень изоляции транзакции достаточен для обеспечения повторяемого чтения фиксированных транзакций. Вне блока, задаваемого этой величиной, курсор полностью динамичен. Размер блока серверного курсора полностью динамичен и может быть изменен в любой момент в процессе обработки выборки.  
  
## <a name="sqlsetstmtattr-and-table-valued-parameters"></a>Функция SQLSetStmtAttr и возвращающие табличные значения параметры  
 Перед доступом к полям дескриптора для столбцов параметров, оцениваемых таблицей, можно использовать для установки SQL_SOPT_SS_PARAM_FOCUS в дескрипторе параметра приложения (APD).  
  
 При попытке установить SQL_SOPT_SS_PARAM_FOCUS к облачному параметру, который не является параметром, ценным на стол, s'LSetStmtAttr возвращается SQL_ERROR и создается диагностическая запись с помощью S'LSTATE S HY024 и сообщения "Недействительное значение атрибута". Если возвращается значение SQL_ERROR, то атрибут SQL_SOPT_SS_PARAM_FOCUS не меняется.  
  
 Установка атрибута SQL_SOPT_SS_PARAM_FOCUS в значение 0 восстанавливает доступ к записям дескриптора для параметров.  
  
 Кроме того, можно использовать для установки SQL_SOPT_SS_NAME_SCOPE. Дополнительные сведения см. в подразделе «SQL_SOPT_SS_NAME_SCOPE» далее в этом разделе.  
  
 Для получения дополнительной [Table-Valued Parameter Metadata for Prepared Statements](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)информации см.  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlsetstmtattr-support-for-sparse-columns"></a>Поддержка разреженных столбцов функцией SQLSetStmtAttr  
 Для установки SQL_SOPT_SS_NAME_SCOPE можно использовать SQL_SOPT_SS_NAME_SCOPE. Для получения дополнительной информации смотрите раздел SQL_SOPT_SS_NAME_SCOPE, позже в этой теме. Для получения дополнительной информации о разреженной столбцов, [см. Sparse колонки поддержка &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="statement-attributes"></a>Атрибуты инструкции  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает следующие атрибуты инструкций, специфичные для драйвера.  
  
### <a name="sql_sopt_ss_cursor_options"></a>SQL_SOPT_SS_CURSOR_OPTIONS  
 Атрибут SQL_SOPT_SS_CURSOR указывает, будет ли драйвер использовать для курсоров специфичные для данного драйвера параметры настройки производительности. При установке этих опций не допускается [использование s'LGetData.](../../relational-databases/native-client-odbc-api/sqlgetdata.md) Значение по умолчанию равно SQL_CO_OFF. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_CO_OFF|По умолчанию. Отстраняет быстро вперед только, только для чтения курсоры и autofetch, позволяет **S'LGetData** на вперед только, только для чтения курсоры. Если атрибут SQL_SOPT_SS_CURSOR_OPTIONS имеет значение SQL_CO_OFF, тип курсора не изменится. То есть быстрый однопроходный курсор останется быстрым однопроходным курсором. Чтобы изменить тип курсора, приложение должно теперь установить другой тип курсора с помощью **S'LSetStmtAttr**/SQL_ATTR_CURSOR_TYPE.|  
|SQL_CO_FFO|Включает в себя курсоры только вперед, только для чтения, отклоняет **s-LGetData** только на курсорах только для чтения.|  
|SQL_CO_AF|Включает параметр автоматической выборки для курсора любого типа. Когда эта опция установлена для ручки оператора, **S'LExecute** или **S'LExecDirect** будет генерировать неявный **S'LFetchScroll** (SQL_FIRST). Курсор открыт, и первый набор строк возвращен за одно обращение к серверу.|  
|SQL_CO_FFO_AF|Включает быстрые однопроходные курсоры с параметром автоматической выборки. Эквивалентно одновременному заданию SQL_CO_AF и SQL_CO_FFO.|  
  
 Если эти параметры заданы, сервер автоматически закрывает курсор, когда обнаруживает, что была получена последняя строка. Приложение по-прежнему должно вызывать [S'LFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md) (SQL_CLOSE) или [S'LCloseCursor,](../../relational-databases/native-client-odbc-api/sqlclosecursor.md)но драйвер не должен отправлять близкое уведомление на сервер.  
  
 Если список избранных содержит **текст,** **ntext**или столбец **изображения,** курсор быстрого форварда преобразуется в динамический курсор, и **допускается s'LGetData.**  
  
### <a name="sql_sopt_ss_defer_prepare"></a>SQL_SOPT_SS_DEFER_PREPARE  
 Атрибут SQL_SOPT_SS_DEFER_PREPARE определяет, подготовлено ли заявление немедленно или отложено до тех пор, пока не будет выполнена [s'L-Остереколь](../../relational-databases/native-client-odbc-api/sqldescribecol.md) или [S'LDescribeParam.](../../relational-databases/native-client-odbc-api/sqldescribeparam.md) **SQLExecute** В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 и более ранних версиях это свойство не учитывается (подготовка не откладывается). Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_DP_ON|По умолчанию. После вызова [функции S'LPrepare](https://go.microsoft.com/fwlink/?LinkId=59360), подготовка оператора откладывается до тех пор, пока не будет выполнена операция **s'L'L'E(** **s'LDescribeCol** или **S'LDescribeParam).**|  
|SQL_DP_OFF|Заявление готовится сразу же после выполнения **S'LPrepare.**|  
  
### <a name="sql_sopt_ss_regionalize"></a>SQL_SOPT_SS_REGIONALIZE  
 Атрибут SQL_SOPT_SS_REGIONALIZE используется для задания преобразования данных на уровне инструкции. Атрибут указывает драйверу, что следует использовать настройки локали на клиенте при преобразовании данных в денежном формате, формате даты и времени в символьные данные. Преобразование проводится только из собственных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в строки символов.  
  
 Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_RE_OFF|По умолчанию. Драйвер ODBC не использует настройки локали на клиенте при преобразовании данных в денежном формате, формате даты и времени в строковые данные.|  
|SQL_RE_ON|Драйвер ODBC использует настройки локали на клиенте при преобразовании данных в денежном формате, формате даты и времени в символьные данные.|  
  
 Региональные параметры преобразований применяются к типам данных валюты, чисел и даты-времени. Параметры преобразований применяются только к выходным преобразованиям, когда значения валюты, числовые значения, значения даты или времени преобразуются в символьные строки.  
  
> [!NOTE]  
>  Когда атрибут инструкции SQL_SOPT_SS_REGIONALIZE включен, драйвер использует настройки локали из реестра текущего пользователя. Драйвер не соблюдает данный поток текущего потока, если приложение устанавливает его, например, вызывая **SetThreadLocale.**  
  
 Изменение режима работы источника данных с региональными параметрами может привести к ошибке приложения. Изменение этого значения может отрицательно повлиять на работу приложения, анализирующего строки даты и предполагающего, что строки даты будут выводиться в виде, определенном ODBC.  
  
### <a name="sql_sopt_ss_textptr_logging"></a>SQL_SOPT_SS_TEXTPTR_LOGGING  
 В SQL_SOPT_SS_TEXTPTR_LOGGING атрибут переключает журналы операций на столбцах, содержащих **текстовые** или **изображенияданные.** Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_TL_OFF|Отстраняет журналопераций, выполняемых на **текстовых** и **изображений.**|  
|SQL_TL_ON|По умолчанию. Позволяет регистриру операций, выполняемых на **текстовых** и **изображений.**|  
  
### <a name="sql_sopt_ss_hidden_columns"></a>SQL_SOPT_SS_HIDDEN_COLUMNS  
 В результирующем наборе атрибут SQL_SOPT_SS_HIDDEN_COLUMNS предоставляет столбцы, скрытые в инструкции [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT FOR BROWSE. По умолчанию драйвер не предоставляет доступ к этим столбцам. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_HC_OFF|По умолчанию. Столбцы FOR BROWSE в результирующем наборе скрыты.|  
|SQL_HC_ON|Обеспечивает доступ к столбцам FOR BROWSE.|  
  
### <a name="sql_sopt_ss_querynotification_msgtext"></a>Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT возвращает текст сообщения в ответ на запрошенное уведомление о запросе.  
  
### <a name="sql_sopt_ss_querynotification_options"></a>SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS задает параметры для запроса уведомления о запросе. Эти параметры заданы в строке с конструкцией `name=value`, как показано ниже. За создание службы и считывание уведомлений из очереди отвечает приложение.  
  
 Строка параметров уведомлений запросов имеет следующий синтаксис.  
  
 `service=<service-name>[;(local database=<database>|broker instance=<broker instance>)]`  
  
 Пример:  
  
 `service=mySSBService;local database=mydb`  
  
### <a name="sql_sopt_ss_querynotification_timeout"></a>SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT задает время в секундах, в течение которого уведомление о запросе будет активным. Значение по умолчанию составляет 432 000 секунд (5 суток). Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
### <a name="sql_sopt_ss_param_focus"></a>SQL_SOPT_SS_PARAM_FOCUS  
 Атрибут SQL_SOPT_SS_PARAM_FOCUS определяет фокус для последующих вызовов S'LBindParameter, S'LGetDescfield, S'LSetDescfield, S'LGetDescrec и S'LSetDescRec и S'LSetDescRec.  
  
 Атрибут SQL_SOPT_SS_PARAM_FOCUS принадлежит к типу SQLULEN.  
  
 По умолчанию он имеет значение 0; это означает, что вызовы относятся к параметрам, соответствующим маркерам параметров в инструкции SQL. Если задать для атрибута значение, равное порядковому номеру возвращающего табличное значение параметра, вызовы будут относиться к столбцам этого параметра. При установке значения, которое не является параметром параметра параметра, ценяемого на стол, эти вызовы возвращают ошибку IM020: "Параметр фокус не относится к параметру, ценяемому на стол".  
  
### <a name="sql_sopt_ss_name_scope"></a>SQL_SOPT_SS_NAME_SCOPE  
 Атрибут SQL_SOPT_SS_NAME_SCOPE задает область действия имени для последующих вызовов функций работы с каталогами. Набор результатов, возвращенный S'LColumns, зависит от настройки SQL_SOPT_SS_NAME_SCOPE.  
  
 Атрибут SQL_SOPT_SS_NAME_SCOPE принадлежит к типу SQLULEN.  
  
|*ЗначениеPtr*|Описание|  
|----------------------|-----------------|  
|SQL_SS_NAME_SCOPE_TABLE|По умолчанию.<br /><br /> При использовании возвращающих табличное значение параметров этот атрибут указывает, что нужно возвратить метаданные реально существующих таблиц.<br /><br /> При использовании разреженной функции столбцов, S'LColumns будет возвращать только столбцы, которые не являются членами разреженной **column_set.**|  
|SQL_SS_NAME_SCOPE_TABLE_TYPE|Указывает, что приложению требуются метаданные для табличного типа, а не для реально существующих таблиц (функции работы с каталогами должны возвращать метаданные для табличных типов). Затем приложение передает TYPE_NAME параметра, оцениваемого таблицей, в качестве параметра *TableName.*|  
|SQL_SS_NAME_SCOPE_EXTENDED|При использовании разреженной функции столбцов S'LColumns возвращает все столбцы, независимо от **column_set** членства.|  
|SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET|При использовании разреженной функции столбцов, S'LColumns возвращает только столбцы, которые являются членами разреженной **column_set.**|  
|SQL_SS_NAME_SCOPE_DEFAULT|Равен атрибуту SQL_SS_NAME_SCOPE_TABLE.|  
  
 SS_TYPE_CATALOG_NAME и SS_TYPE_SCHEMA_NAME используются с параметрами *CatalogueName* и *SchemaName,* соответственно, для определения каталога и схемы для параметра, оцениваемого таблицей. Когда приложение закончит получать метаданные для возвращающего табличное значение параметра, оно должно вновь присвоить SQL_SOPT_SS_NAME_SCOPE значение по умолчанию SQL_SS_NAME_SCOPE_TABLE.  
  
 Если SQL_SOPT_SS_NAME_SCOPE имеет значение SQL_SS_NAME_SCOPE_TABLE, то запросы к связанным серверам завершаются ошибкой. Вызовы в S'LColumns или S'LPrimaryKeys с каталогом, содержащим компонент сервера, потерпят неудачу.  
  
 При попытке задать для атрибута SQL_SOPT_SS_NAME_SCOPE недопустимое значение будет возвращено значение SQL_ERROR и создана диагностическая запись с параметром SQLSTATE HY024 и сообщением «Недопустимое значение атрибута».  
  
 Если функция каталога, чем S'LTables, S'LColumns или S'LPrimaryKeys, называется, когда SQL_SOPT_SS_NAME_SCOPE имеет значение, кроме SQL_SS_NAME_SCOPE_TABLE, SQL_ERROR возвращается. Создается диагностическая запись с параметром SQLSTATE HY010 и сообщением «Ошибочная последовательность функций (значение атрибута SQL_SOPT_SS_NAME_SCOPE не равно SQL_SS_NAME_SCOPE_TABLE)».  
  
## <a name="see-also"></a>См. также:  
 [Функция СЗЛГЕтстматтр](https://go.microsoft.com/fwlink/?LinkId=59355)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
