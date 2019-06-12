---
title: Метод getTables (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTables
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a7514673-3457-4541-9560-28a8284ad9e3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 81cb6429cbf1c3f1dd1d97a0aee9458fff637f15
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779069"
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
 *catalog*  
  
 Значение типа **String**, содержащее имя каталога. Задание значения NULL для этого параметра указывает на то, что имя каталога использовать не нужно.  
  
 *schema*  
  
 Значение типа **String**, содержащее шаблон имени схемы. Задание значения NULL для этого параметра указывает на то, что имя схемы использовать не нужно.  
  
 *tableName*  
  
 Значение типа **String**, содержащее шаблон имени таблицы.  
  
 *types*  
  
 Массив строковых значений, содержащий включаемые типы таблиц. Значение NULL показывает, что нужно включать все типы таблиц.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTables определен с помощью метода getTables в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getTables, включает следующие данные:  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|**String**|Имя схемы для таблицы.|  
|TABLE_NAME|**String**|Имя таблицы.|  
|TABLE_TYPE|**String**|Табличный тип.|  
|REMARKS|**String**|Описание таблицы.<br /><br /> **Примечание**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|TYPE_CAT|**String**|Не поддерживается драйвером JDBC.|  
|TYPE_SCHEM|**String**|Не поддерживается драйвером JDBC.|  
|TYPE_NAME|**String**|Не поддерживается драйвером JDBC.|  
|SELF_REFERENCING_COL_NAME|**String**|Не поддерживается драйвером JDBC.|  
|REF_GENERATION|**String**|Не поддерживается драйвером JDBC.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getTables, см. в разделе "sp_tables (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Следующий пример показывает использование метода getTables для возврата описания таблицы Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
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
  
  
