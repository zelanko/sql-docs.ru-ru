---
title: Метод getVersionColumns (SQLServerDatabaseMetaData) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getVersionColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dd275d3-d9b2-4db7-938a-d4406c940a7a
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 916191363743bd204b6841e1713e92cfeaddd46b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
 Объект **строка** , содержащее имя каталога.  
  
 *schema*  
  
 Объект **строка** , содержащее шаблон имени схемы.  
  
 *table*  
  
 Объект **строка** , содержащее имя таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getVersionColumns указывается с помощью метода getVersionColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getVersionColumns возвращает результирующий набор будет содержать следующие сведения:  
  
|Название|Тип|Описание|  
|----------|----------|-----------------|  
|SCOPE|**короткий**|Не поддерживается драйвером JDBC.|  
|COLUMN_NAME|**String**|Имя столбца.|  
|DATA_TYPE|**короткий**|Тип данных SQL из java.sql.Types.|  
|TYPE_NAME|**String**|Имя типа данных.|  
|COLUMN_SIZE|**int**|Точность столбца.|  
|BUFFER_LENGTH|**int**|Длина столбца в байтах.|  
|DECIMAL_DIGITS|**короткий**|Масштаб столбца.|  
|PSEUDO_COLUMN|**короткий**|Указывает, является ли столбец псевдостолбцом. Может иметь одно из следующих значений.<br /><br /> versionColumnUnknown (0)<br /><br /> versionColumnNotPseudo (1)<br /><br /> versionColumnPseudo (2)|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getVersionColumns см. в разделе «sp_datatype_info (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getVersionColumns для возврата сведений о столбцах, которые автоматически обновляются в таблице Person.Contact [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
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
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
