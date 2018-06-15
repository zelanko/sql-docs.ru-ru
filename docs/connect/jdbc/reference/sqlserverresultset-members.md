---
title: Элементы SQLServerResultSet | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf318137b6d3f23a2161de97999df29b7f29ed8b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32852747"
---
# <a name="sqlserverresultset-members"></a>Элементы SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Название|Описание|  
|----------|-----------------|  
|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] чтение и запись типа оптимистичный параллелизм без блокировки строк.|  
|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] чтение и запись типа оптимистичный параллелизм без блокировки строк.|  
|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] чтение и запись типа оптимистической блокировки с блокировки строк.|  
|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип курсора быстрый однопроходный, только для чтения.|  
|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] динамический тип курсора.|  
|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип курсора keyset.|  
|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип статического курсора.|  
|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|Используется для указания [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] тип курсора быстрый однопроходный, только для чтения.|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Описание|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE_CURSORS_AT_COMMIT, CONCUR_READ_ONLY, CONCUR_UPDATABLE, FETCH_FORWARD, FETCH_REVERSE, FETCH_UNKNOWN, HOLD_CURSORS_OVER_COMMIT, TYPE_FORWARD_ONLY, TYPE_SCROLL_INSENSITIVE, TYPE_SCROLL_SENSITIVE|  
  
