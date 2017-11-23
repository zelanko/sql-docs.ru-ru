---
title: "Метод getTableTypes (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getTableTypes
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e0f5dc57-07b8-4811-ab1a-80a524bfdb42
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1d4bda5e46fac353d28458eabb2090eb3915e84c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="gettabletypes-method-sqlserverdatabasemetadata"></a>Метод getTableTypes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает табличные типы, доступные в текущей базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getTableTypes()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTableTypes указывается с помощью метода getTableTypes в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getTableTypes возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_TYPE|**Строковые значения**|Табличный тип.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getTableTypes см. в разделе «sp_tables (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Следующий пример демонстрирует метод getTableTypes используется для возврата сведений о типе таблиц в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных, учитывая, что база данных указывается в строке соединения.  
  
```  
public static void executeGetTableTypes(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTableTypes();  
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
  
  
