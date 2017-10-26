---
title: "Метод getFunctionColumns (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2b0e0f7-717c-48e6-bcd2-a325d938a833
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1508d70610c47116a4aaf58063b0f4196459d3e4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
 *каталог*  
  
 Объект **строка** , содержащее имя каталога. Если это пустая строка, то результат включает функции, доступные без каталога. Если это **null**, имя каталога не используется для поиска.  
  
 *schemaPattern*  
  
 Объект **строка** , содержащее шаблон имени схемы. Если это пустая строка, то результат включает функции, доступные без схемы. Если это **null**, имя схемы не используется для поиска.  
  
 *functionNamePattern*  
  
 Объект **строка** , содержащее имя функции.  
  
 *columnNamePattern*  
  
 Объект **строка** , содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getFunctionColumns указывается с помощью метода getFunctionColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Этот метод возвращает только те функции и параметры, которые соответствуют указанному имени@@@ схемы, имени функции, имени параметра в указанном каталоге  
  
 Каждая строка в результирующем наборе содержит следующие столбцы для описания параметра, описания столбца или возвращаемого типа.  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|FUNCTION_CAT|**Строковые значения**|Имя базы данных, в которой находится указанная функция.|  
|FUNCTION_SCHEM|**Строковые значения**|Имя@@@ схемы для функции.|  
|FUNCTION_NAME|**Строковые значения**|Имя функции.|  
|COLUMN_NAME|**Строковые значения**|Имя параметра или столбца.|  
|COLUMN_TYPE|**короткий**|**Тип столбца. Он может принимать одно из следующих значений:**<br /><br /> functionColumnUnknown (0): неизвестный тип.<br /><br /> functionColumnIn (1): входной параметр.<br /><br /> functionColumnInOut (2): входной/выходной параметр.<br /><br /> functionColumnOut (3): выходной параметр.<br /><br /> functionReturn (4): значение, возвращаемое функцией.<br /><br /> functionColumnResult (5): параметр или столбец представляет собой столбец в результирующем наборе.|  
|DATA_TYPE|**smallint**|Значение из Java.sql.Types тип данных SQL.|  
|TYPE_NAME|**Строковые значения**|Имя типа данных.|  
|PRECISION|**int**|Общее количество значащих цифр.|  
|LENGTH|**int**|Длина данных в байтах.|  
|SCALE|**короткий**|Количество цифр справа от десятичной запятой.|  
|RADIX|**короткий**|Основание системы счисления для числовых типов.|  
|NULLABLE|**короткий**|Указывает, если параметра или возвращаемого значения может содержать **null** значение.<br /><br /> **Он может принимать одно из следующих значений:**<br /><br /> functionNoNulls (0): значение NULL недопустимо.<br /><br /> functionNullable (1): значение NULL допустимо.<br /><br /> functionNullableUnknown (2): неизвестно.|  
|REMARKS|**Строковые значения**|Примечания по параметру или столбцу.|  
|COLUMN_DEF|**Строковые значения**|Значение по умолчанию для столбца.<br /><br /> **Примечание:** эта информация доступна с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и является драйвером JDBC.|  
|SQL_DATA_TYPE|**smallint**|Этот столбец содержит то же, как **DATA_TYPE** столбца, за исключением **datetime** и ISO **интервал** типов данных.<br /><br /> **Примечание:** эта информация доступна с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и является драйвером JDBC.|  
|SQL_DATETIME_SUB|**smallint**|**Datetime** ISO **интервал** Доп. Если значение **SQL_DATA_TYPE** — **SQL_DATETIME** или **SQL_INTERVAL**. Для типов данных, отличный от **datetime** и ISO **интервал**, этот столбец равен NULL.<br /><br /> **Примечание:**эта информация доступна с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] и является драйвером JDBC.|  
|CHAR_OCTET_LENGTH|**int**|Максимальная длина значений символьных и двоичных параметров или столбцов. Для остальных типов данных имеет значение равное NULL.|  
|ORDINAL_POSITION|**int**|Для входных или выходных параметров представляет позицию начинающуюся с 1<br /><br /> Для результирующего набора столбцов представляет позицию столбца в результирующем наборе начинающуюся с 1.<br /><br /> Для возвращаемого значения имеет значение равное 0.|  
|IS_NULLABLE|**Строковые значения**|Определяет допустимость значений NULL для параметра или столбца.<br /><br /> Может иметь одно из следующих значений.<br /><br /> **Да**: параметр или столбец могут содержать значения NULL.<br /><br /> **НЕ**: параметр или столбец не может содержать значения NULL.<br /><br /> Пустая строка (""): неизвестно.|  
|SS_TYPE_CATALOG_NAME|**Строковые значения**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_TYPE_SCHEMA_NAME|**Строковые значения**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_CATALOG_NAME|**Строковые значения**|Определяемый пользователем тип с полным именем.|  
|SS_UDT_SCHEMA_NAME|**Строковые значения**|Имя каталога, в котором определено имя коллекции схем XML. Если не удается найти имя каталога, то эта переменная содержит пустую строку.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**Строковые значения**|Имя схемы, в которой определено имя коллекции схем XML. Если не удается найти имя схемы, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**Строковые значения**|Имя коллекции схем XML. Если не удается найти имя, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**Строковые значения**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_XML_SCHEMACOLLECTION_NAME|**Строковые значения**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_DATA_TYPE|**tinyint**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Тип данных, используемый расширенными хранимыми процедурами.<br /><br /> **Примечание** Дополнительные сведения о типах данных, возвращенных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], в разделе «Типы данных (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.|  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

