---
title: "Метод getColumns (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f173fa5d-e114-4a37-a5c4-2baad9ff3af1
caps.latest.revision: 39
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 75d9ab3fb70f854e56df0c659275a2983a8487ff
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcolumns-method-sqlserverdatabasemetadata"></a>Метод getColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов таблицы, доступных в указанном каталоге.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getColumns(java.lang.String catalog,  
                                     java.lang.String schema,  
                                     java.lang.String table,  
                                     java.lang.String col)  
```  
  
#### <a name="parameters"></a>Параметры  
 *каталог*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *схемы*  
  
 Объект **строка** , содержащее шаблон имени схемы.  
  
 *table*  
  
 Объект **строка** , содержащее шаблон имени таблицы.  
  
 *номер столбца*  
  
 Объект **строка** , содержащее шаблон имени столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getColumns указывается с помощью метода getColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getColumns возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Строковые значения**|Имя каталога.|  
|TABLE_SCHEM|**Строковые значения**|Имя схемы для таблицы.|  
|TABLE_NAME|**Строковые значения**|Имя таблицы.|  
|COLUMN_NAME|**Строковые значения**|Имя столбца.|  
|DATA_TYPE|**smallint**|Тип данных SQL из java.sql.Types.|  
|TYPE_NAME|**Строковые значения**|Имя типа данных.|  
|COLUMN_SIZE|**int**|Точность столбца.|  
|BUFFER_LENGTH|**smallint**|Размер передаваемых данных.|  
|DECIMAL_DIGITS|**smallint**|Масштаб столбца.|  
|NUM_PREC_RADIX|**smallint**|Основание системы счисления столбца.|  
|NULLABLE|**smallint**|Указывает, допускает ли столбец значения NULL. Может иметь одно из следующих значений.<br /><br /> columnNoNulls (0)<br /><br /> columnNullable (1)|  
|REMARKS|**Строковые значения**|Примечания, связанные со столбцом.<br /><br /> **Примечание:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] всегда возвращает значение null для этого столбца.  |  
|COLUMN_DEF|**Строковые значения**|Значение по умолчанию для столбца.|  
|SQL_DATA_TYPE|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец содержит то же значение, что и столбец DATA_TYPE, за исключением типа данных datetime и типа данных SQL-92 interval. Этот столбец всегда возвращает значение.|  
|SQL_DATETIME_SUB|**smallint**|Код подтипа для datetime и интервальных типов данных SQL-92. Для других типов данных этот столбец возвращает значение NULL.|  
|CHAR_OCTET_LENGTH|**int**|Максимальный размер столбца в байтах.|  
|ORDINAL_POSITION|**int**|Индекс столбца в таблице.|  
|IS_NULLABLE|**Строковые значения**|Указывает, допускает ли столбец значения NULL.|  
|SS_IS_SPARSE|**smallint**|Если столбец является разреженным, это имеет значение 1. в противном случае — 0. <sup>1</sup>|  
|SS_IS_COLUMN_SET|**smallint**|Если столбец является разреженным столбцом column_set, то значение 1. В противном случае — значение 0. <sup>1</sup>|  
|SS_IS_COMPUTED|**smallint**|Указывает, является ли столбец в TABLE_TYPE вычисляемым. <sup>1</sup>|  
|IS_AUTOINCREMENT|**Строковые значения**|Значение «YES», если в столбце действует автоувеличение. Значение «NO», если в столбце не действует автоувеличение. Пустая строка («»), если драйверу не удается определить, действует ли в столбце автоувеличение. <sup>1</sup>|  
|SS_UDT_CATALOG_NAME|**Строковые значения**|Имя каталога, содержащего определяемый пользователем тип. <sup>1</sup>|  
|SS_UDT_SCHEMA_NAME|**Строковые значения**|Имя схемы, содержащей определяемый пользователем тип. <sup>1</sup>|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**Строковые значения**|Определяемый пользователем тип с полным именем. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**Строковые значения**|Имя каталога, в котором определено имя коллекции схем XML. Если не удается найти имя каталога, то эта переменная содержит пустую строку. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**Строковые значения**|Имя схемы, в которой определено имя коллекции схем XML. Если не удается найти имя схемы, значением является пустая строка. <sup>1</sup>|  
|SS_XML_SCHEMACOLLECTION_NAME|**Строковые значения**|Имя коллекции схем XML. Если не удается найти имя, значением является пустая строка. <sup>1</sup>|  
|SS_DATA_TYPE|**tinyint**|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Тип данных, используемый расширенными хранимыми процедурами.<br /><br /> **Примечание** Дополнительные сведения о типах данных, возвращенных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)], в разделе «Типы данных (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.|  
  
 (1) этот столбец не будет присутствовать в том случае, если вы подключаетесь к [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)].  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getColumns см. в разделе «sp_columns (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
 В [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC, вы увидите следующие изменения в новых версиях драйвера JDBC:  
  
 В столбце DATA_TYPE имеются следующие изменения.  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Тип данных|Тип возвращаемого значения в драйвере JDBC 2.0 (или, если подключение к [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)]) и связанная Числовая константа|Тип возвращаемого значения в версии 3.0 драйвера JDBC при подключении к [!INCLUDE[ssKatmai](../../../includes/sskatmai_md.md)] или более поздней версии|  
|-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|  
|Определяемый пользователем тип размером более 8 КБ|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geography|LONGVARBINARY (-4)|VARBINARY (-3)|  
|geometry|LONGVARBINARY (-4)|VARBINARY (-3)|  
|varbinary(max)|LONGVARBINARY (-4)|VARBINARY (-3)|  
|nvarchar(max)|LONGVARCHAR (-1) или LONGNVARCHAR (JDBC 4) (-16)|VARCHAR (12) или NVARCHAR (JDBC 4) (-9)|  
|varchar(max)|LONGVARCHAR (-1)|VARCHAR (12)|  
|time|VARCHAR (12) или NVARCHAR (JDBC 4) (-9)|TIME (-154)|  
|date|VARCHAR (12) или NVARCHAR (JDBC 4) (-9)|DATE (91)|  
|datetime2|VARCHAR (12) или NVARCHAR (JDBC 4) (-9)|TIMESTAMP (93)|  
|datetimeoffset|VARCHAR (12) или NVARCHAR (JDBC 4) (-9)|microsoft.sql.Types.DATETIMEOFFSET  (-155)|  
  
 В столбце COLUMN_SIZE выполнены следующие изменения.  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Тип данных|Тип возвращаемого значения в драйвере JDBC 2.0|Тип возвращаемого значения в драйвере JDBC 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|nvarchar(max)|1073741823|2147483647 (метаданные базы данных)|  
|xml|1073741823|2147483647 (метаданные базы данных)|  
|Определяемый пользователем тип размером 8 КБ и менее|8 КБ (результирующий набор и метаданные параметров)|Фактический размер, возвращенный хранимой процедурой.|  
|time||Длина строкового представления типа в символах с учетом максимально допустимой точности для долей секунды.|  
|date||Аналогично типу time|  
|datetime2||Аналогично типу time|  
|datetimeoffset||Аналогично типу time|  
  
 В столбце BUFFER_LENGTH выполнены следующие изменения.  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Тип данных|Тип возвращаемого значения в драйвере JDBC 2.0|Тип возвращаемого значения в драйвере JDBC 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|Определяемый пользователем тип размером более 8 КБ||2147483647|  
  
 В столбце TYPE_NAME выполнены следующие изменения.  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Тип данных|Тип возвращаемого значения в драйвере JDBC 2.0|Тип возвращаемого значения в драйвере JDBC 3.0|  
|-------------------------------------------------------------------|------------------------------------|------------------------------------|  
|varchar(max)|text|varchar|  
|varbinary(max)|image|varbinary|  
  
 В столбце DECIMAL_DIGITS выполнены следующие изменения.  
  
|Тип [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]|JDBC Driver 2.0|JDBC Driver 3.0|  
|--------------------------------------------------------------|---------------------|---------------------|  
|time|null|7 (или меньшее значение, если указано)|  
|date|null|null|  
|datetime2|null|7 (или меньшее значение, если указано)|  
|datetimeoffset|null|7 (или меньшее значение, если указано)|  
  
 В столбце SQL_DATA_TYPE выполнены следующие изменения.  
  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Тип данных|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Значение данных 2008 в драйвере JDBC 2.0|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]Значение данных 2008 в драйвере JDBC 3.0|  
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|  
|varchar(max)|-10|-9|  
|nvarchar(max)|-1|-9|  
|xml|-10|-152|  
|Определяемый пользователем тип размером 8 КБ и менее|–3|-151|  
|Определяемый пользователем тип размером более 8 КБ|Недоступно в версии 2.0 драйвера JDBC|-151|  
|geography|-4|-151|  
|geometry|-4|-151|  
|hierarchyid|-4|-151|  
|time|-9|92|  
|date|-9|91|  
|datetime2|-9|93|  
|datetimeoffset|-9|-155|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getColumns для возврата сведений о таблице Person.Contact [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
import java.sql.*;  
public class c1 {  
   public static void main(String[] args) {  
      String connectionUrl = "jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedsecurity=true";  
  
      Connection con = null;  
      Statement stmt = null;  
      ResultSet rs = null;  
  
      try {  
         Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
         con = DriverManager.getConnection(connectionUrl);  
         DatabaseMetaData dbmd = con.getMetaData();  
         rs = dbmd.getColumns("AdventureWorks", "Person", "Contact", "FirstName");  
  
         ResultSet r = dbmd.getColumns(null, null, "Contact", null);  
         ResultSetMetaData rm = r.getMetaData();   
         int noofcols = rm.getColumnCount();  
  
         if (r.next())  
            for (int i = 0 ; i < noofcols ; i++ )  
            System.out.println(rm.getColumnName( i + 1 ) + ": \t\t" + r.getString( i + 1 ));  
      }  
  
      catch (Exception e) {}  
      finally {}  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
