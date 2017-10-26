---
title: "Метод getIndexInfo (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
caps.latest.revision: 15
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 028937d023b6cf899eb5fa47354cb0c5d21545bc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getindexinfo-method-sqlserverdatabasemetadata"></a>Метод getIndexInfo (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание индексов и статистику для заданной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getIndexInfo(java.lang.String cat,  
                                       java.lang.String schema,  
                                       java.lang.String table,  
                                       boolean unique,  
                                       boolean approximate)  
```  
  
#### <a name="parameters"></a>Параметры  
 *CAT*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *схемы*  
  
 Объект **строка** , содержащее имя схемы.  
  
 *table*  
  
 Объект **строка** , содержащее имя таблицы.  
  
 *Уникальный*  
  
 **значение true,** Если возвращаются только индексы для уникальных значений. **false** Если возвращаются все индексы.  
  
 *Приблизительное*  
  
 **значение true,** , если результаты отражают приблизительные или устаревшие значения. **false** Если результаты точны.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getIndexInfo указывается с помощью метода getIndexInfo в интерфейсе java.sql.DatabaseMetaData.  
  
 Метод getIndexInfo возвращает результирующий набор будет содержать следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**Строковые значения**|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|**Строковые значения**|Схема таблицы.|  
|TABLE_NAME|**Строковые значения**|Имя таблицы.|  
|NON_UNIQUE|**boolean**|Указывает, могут ли значения индекса быть неуникальными.|  
|INDEX_QUALIFIER|**Строковые значения**|Имя владельца индекса. Принимает значение NULL, если TYPE равен tableIndexStatistic.|  
|INDEX_NAME|**Строковые значения**|Имя индекса.|  
|TYPE|**короткий**|Тип индекса. Может иметь одно из следующих значений.<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**короткий**|Порядковый номер столбца в индексе. Номер первого столбца в таблице равен 1.|  
|COLUMN_NAME|**Строковые значения**|Имя столбца.|  
|ASC_OR_DESC|**Строковые значения**|Порядок, используемый в параметрах сортировки индекса. Может иметь одно из следующих значений.<br /><br /> A (по возрастанию)<br /><br /> D (по убыванию)<br /><br /> NULL (неприменимо)<br /><br /> **Примечание:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] всегда возвращает «A».  |  
|CARDINALITY|**int**|Число строк в таблице или уникальных значений в индексе.|  
|PAGES|**int**|Число страниц для хранения индекса или таблицы.|  
|FILTER_CONDITION|**Строковые значения**|Условие фильтра.<br /><br /> **Примечание:** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] всегда возвращает значение null.  |  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getIndexInfo см. в разделе «sp_indexes (Transact-SQL)» в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] электронной документации.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как использовать метод getIndexInfo для возврата сведений об индексах и статистики для таблицы Person.Contact в [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] образца базы данных.  
  
```  
public static void executeGetIndexInfo(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getIndexInfo("AdventureWorks", "Person", "Contact", false, true);  
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
  
  