## <a name="methods"></a>Методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Абсолютный](../../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)|Перемещает курсор в указанную строку в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[afterLast](../../../connect/jdbc/reference/afterlast-method-sqlserverresultset.md)|Перемещает курсор в после последней строки [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[beforeFirst](../../../connect/jdbc/reference/beforefirst-method-sqlserverresultset.md)|Перемещает курсор в перед первой строкой [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[cancelRowUpdates](../../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)|Отменяет обновления текущей строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverresultset.md)|Удаляет все предупреждения, сообщила об этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverresultset.md)|Это освобождает [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта базы данных и ресурсы JDBC вместо ожидания это может произойти, когда он автоматически закрывается.|  
|[deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)|Удаляет текущую строку из этого[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта и из базы данных.|  
|[Завершение](../../../connect/jdbc/reference/finalize-method-sqlserverresultset.md)|Явно закрывает это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[findColumn](../../../connect/jdbc/reference/findcolumn-method-sqlserverresultset.md)|Возвращает индекс первого столбца сопоставления для имени указанного столбца в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[Первый](../../../connect/jdbc/reference/first-method-sqlserverresultset.md)|Перемещение курсора к первой строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объект массива.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде потока символов ASCII.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)|Получает значение индекса заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.math.BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде двоичного потока неинтерпретированных байтов.|  
|[GetBlob](../../../connect/jdbc/reference/getblob-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде больших двоичных объектов объекта на языке программирования Java.|  
|[GetBoolean](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **логическое** языке программирования Java.|  
|[GetByte](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **байтов** языке программирования Java.|  
|[Метод GetBytes](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **байтов** массива в языке программирования Java.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.io.Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объект Clob в языке программирования Java.|  
|[getConcurrency](../../../connect/jdbc/reference/getconcurrency-method-sqlserverresultset.md)|Извлекает режим параллелизма этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getCursorName](../../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)|Возвращает имя курсора SQL, используемые этим [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[функция getDate](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.sql.Date на языке программирования Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)|Получает значение указанного столбца в виде[класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) объекта.|  
|[GetDouble](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **двойные** языке программирования Java.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverresultset.md)|Извлекает значение направления выборки для этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)|Извлекает размер выборки для данного [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[GetFloat](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **float** языке программирования Java.|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverresultset.md)|Извлекает значение удержания это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **int** языке программирования Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **длинные** языке программирования Java.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)|Извлекает количество, типы и свойства этой [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) столбцы этого объекта.|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объект модуля чтения.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)объекта в виде **NClob** объекта на языке программирования Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект в виде строки на Java языка программирования.|  
|[Функция GetObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта на языке программирования Java.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде ссылки объекта на языке программирования Java.|  
|[getRow](../../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)|Извлекает номер текущей строки.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **короткие** языке программирования Java.|  
|[getStatement](../../../connect/jdbc/reference/getstatement-method-sqlserverresultset.md)|Извлекает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) , создающего это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[GetString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **строка** языке программирования Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде **SQLXML** объекта.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.sql.Time на языке программирования Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.sql.Timestamp на языке программирования Java.|  
|[GetType](../../../connect/jdbc/reference/gettype-method-sqlserverresultset.md)|Извлекает тип курсора этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[getUnicodeStream](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как поток символов Юникода.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде URL-адрес объекта.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverresultset.md)|Возвращает первое предупреждение, указанное в отчетах вызовов в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)|Вставляет содержимое строки вставки в это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта и в базу данных.|  
|[isAfterLast](../../../connect/jdbc/reference/isafterlast-method-sqlserverresultset.md)|Сообщает, является ли курсор после последней строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[isBeforeFirst](../../../connect/jdbc/reference/isbeforefirst-method-sqlserverresultset.md)|Сообщает, является ли курсор находится перед первой строкой в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[IsClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverresultset.md)|Указывает, является ли это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект был закрыт.|  
|[isFirst](../../../connect/jdbc/reference/isfirst-method-sqlserverresultset.md)|Сообщает, является ли курсор в первой строке этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[isLast](../../../connect/jdbc/reference/islast-method-sqlserverresultset.md)|Сообщает, является ли курсор на последнюю строку [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[последний](../../../connect/jdbc/reference/last-method-sqlserverresultset.md)|Перемещает курсор на последнюю строку в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[moveToCurrentRow](../../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)|Перемещает курсор в сохраненное местоположение курсора, обычно в текущую строку.|  
|[moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)|Перемещает курсор в строку вставки.|  
|[Далее](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)|Перемещает курсор на одну строку вниз от текущей позиции.|  
|[предыдущие](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)|Перемещает курсор к предыдущей строке в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[refreshRow](../../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md)|Обновляет текущую строку, записывая последнее значение из базы данных.|  
|[relative](../../../connect/jdbc/reference/relative-method-sqlserverresultset.md)|Перемещает курсор на заданное количество строк относительно текущей строки в положительном или отрицательном направлении.|  
|[RowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли удалена строка.|  
|[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли сделана вставка в текущую строку.|  
|[RowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли обновлена текущая строка.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)|Дает указание относительно направления, в котором строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта будет обработан.|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)|Дает указание относительно числа строк, которые должны быть извлечены из базы данных, при необходимости в дополнительных строках для данного драйвера JDBC [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[updateArray](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)|Обновляет указанный столбец объектом массив.|  
|[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)|Обновляет значение ASCII-потока в указанном столбце.|  
|[updateBigDecimal](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)|Обновляет указанный столбец объектом BigDecimal.|  
|[updateBinaryStream](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)|Обновляет значение двоичного потока в указанном столбце.|  
|[updateBlob](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)|Обновляет значение java.sql.Blob в указанном столбце.|  
|[updateBoolean](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)|Обновляет указанный столбец с **логическое** значение.|  
|[updateByte](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)|Обновляет указанный столбец с **байтов** значение.|  
|[updateBytes](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)|Обновляет указанный столбец с массивом **байтов** значения.|  
|[updateCharacterStream](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)|Обновляет указанный столбец значением потока символов.|  
|[updateClob](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)|Обновляет указанный столбец значением java.sql.Clob.|  
|[updateDate](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)|Обновляет указанный столбец значением даты.|  
|[метод updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)|Обновления [класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) столбца.|  
|[updateDouble](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)|Обновляет указанный столбец с **двойные** значение.|  
|[updateFloat](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)|Обновляет указанный столбец с **float** значение.|  
|[updateInt](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)|Обновляет указанный столбец с **int** значение.|  
|[updateLong](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)|Обновляет указанный столбец с **длинные** значение.|  
|[updateNCharacterStream](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)|Обновляет указанный столбец значением потока символов.|  
|[updateNClob](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)|Обновляет заданное значение объекта в указанном столбце.|  
|[updateNString](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)|Обновляет указанный столбец с **строка** значение.|  
|[updateNull](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)|Обновляет указанный столбец значением NULL.|  
|[updateObject](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)|Обновляет указанный столбец с **объекта** значение.|  
|[updateRef](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)|Обновляет указанный столбец значением java.sql.Ref.|  
|[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)|Обновляет основной базы данных новым содержимым текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.|  
|[updateShort](../../../connect/jdbc/reference/updateshort-method-sqlserverresultset.md)|Обновляет указанный столбец с **короткие** значение.|  
|[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)|Обновляет указанный столбец с **строка** значение.|  
|[updateSQLXML](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)|Обновляет указанный столбец с **SQLXML** значение.|  
|[updateTime](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)|Обновляет указанный столбец значением времени.|  
|[updateTimestamp](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)|Обновляет указанный столбец значением отметки времени.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlserverresultset.md)|Проверяет, является ли последнее считанное значение NULL.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также  
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
