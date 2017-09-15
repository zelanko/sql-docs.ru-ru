---
title: "Метод getColumnPrivileges (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.getColumnPrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ab6a671-9573-4b95-8c23-364306c60d25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1db7a72e555114711151e82281a4890f34d75fe6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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
 *каталог*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *схемы*  
  
 Объект **строка** , содержащее имя схемы.  
  
 *table*  
  
 Объект **строка** , содержащее имя таблицы.  
  
 *номер столбца*  
  
 Объект **строка** , содержащее шаблон имени столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getColumnPrivileges указывается с помощью метода getColumnPrivileges в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getColumnPrivileges возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Строковые значения**|Имя каталога.|  
|TABLE_SCHEM|**Строковые значения**|Имя схемы для таблицы.|  
|TABLE_NAME|**Строковые значения**|Имя таблицы.|  
|COLUMN_NAME|**Строковые значения**|Имя столбца.|  
|GRANTOR|**Строковые значения**|Объект, предоставляющий доступ.|  
|GRANTEE|**Строковые значения**|Объект, получающий доступ.|  
|PRIVILEGE|**Строковые значения**|Тип предоставляемого доступа.|  
|IS_GRANTABLE|**Строковые значения**|Указывает, разрешается ли получателю прав предоставлять доступ другим пользователям.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getColumnPrivileges см. в разделе «sp_column_privileges (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует метод getColumnPrivileges для возврата прав доступа для столбца FirstName в таблице Person.Contact [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
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
  
  
