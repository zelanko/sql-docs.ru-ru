---
title: "Метод getTypeInfo (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.getTypeInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 23208f01-c1bf-4235-b29c-9051d3df59a3
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4cce857630acc646d10da1ede7aa9139d62b6039
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="gettypeinfo-method-sqlserverdatabasemetadata"></a>Метод getTypeInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает описание всех стандартных типов SQL, которые поддерживаются в текущей базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getTypeInfo()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTypeInfo указывается с помощью метода getTypeInfo в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getTypeInfo возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TYPE_NAME|**Строковые значения**|Имя типа данных.|  
|DATA_TYPE|**короткий**|Тип данных SQL из java.sql.Types.|  
|PRECISION|**int**|Общее количество значащих цифр.|  
|LITERAL_PREFIX|**Строковые значения**|Символ или символы, используемые перед константой.|  
|LITERAL_SUFFIX|**Строковые значения**|Символ или символы, используемые для удаления константы.|  
|CREATE_PARAMS|**Строковые значения**|Описание создания параметров типа данных.|  
|NULLABLE|**короткий**|Указывает, может ли столбец содержать значение NULL. Может иметь одно из следующих значений.<br /><br /> typeNoNulls (0)<br /><br /> typeNullable (1)<br /><br /> typeNullableUnknown (2)|  
|CASE_SENSITIVE|**boolean**|Указывает, учитывается ли регистр символов для типа данных. «**true**«Если тип — с учетом регистра, в противном случае —»**false**».|  
|SEARCHABLE|**короткий**|Указывает, может ли указанный столбец использоваться в предложении SQL WHERE. Может иметь одно из следующих значений.<br /><br /> typePredNone (0)<br /><br /> typePredChar (1)<br /><br /> typePredBasic (2)<br /><br /> typeSeachable (3)|  
|UNSIGNED_ATTRIBUTE|**boolean**|Указывает знак типа данных. «**true**«Если тип без знака, в противном случае —»**false**».|  
|FIXED_PREC_SCALE|**boolean**|Указывает, что тип данных может быть значением типа money. "**true**", если тип данных является значением типа money в противном случае — "**false**».|  
|AUTO_INCREMENT|**boolean**|Указывает, что тип данных может быть автоматически увеличен. «**true**«Если тип может быть автоматически увеличен; в противном случае —»**false**».|  
|LOCAL_TYPE_NAME|**Строковые значения**|Локализованное имя типа данных.|  
|MINIMUM_SCALE|**короткий**|Максимальное число цифр справа от десятичной запятой.|  
|MAXIMUM_SCALE|**короткий**|Минимальное число цифр справа от десятичной запятой.|  
|SQL_DATA_TYPE|**int**|Не поддерживается драйвером JDBC.|  
|SQL_DATETIME_SUB|**int**|Не поддерживается драйвером JDBC.|  
|NUM_PREC_RADIX|**int**|Количество битов или цифр для расчета максимального числа, которое может содержаться в столбце.|  
|INTERVAL_PRECISION|**smallint**|Значение точности интервала.|  
|USERTYPE|**smallint**|**Usertype** значение из **systypes** таблицы. Дополнительные сведения см. в электронной документации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getTypeInfo см. в разделе «sp_datatype_info (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getTypeInfo для возврата сведений о типах данных, используемых в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005_md.md)] (или более поздней версии) базы данных.  
  
```  
public static void executeGetTypeInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTypeInfo();  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

