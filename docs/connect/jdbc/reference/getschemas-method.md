---
title: "Метод getSchemas () | Документы Microsoft"
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
- SQLServerDatabaseMetaData.getSchemas
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: adba0ee6-ff6d-4215-b646-62c735be3fe9
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a66767527b1fb7bfe2c3b3f03414ef643676b4e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getschemas-method-"></a>Метод getSchemas ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имена схем, доступных в текущей базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getSchemas()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSchemas указывается с помощью метода getSchemas в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращенный методом getSchemas содержит следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**Строковые значения**|Имя схемы.|  
|TABLE_CATALOG|**Строковые значения**|Имя каталога для схемы.|  
  
 Результаты упорядочиваются по значениям TABLE_CATALOG, затем по значениям TABLE_SCHEM. Каждая строка первым столбцом содержит TABLE_SCHEM, а вторым — TABLE_CATALOG.  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getSchemas см. в разделе «sys.schemas (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getSchemas для возврата сведений о каталоге и его имен связанную схему, в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] при аргумент соединения указывает базу данных для использования.  
  
```  
public static void executeGetSchemas(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getSchemas();  
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
  
  

