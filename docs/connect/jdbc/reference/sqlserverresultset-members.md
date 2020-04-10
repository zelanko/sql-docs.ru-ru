---
title: Элементы SQLServerResultSet | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2a438d5d-2d6a-46a0-a2ae-f35fbae4a472
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17d15be7b332d899aa35a0ce7c3d7c2b9cac1edf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80927122"
---
# <a name="sqlserverresultset-members"></a>Элементы SQLServerResultSet
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены элементы, предоставляемые классом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
  
|Имя|Description|  
|----------|-----------------|  
|[CONCUR_SS_OPTIMISTIC_CC](../../../connect/jdbc/reference/concur-ss-optimistic-cc-field-sqlserverresultset.md)|Указывает тип оптимистичного параллелизма чтения-записи в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] без блокировки строк.|  
|[CONCUR_SS_OPTIMISTIC_CCVAL](../../../connect/jdbc/reference/concur-ss-optimistic-ccval-field-sqlserverresultset.md)|Указывает тип оптимистичного параллелизма чтения-записи в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] без блокировки строк.|  
|[CONCUR_SS_SCROLL_LOCKS](../../../connect/jdbc/reference/concur-ss-scroll-locks-field-sqlserverresultset.md)|Указывает тип оптимистичного параллелизма чтения-записи в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с блокировкой строки.|  
|[TYPE_SS_DIRECT_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-direct-forward-only-field-sqlserverresultset.md)|Используется для указания курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] исключительно с типом быстрого последовательного доступа и только для чтения.|  
|[TYPE_SS_SCROLL_DYNAMIC](../../../connect/jdbc/reference/type-ss-scroll-dynamic-field-sqlserverresultset.md)|Используется для указания типа динамических курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SCROLL_KEYSET](../../../connect/jdbc/reference/type-ss-scroll-keyset-field-sqlserverresultset.md)|Позволяет указать тип курсора для набора ключей [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SCROLL_STATIC](../../../connect/jdbc/reference/type-ss-scroll-static-field-sqlserverresultset.md)|Используется для указания типа статических курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[TYPE_SS_SERVER_CURSOR_FORWARD_ONLY](../../../connect/jdbc/reference/type-ss-server-cursor-forward-only-field-sqlserverresultset.md)|Используется для указания курсоров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] исключительно с типом быстрого последовательного доступа и только для чтения.|  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Класс, из которого наследуется:|Description|  
|---------------------------|-----------------|  
|java.sql.ResultSet|CLOSE_CURSORS_AT_COMMIT, CONCUR_READ_ONLY, CONCUR_UPDATABLE, FETCH_FORWARD, FETCH_REVERSE, FETCH_UNKNOWN, HOLD_CURSORS_OVER_COMMIT, TYPE_FORWARD_ONLY, TYPE_SCROLL_INSENSITIVE, TYPE_SCROLL_SENSITIVE|  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[absolute](../../../connect/jdbc/reference/absolute-method-sqlserverresultset.md)|Перемещает курсор в указанную строку этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[afterLast](../../../connect/jdbc/reference/afterlast-method-sqlserverresultset.md)|Перемещает курсор в область за последней строкой этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[beforeFirst](../../../connect/jdbc/reference/beforefirst-method-sqlserverresultset.md)|Перемещает курсор в область до первой строки этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[cancelRowUpdates](../../../connect/jdbc/reference/cancelrowupdates-method-sqlserverresultset.md)|Отменяет обновления текущей строки в этом объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverresultset.md)|Удаляет все предупреждения, включенные в отчет для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverresultset.md)|Высвобождает ресурсы базы данных и JDBC этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) вместо ожидания их автоматического освобождения.|  
|[deleteRow](../../../connect/jdbc/reference/deleterow-method-sqlserverresultset.md)|Удаляет текущую строку из этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) и из используемой базы данных.|  
|[finalize](../../../connect/jdbc/reference/finalize-method-sqlserverresultset.md)|Явно закрывает этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[findColumn](../../../connect/jdbc/reference/findcolumn-method-sqlserverresultset.md)|Извлекает индекс первого столбца, имя которого совпадает с именем, указанным в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[first](../../../connect/jdbc/reference/first-method-sqlserverresultset.md)|Перемещает курсор в первую строку этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getArray](../../../connect/jdbc/reference/getarray-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Array.|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде потока символов ASCII.|  
|[getBigDecimal](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)|Извлекает значение индекса заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде java.math.BigDecimal.|  
|[getBinaryStream](../../../connect/jdbc/reference/getbinarystream-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде двоичного потока неинтерпретированных байтов.|  
|[getBlob](../../../connect/jdbc/reference/getblob-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта BLOB на языке программирования Java.|  
|[getBoolean](../../../connect/jdbc/reference/getboolean-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **boolean** на языке программирования Java.|  
|[getByte](../../../connect/jdbc/reference/getbyte-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **byte** на языке программирования Java.|  
|[getBytes](../../../connect/jdbc/reference/getbytes-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде массива типа **byte** на языке программирования Java.|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.io.Reader.|  
|[getClob](../../../connect/jdbc/reference/getclob-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Clob на языке программирования Java.|  
|[getConcurrency](../../../connect/jdbc/reference/getconcurrency-method-sqlserverresultset.md)|Извлекает режим параллелизма этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getCursorName](../../../connect/jdbc/reference/getcursorname-method-sqlserverresultset.md)|Возвращает имя курсора SQL, используемого данным объектом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getDate](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Date на языке программирования Java.|  
|[getDateTimeOffset](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)|Получает значение указанного столбца в виде объекта [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[getDouble](../../../connect/jdbc/reference/getdouble-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **double** на языке программирования Java.|  
|[getFetchDirection](../../../connect/jdbc/reference/getfetchdirection-method-sqlserverresultset.md)|Извлекает значение направления выборки для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getFetchSize](../../../connect/jdbc/reference/getfetchsize-method-sqlserverresultset.md)|Извлекает значение размера выборки для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getFloat](../../../connect/jdbc/reference/getfloat-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **float** на языке программирования Java.|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverresultset.md)|Извлекает значение удержания этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getInt](../../../connect/jdbc/reference/getint-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **int** на языке программирования Java.|  
|[getLong](../../../connect/jdbc/reference/getlong-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **long** на языке программирования Java.|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)|Извлекает количество, типы и свойства столбцов этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getNCharacterStream](../../../connect/jdbc/reference/getncharacterstream-method-sqlserverresultset.md)|Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Reader.|  
|[getNClob](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **NClob** на языке программирования Java.|  
|[getNString](../../../connect/jdbc/reference/getnstring-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа String на языке программирования Java.|  
|[getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md)|Получает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта на языке программирования Java.|  
|[getRef](../../../connect/jdbc/reference/getref-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта Ref на языке программирования Java.|  
|[getRow](../../../connect/jdbc/reference/getrow-method-sqlserverresultset.md)|Извлекает номер текущей строки.|  
|[getShort](../../../connect/jdbc/reference/getshort-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **short** на языке программирования Java.|  
|[getStatement](../../../connect/jdbc/reference/getstatement-method-sqlserverresultset.md)|Извлекает объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), на основе которого был создан этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getString](../../../connect/jdbc/reference/getstring-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде значения типа **String** на языке программирования Java.|  
|[getSQLXML](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)|Извлекает значение указанного столбца в текущей строке объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта **SQLXML**.|  
|[getTime](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Time на языке программирования Java.|  
|[getTimestamp](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта java.sql.Timestamp на языке программирования Java.|  
|[getType](../../../connect/jdbc/reference/gettype-method-sqlserverresultset.md)|Извлекает тип курсора этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[getUnicodeStream](../../../connect/jdbc/reference/getunicodestream-method-sqlserverresultset.md)|Извлекает значение заданного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде потока символов Юникод.|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverresultset.md)|Извлекает значение указанного столбца в текущей строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в виде объекта URL.|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverresultset.md)|Извлекает первое предупреждение, указанное в отчетах для вызовов этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[insertRow](../../../connect/jdbc/reference/insertrow-method-sqlserverresultset.md)|Вставляет содержимое строки вставки в этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) и в базу данных.|  
|[isAfterLast](../../../connect/jdbc/reference/isafterlast-method-sqlserverresultset.md)|Извлекает логическое значение, которое показывает, располагается ли курсор за последней строкой этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[isBeforeFirst](../../../connect/jdbc/reference/isbeforefirst-method-sqlserverresultset.md)|Извлекает логическое значение, которое показывает, располагается ли курсор перед первой строкой этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverresultset.md)|Указывает, был ли закрыт этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[isFirst](../../../connect/jdbc/reference/isfirst-method-sqlserverresultset.md)|Извлекает логическое значение, которое показывает, располагается ли курсор в первой строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[isLast](../../../connect/jdbc/reference/islast-method-sqlserverresultset.md)|Извлекает логическое значение, которое показывает, располагается ли курсор в последней строке этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[last](../../../connect/jdbc/reference/last-method-sqlserverresultset.md)|Перемещает курсор в последнюю строку этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[moveToCurrentRow](../../../connect/jdbc/reference/movetocurrentrow-method-sqlserverresultset.md)|Перемещает курсор в сохраненное местоположение курсора, обычно в текущую строку.|  
|[moveToInsertRow](../../../connect/jdbc/reference/movetoinsertrow-method-sqlserverresultset.md)|Перемещает курсор в строку вставки.|  
|[next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md)|Перемещает курсор на одну строку вниз от текущей позиции.|  
|[previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md)|Перемещает курсор в предыдущую строку этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[refreshRow](../../../connect/jdbc/reference/refreshrow-method-sqlserverresultset.md)|Обновляет текущую строку, записывая последнее значение из базы данных.|  
|[relative](../../../connect/jdbc/reference/relative-method-sqlserverresultset.md)|Перемещает курсор на заданное количество строк относительно текущей строки в положительном или отрицательном направлении.|  
|[rowDeleted](../../../connect/jdbc/reference/rowdeleted-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли удалена строка.|  
|[rowInserted](../../../connect/jdbc/reference/rowinserted-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли сделана вставка в текущую строку.|  
|[rowUpdated](../../../connect/jdbc/reference/rowupdated-method-sqlserverresultset.md)|Возвращает значение, определяющее, была ли обновлена текущая строка.|  
|[setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md)|Дает указание относительно направления, в котором будут обрабатываться строки в этом объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[setFetchSize](../../../connect/jdbc/reference/setfetchsize-method-sqlserverresultset.md)|Дает драйверу JDBC подсказку относительно числа строк, которые должны быть извлечены из базы данных, когда этому объекту [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) нужны дополнительные строки.|  
|[updateArray](../../../connect/jdbc/reference/updatearray-method-sqlserverresultset.md)|Обновляет указанный столбец объектом Array.|  
|[updateAsciiStream](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)|Обновляет значение ASCII-потока в указанном столбце.|  
|[updateBigDecimal](../../../connect/jdbc/reference/updatebigdecimal-method-sqlserverresultset.md)|Обновляет указанный столбец объектом BigDecimal.|  
|[updateBinaryStream](../../../connect/jdbc/reference/updatebinarystream-method-sqlserverresultset.md)|Обновляет значение двоичного потока в указанном столбце.|  
|[updateBlob](../../../connect/jdbc/reference/updateblob-method-sqlserverresultset.md)|Обновляет значение java.sql.Blob в указанном столбце.|  
|[updateBoolean](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **boolean**.|  
|[updateByte](../../../connect/jdbc/reference/updatebyte-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **byte**.|  
|[updateBytes](../../../connect/jdbc/reference/updatebytes-method-sqlserverresultset.md)|Обновляет указанный столбец массивом значений **byte**.|  
|[updateCharacterStream](../../../connect/jdbc/reference/updatecharacterstream-method-sqlserverresultset.md)|Обновляет указанный столбец значением потока символов.|  
|[updateClob](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)|Обновляет указанный столбец значением java.sql.Clob.|  
|[updateDate](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)|Обновляет указанный столбец значением даты.|  
|[updateDateTimeOffset](../../../connect/jdbc/reference/updatedatetimeoffset-sqlserverresultset.md)|Обновляет столбец [класса DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md).|  
|[updateDouble](../../../connect/jdbc/reference/updatedouble-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **double**.|  
|[updateFloat](../../../connect/jdbc/reference/updatefloat-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **float**.|  
|[updateInt](../../../connect/jdbc/reference/updateint-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **int**.|  
|[updateLong](../../../connect/jdbc/reference/updatelong-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **long**.|  
|[updateNCharacterStream](../../../connect/jdbc/reference/updatencharacterstream-method-sqlserverresultset.md)|Обновляет указанный столбец значением потока символов.|  
|[updateNClob](../../../connect/jdbc/reference/updatenclob-method-sqlserverresultset.md)|Обновляет заданное значение объекта в указанном столбце.|  
|[updateNString](../../../connect/jdbc/reference/updatenstring-method-sqlserverresultset.md)|Обновляет указанный столбец значением **String**.|  
|[updateNull](../../../connect/jdbc/reference/updatenull-method-sqlserverresultset.md)|Обновляет указанный столбец значением NULL.|  
|[updateObject](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)|Обновляет указанный столбец значением **Object**.|  
|[updateRef](../../../connect/jdbc/reference/updateref-method-sqlserverresultset.md)|Обновляет указанный столбец значением java.sql.Ref.|  
|[updateRow](../../../connect/jdbc/reference/updaterow-method-sqlserverresultset.md)|Обновляет основную базу данных новым содержимым текущей строки этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).|  
|[updateShort](../../../connect/jdbc/reference/updateshort-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **short**.|  
|[updateString](../../../connect/jdbc/reference/updatestring-method-sqlserverresultset.md)|Обновляет указанный столбец значением **String**.|  
|[updateSQLXML](../../../connect/jdbc/reference/updatesqlxml-method-sqlserverresultset.md)|Обновляет указанный столбец значением типа **SQLXML**.|  
|[updateTime](../../../connect/jdbc/reference/updatetime-method-sqlserverresultset.md)|Обновляет указанный столбец значением времени.|  
|[updateTimestamp](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)|Обновляет указанный столбец значением отметки времени.|  
|[wasNull](../../../connect/jdbc/reference/wasnull-method-sqlserverresultset.md)|Проверяет, является ли последнее считанное значение NULL.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
