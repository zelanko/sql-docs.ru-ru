---
title: Метод getCatalogs (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCatalogs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7f8bd0f1-f340-4bb9-b559-0a6176124033
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c63d7ea85cd36f6cbc6f536e7fc7f9f20def2ad2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803956"
---
# <a name="getcatalogs-method-sqlserverdatabasemetadata"></a>Метод getCatalogs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имена каталогов, доступных на подключенном сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getCatalogs()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCatalogs определяется методом getCatalogs в интерфейсе java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  В SQL Azure, следует подключиться к базе данных master для вызова **SQLServerDatabaseMetaData.getCatalogs**. SQL Azure не поддерживает возврат всего набора каталогов из пользовательских баз данных. **SQLServerDatabaseMetaData.getCatalogs** использует для получения каталогов представление sys.databases. См. обсуждение разрешений в [sys.database_usage (база данных SQL Azure)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md) для понимания **SQLServerDatabaseMetaData.getCatalogs** поведение в SQL Azure.  
  
 Результирующий набор, возвращаемый методом getCatalogs, включает следующие данные:  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Имя каталога, включая системные базы данных [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getCatalogs для возвращения имен всех баз данных, содержащихся в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включая системные базы данных.  
  
```  
public static void executeGetCatalogs(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCatalogs();  
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
  
  
