---
title: "Элементы SQLServerResultSetMetaData | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37587981-2979-49a3-a6ab-df4bfb9b8748
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7c555f6a12d2d6706813673463c31e6ac6dd5e17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverresultsetmetadata-members"></a>Элементы SQLServerResultSetMetaData
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
  
|Имя|Description|  
|----------|-----------------|  
|java.sql.ResultSetMetaData|columnNoNulls, columnNullable, columnNullableUnknown|  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[getCatalogName](../../../connect/jdbc/reference/getcatalogname-method-sqlserverresultsetmetadata.md)|Возвращает имя каталога для таблицы, содержащей указанный столбец.|  
|[getColumnClassName](../../../connect/jdbc/reference/getcolumnclassname-method-sqlserverresultsetmetadata.md)|Возвращает полное имя класса Java, экземпляры которого создаются в том случае, если [getObject](../../../connect/jdbc/reference/getobject-method-sqlserverresultset.md) метод [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) класс называется для извлечения значения из столбца.|  
|[getColumnCount](../../../connect/jdbc/reference/getcolumncount-method-sqlserverresultsetmetadata.md)|Возвращает число столбцов в результирующем наборе.|  
|[getColumnDisplaySize](../../../connect/jdbc/reference/getcolumndisplaysize-method-sqlserverresultsetmetadata.md)|Возвращает стандартную максимальную ширину заданного столбца в символах.|  
|[getColumnLabel](../../../connect/jdbc/reference/getcolumnlabel-method-sqlserverresultsetmetadata.md)|Возвращает название, предполагаемое для использования в распечатках, и отображает заданный столбец.|  
|[getColumnName](../../../connect/jdbc/reference/getcolumnname-method-sqlserverresultsetmetadata.md)|Возвращает имя указанного столбца.|  
|[getColumnType](../../../connect/jdbc/reference/getcolumntype-method-sqlserverresultsetmetadata.md)|Возвращает тип SQL указанного столбца.|  
|[getColumnTypeName](../../../connect/jdbc/reference/getcolumntypename-method-sqlserverresultsetmetadata.md)|Возвращает имя определяемого базой данных типа для указанного столбца.|  
|[getPrecision](../../../connect/jdbc/reference/getprecision-method-sqlserverresultsetmetadata.md)|Возвращает число десятичных разрядов для указанного столбца.|  
|[getScale](../../../connect/jdbc/reference/getscale-method-sqlserverresultsetmetadata.md)|Возвращает число цифр справа от десятичной запятой для указанного столбца.|  
|[getSchemaName](../../../connect/jdbc/reference/getschemaname-method-sqlserverresultsetmetadata.md)|Возвращает имя схемы для таблицы, содержащей указанный столбец.|  
|[getTableName](../../../connect/jdbc/reference/gettablename-method-sqlserverresultsetmetadata.md)|Возвращает имя таблицы для указанного столбца.|  
|[isAutoIncrement](../../../connect/jdbc/reference/isautoincrement-method-sqlserverresultsetmetadata.md)|Указывает, производится ли автоматическая нумерация указанного столбца, что делает его доступным только для чтения.|  
|[isCaseSensitive](../../../connect/jdbc/reference/iscasesensitive-method-sqlserverresultsetmetadata.md)|Указывает, учитывается ли регистр символов для столбца.|  
|[isCurrency](../../../connect/jdbc/reference/iscurrency-method-sqlserverresultsetmetadata.md)|Указывает, содержит ли указанный столбец значения денежных сумм.|  
|[isDefinitelyWritable](../../../connect/jdbc/reference/isdefinitelywritable-method-sqlserverresultsetmetadata.md)|Указывает, будет ли запись в указанный столбец наверняка успешной.|  
|[isNullable](../../../connect/jdbc/reference/isnullable-method-sqlserverresultsetmetadata.md)|Указывает допустимость значений NULL для указанного столбца.|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverresultsetmetadata.md)|Указывает, является ли указанный столбец наверняка недоступным для чтения.|  
|[isSearchable](../../../connect/jdbc/reference/issearchable-method-sqlserverresultsetmetadata.md)|Указывает, может ли указанный столбец использоваться в предложении SQL WHERE.|  
|[isSigned](../../../connect/jdbc/reference/issigned-method-sqlserverresultsetmetadata.md)|Указывает, являются ли значения в указанном столбце числами со знаком.|  
|[isSparseColumnSet](../../../connect/jdbc/reference/issparsecolumnset-method-sqlserverresultsetmetadata.md)|Указывает, является ли столбец из результирующего набора набором разреженных столбцов.|  
|[isWritable](../../../connect/jdbc/reference/iswritable-method-sqlserverresultsetmetadata.md)|Указывает, возможна ли успешная запись в указанный столбец.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|java.sql.Wrapper|isWrapperFor, unwrap|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  

