---
title: Метод getColumnPrivileges (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ae80a8c33f68ad2f3d2c85b1343a5cc0f2b423c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952878"
---
# <a name="getcolumnprivileges-method-sqlserverdatabasemetadata"></a>Метод getColumnPrivileges (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание прав доступа для столбцов в таблице.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getColumnPrivileges(java.lang.String catalog,  
                                              java.lang.String schema,  
                                              java.lang.String table,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Параметры  
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *schema*  
  
 Значение типа **String**, содержащее имя схемы.  
  
 *table*  
  
 Значение типа **String**, содержащее имя таблицы.  
  
 *col*  
  
 Значение типа **String**, содержащее шаблон имени столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getColumnPrivileges определен с помощью метода getColumnPrivileges в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getColumnPrivileges, включает следующие данные.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Имя каталога.|  
|TABLE_SCHEM|**String**|Имя схемы для таблицы.|  
|TABLE_NAME|**String**|Имя таблицы.|  
|COLUMN_NAME|**String**|Имя столбца.|  
|GRANTOR|**String**|Объект, предоставляющий доступ.|  
|GRANTEE|**String**|Объект, получающий доступ.|  
|PRIVILEGE|**String**|Тип предоставляемого доступа.|  
|IS_GRANTABLE|**String**|Указывает, разрешается ли получателю прав предоставлять доступ другим пользователям.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getColumnPrivileges, см. в разделе "sp_column_privileges (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getColumnPrivileges для возврата прав доступа для столбца FirstName в таблице Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetColumnPrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getColumnPrivileges("AdventureWorks", "Person", "Contact", "FirstName");  
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
  
  
