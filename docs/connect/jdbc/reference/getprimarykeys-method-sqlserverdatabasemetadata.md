---
title: Метод getPrimaryKeys (SQLServerDatabaseMetaData) | Документы Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getPrimaryKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebfe236a-dc02-493e-a3ab-5353d3769e36
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c134116a9c39fd4019b67a554982dd30866c110
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getprimarykeys-method-sqlserverdatabasemetadata"></a>Метод getPrimaryKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов первичного ключа заданной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getPrimaryKeys(java.lang.String cat,  
                                         java.lang.String schema,  
                                         java.lang.String table)  
```  
  
#### <a name="parameters"></a>Параметры  
 *CAT*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *schema*  
  
 Объект **строка** , содержащее имя схемы.  
  
 *table*  
  
 Объект **строка** , содержащее имя таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getPrimaryKeys указывается с помощью метода getPrimaryKeys в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getPrimaryKeys возвращает результирующий набор будет содержать следующие сведения:  
  
|Название|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|Строковые значения|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|Строковые значения|Схема таблицы.|  
|TABLE_NAME|Строковые значения|Имя таблицы.|  
|COLUMN_NAME|Строковые значения|Имя столбца.|  
|KEY_SEQ|short|Порядковый номер столбца в первичном ключе из нескольких столбцов.|  
|PK_NAME|Строковые значения|Имя первичного ключа.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getPrimaryKeys см. в разделе «sp_pkeys (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getPrimaryKeys для возврата сведений о первичных ключах таблицы Person.Contact в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
public static void executeGetPrimaryKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getPrimaryKeys("AdventureWorks", "Person", "Contact");  
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
  
  
