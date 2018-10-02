---
title: Метод getFunctionColumns (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 287a05727bf62de813afec4ad285ef47f3b65943
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47801642"
---
# <a name="getfunctioncolumns-method-sqlserverdatabasemetadata"></a>Метод getFunctionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание параметров и возвращаемого типа системной или пользовательской функции указанного каталога.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public ResultSet getFunctionColumns(java.lang.String catalog,  
                       java.lang.String schemaPattern,  
                       java.lang.String functionNamePattern  
                       java.lang.String columnNamePattern)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога. Если это пустая строка, то результат включает функции, доступные без каталога. Если это значение **NULL**, то имя каталога не используется для поиска.  
  
 *schemaPattern*  
  
 Значение типа **String**, содержащее шаблон имени схемы. Если это пустая строка, то результат включает функции, доступные без схемы. Если это значение **NULL**, то имя схемы не используется для поиска.  
  
 *functionNamePattern*  
  
 Значение типа **String**, содержащее имя функции.  
  
 *columnNamePattern*  
  
 Значение типа **String**, содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFunctionColumns указывается с помощью метода getFunctionColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод возвращает только те функции и параметры, которые соответствуют указанному имени@@@ схемы, имени функции, имени параметра в указанном каталоге  
  
 Каждая строка в результирующем наборе содержит следующие столбцы для описания параметра, описания столбца или возвращаемого типа.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**String**|Имя базы данных, в которой находится указанная функция.|  
|FUNCTION_SCHEM|**String**|Имя@@@ схемы для функции.|  
|FUNCTION_NAME|**String**|Имя функции.|  
|COLUMN_NAME|**String**|Имя параметра или столбца.|  
|COLUMN_TYPE|**short**|**Тип столбца. Может быть одним из указанных далее значений.**<br /><br /> functionColumnUnknown (0): неизвестный тип.<br /><br /> functionColumnIn (1): входной параметр.<br /><br /> functionColumnInOut (2): входной/выходной параметр.<br /><br /> functionColumnOut (3): выходной параметр.<br /><br /> functionReturn (4): значение, возвращаемое функцией.<br /><br /> functionColumnResult (5): параметр или столбец представляет собой столбец в результирующем наборе.|  
|DATA_TYPE|**smallint**|Значение типа данных SQL из Java.sql.Types.|  
|TYPE_NAME|**String**|Имя типа данных.|  
|PRECISION|**int**|Общее количество значащих цифр.|  
|LENGTH|**int**|Длина данных в байтах.|  
|SCALE|**short**|Количество цифр справа от десятичной запятой.|  
|RADIX|**short**|Основание системы счисления для числовых типов.|  
|NULLABLE|**short**|Показывает, может ли возвращаемое значение или параметр содержать значение **NULL**.<br /><br /> **Может быть одним из указанных далее значений.**<br /><br /> functionNoNulls (0): значение NULL недопустимо.<br /><br /> functionNullable (1): значение NULL допустимо.<br /><br /> functionNullableUnknown (2): неизвестно.|  
|REMARKS|**String**|Примечания по параметру или столбцу.|  
|COLUMN_DEF|**String**|Значение по умолчанию для столбца.<br /><br /> **Примечание**. Эти данные доступны только для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и определяются драйвером JDBC.|  
|SQL_DATA_TYPE|**smallint**|Этот столбец содержит то же значение, что и столбец **DATA_TYPE**, за исключением типов данных **datetime** и ISO **interval**.<br /><br /> **Примечание**. Эти данные доступны только для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и определяются драйвером JDBC.|  
|SQL_DATETIME_SUB|**smallint**|Дополнительный код **datetime** ISO **interval**, если значение **SQL_DATA_TYPE** равно **SQL_DATETIME** или **SQL_INTERVAL**. Для типов данных, отличных от **datetime** и ISO **интервал**, этот столбец равен NULL.<br /><br /> **Примечание**. Эти данные доступны только для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и определяются драйвером JDBC.|  
|CHAR_OCTET_LENGTH|**int**|Максимальная длина значений символьных и двоичных параметров или столбцов. Для остальных типов данных имеет значение равное NULL.|  
|ORDINAL_POSITION|**int**|Для входных или выходных параметров представляет позицию начинающуюся с 1<br /><br /> Для результирующего набора столбцов представляет позицию столбца в результирующем наборе начинающуюся с 1.<br /><br /> Для возвращаемого значения имеет значение равное 0.|  
|IS_NULLABLE|**String**|Определяет допустимость значений NULL для параметра или столбца.<br /><br /> Может иметь одно из следующих значений.<br /><br /> **YES**: параметр или столбец могут содержать значения NULL.<br /><br /> **NO**: параметр или столбец не могут содержать значения NULL.<br /><br /> Пустая строка (""): неизвестно.|  
|SS_TYPE_CATALOG_NAME|**String**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_TYPE_SCHEMA_NAME|**String**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_CATALOG_NAME|**String**|Определяемый пользователем тип с полным именем.|  
|SS_UDT_SCHEMA_NAME|**String**|Имя каталога, в котором определено имя коллекции схем XML. Если не удается найти имя каталога, то эта переменная содержит пустую строку.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Имя схемы, в которой определено имя коллекции схем XML. Если не удается найти имя схемы, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Имя коллекции схем XML. Если не удается найти имя, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_DATA_TYPE|**tinyint**|Тип данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используемый расширенными хранимыми процедурами.<br /><br /> **Примечание**. Дополнительные сведения о типах данных, возвращаемых [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], см. в разделе "Типы данных (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
