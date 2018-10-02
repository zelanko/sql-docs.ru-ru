---
title: Метод getVersionColumns (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 938cf980a4035684b2e77435d5ab4df9522b4407
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47604012"
---
# <a name="getversioncolumns-method-sqlserverdatabasemetadata"></a>Метод getVersionColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов таблицы, которые автоматически обновляются при обновлении любого значения в строке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getVersionColumns(java.lang.String catalog,  
                                            java.lang.String schema,  
                                            java.lang.String table)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *schema*  
  
 Значение типа **String**, содержащее шаблон имени схемы.  
  
 *table*  
  
 Значение типа **String**, содержащее имя таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getVersionColumns указывается с помощью метода getVersionColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getVersionColumns, включает следующие данные:  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|SCOPE|**short**|Не поддерживается драйвером JDBC.|  
|COLUMN_NAME|**String**|Имя столбца.|  
|DATA_TYPE|**short**|Тип данных SQL из java.sql.Types.|  
|TYPE_NAME|**String**|Имя типа данных.|  
|COLUMN_SIZE|**int**|Точность столбца.|  
|BUFFER_LENGTH|**int**|Длина столбца в байтах.|  
|DECIMAL_DIGITS|**short**|Масштаб столбца.|  
|PSEUDO_COLUMN|**short**|Указывает, является ли столбец псевдостолбцом. Может иметь одно из следующих значений.<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getVersionColumns, см. в разделе "sp_datatype_info (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getVersionColumns для возвращения сведений о столбцах, автоматически обновленных в таблице Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetVersionColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getVersionColumns("AdventureWorks", "Person", "Contact");  
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
  
  
