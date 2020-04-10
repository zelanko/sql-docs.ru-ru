---
title: Метод getCatalogs (SQLServerDatabaseMetaData) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2a813a04f11a9ad74e4ceec2663e9d7f812d5c3d
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924997"
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
>  В Базе данных SQL Azure нужно установить соединение с базой данных master, чтобы вызвать **SQLServerDatabaseMetaData.getCatalogs**. SQL Azure не поддерживает возврат всего набора каталогов из пользовательских баз данных. **SQLServerDatabaseMetaData.getCatalogs** использует представление sys.databases для получения каталогов. Обсуждение разрешений см. в статье [sys.database_usage (База данных SQL Azure)](../../../relational-databases/system-catalog-views/sys-database-usage-azure-sql-database.md) поможет вам понять поведение **SQLServerDatabaseMetaData.getCatalogs** в Базе данных SQL Azure.  
  
 Результирующий набор, возвращаемый методом getCatalogs, включает следующие данные:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Имя каталога, включая системные базы данных в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getCatalogs для получения имен всех баз данных, содержащихся в [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], включая системные базы данных.  
  
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
  
  
