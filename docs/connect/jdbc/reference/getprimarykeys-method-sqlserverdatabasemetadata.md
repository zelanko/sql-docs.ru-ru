---
title: Метод getPrimaryKeys (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getPrimaryKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ebfe236a-dc02-493e-a3ab-5353d3769e36
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 73c1f5576d440cc9c98708882b98c5b6d9ceff42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47809982"
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
 *cat*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *schema*  
  
 Значение типа **String**, содержащее имя схемы.  
  
 *table*  
  
 Значение типа **String**, содержащее имя таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getPrimaryKeys указывается с помощью метода getPrimaryKeys в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getPrimaryKeys, включает следующие данные.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|String|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|String|Схема таблицы.|  
|TABLE_NAME|String|Имя таблицы.|  
|COLUMN_NAME|String|Имя столбца.|  
|KEY_SEQ|short|Порядковый номер столбца в первичном ключе из нескольких столбцов.|  
|PK_NAME|String|Имя первичного ключа.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getPrimaryKeys, см. в разделе "sp_pkeys (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Следующий пример показывает использование метода getPrimaryKeys для возврата сведений о первичных ключах таблицы Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
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
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
