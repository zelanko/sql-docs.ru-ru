---
title: "Метод getTables (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9bbf35aeec7b5626b380fc654995d181fe124811
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="gettables-method-sqlserverdatabasemetadata"></a>Метод getTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание таблиц, доступных в заданном каталоге, схеме или по шаблону имени таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getTables(java.lang.String catalog,  
                                    java.lang.String schema,  
                                    java.lang.String table,  
                                    java.lang.String[] types)  
```  
  
#### <a name="parameters"></a>Параметры  
 *каталог*  
  
 Объект **строка** , содержащее имя каталога. Задание значения NULL для этого параметра указывает на то, что имя каталога использовать не нужно.  
  
 *схемы*  
  
 Объект **строка** , содержащее шаблон имени схемы. Задание значения NULL для этого параметра указывает на то, что имя схемы использовать не нужно.  
  
 *имя_таблицы*  
  
 Объект **строка** , содержащее шаблон имени таблицы.  
  
 *типы*  
  
 Массив строковых значений, содержащий включаемые типы таблиц. Значение NULL показывает, что нужно включать все типы таблиц.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTables задается методом gettables в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом gettables будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Строковые значения**|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|**Строковые значения**|Имя схемы для таблицы.|  
|TABLE_NAME|**Строковые значения**|Имя таблицы.|  
|TABLE_TYPE|**Строковые значения**|Табличный тип.|  
|REMARKS|**Строковые значения**|Описание таблицы.<br /><br /> **Примечание:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] не возвращает значения для этого столбца.|  
|TYPE_CAT|**Строковые значения**|Не поддерживается драйвером JDBC.|  
|TYPE_SCHEM|**Строковые значения**|Не поддерживается драйвером JDBC.|  
|TYPE_NAME|**Строковые значения**|Не поддерживается драйвером JDBC.|  
|SELF_REFERENCING_COL_NAME|**Строковые значения**|Не поддерживается драйвером JDBC.|  
|REF_GENERATION|**Строковые значения**|Не поддерживается драйвером JDBC.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом gettables см. в разделе «sp_tables (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getTables для возврата сведений о описание таблицы для таблицы Person.Contact в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
public static void executeGetTables(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTables("AdventureWorks", "Person", "Contact", null);  
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
  
  

