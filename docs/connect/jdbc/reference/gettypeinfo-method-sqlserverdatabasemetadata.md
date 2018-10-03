---
title: Метод getTypeInfo (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTypeInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 23208f01-c1bf-4235-b29c-9051d3df59a3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 40ca58f33dec39a1ec6d39979c7f6f0103acf8b2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682722"
---
# <a name="gettypeinfo-method-sqlserverdatabasemetadata"></a>Метод getTypeInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает описание всех стандартных типов SQL, которые поддерживаются в текущей базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getTypeInfo()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTypeInfo указывается с помощью метода getTypeInfo в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getTypeInfo, включает следующие данные:  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TYPE_NAME|**String**|Имя типа данных.|  
|DATA_TYPE|**short**|Тип данных SQL из java.sql.Types.|  
|PRECISION|**int**|Общее количество значащих цифр.|  
|LITERAL_PREFIX|**String**|Символ или символы, используемые перед константой.|  
|LITERAL_SUFFIX|**String**|Символ или символы, используемые для удаления константы.|  
|CREATE_PARAMS|**String**|Описание создания параметров типа данных.|  
|NULLABLE|**short**|Указывает, может ли столбец содержать значение NULL. Может иметь одно из следующих значений.<br /><br /> typeNoNulls (0)<br /><br /> typeNullable (1)<br /><br /> typeNullableUnknown (2)|  
|CASE_SENSITIVE|**boolean**|Указывает, учитывается ли регистр символов для типа данных. Значение "**true**", если регистр символов учитывается, в противном случае — значение "**false**".|  
|SEARCHABLE|**short**|Указывает, может ли указанный столбец использоваться в предложении SQL WHERE. Может иметь одно из следующих значений.<br /><br /> typePredNone (0)<br /><br /> typePredChar (1)<br /><br /> typePredBasic (2)<br /><br /> typeSeachable (3)|  
|UNSIGNED_ATTRIBUTE|**boolean**|Указывает знак типа данных. Значение "**true**", если тип данных не имеет знака, в противном случае — значение "**false**".|  
|FIXED_PREC_SCALE|**boolean**|Указывает, что тип данных может быть значением типа money. Значение "**true**", если тип данных является значением типа money, в противном случае — значение "**false**".|  
|AUTO_INCREMENT|**boolean**|Указывает, что тип данных может быть автоматически увеличен. Значение "**true**", если тип данных может быть автоматически увеличен, в противном случае — значение "**false**".|  
|LOCAL_TYPE_NAME|**String**|Локализованное имя типа данных.|  
|MINIMUM_SCALE|**short**|Максимальное число цифр справа от десятичной запятой.|  
|MAXIMUM_SCALE|**short**|Минимальное число цифр справа от десятичной запятой.|  
|SQL_DATA_TYPE|**int**|Не поддерживается драйвером JDBC.|  
|SQL_DATETIME_SUB|**int**|Не поддерживается драйвером JDBC.|  
|NUM_PREC_RADIX|**int**|Количество битов или цифр для расчета максимального числа, которое может содержаться в столбце.|  
|INTERVAL_PRECISION|**smallint**|Значение точности интервала.|  
|USERTYPE|**smallint**|Значение **usertype** из таблицы **systypes**. Дополнительные сведения см. в электронной документации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getTypeInfo, см. в разделе "sp_datatype_info (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Следующий пример показывает использование метода getTypeInfo для возврата сведений о типах данных, используемых в базе данных [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии.  
  
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
  
  
