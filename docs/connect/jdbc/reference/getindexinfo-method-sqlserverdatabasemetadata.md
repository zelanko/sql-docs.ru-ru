---
title: Метод getIndexInfo (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getIndexInfo
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8a677cc6-8e33-4e57-8678-0849345aa8d0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 22414058b0763f32c2b991487e006b8de8e50611
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66774347"
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
 *cat*  
  
 Значение типа **String**, содержащее имя каталога.  
  
 *schema*  
  
 Значение типа **String**, содержащее имя схемы.  
  
 *table*  
  
 Значение типа **String**, содержащее имя таблицы.  
  
 *unique*  
  
 **значение true,** Если возвращаются только индексы для уникальных значений. **false** Если возвращаются все индексы.  
  
 *approximate*  
  
 **значение true,** Если результаты отражают приблизительные или устаревшие значения. **false** Если результаты точны.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getIndexInfo указывается с помощью метода getIndexInfo в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getIndexInfo, включает следующие данные.  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|Имя базы данных, в которой расположена указанная таблица.|  
|TABLE_SCHEM|**String**|Схема таблицы.|  
|TABLE_NAME|**String**|Имя таблицы.|  
|NON_UNIQUE|**boolean**|Указывает, могут ли значения индекса быть неуникальными.|  
|INDEX_QUALIFIER|**String**|Имя владельца индекса. Принимает значение NULL, если TYPE равен tableIndexStatistic.|  
|INDEX_NAME|**String**|Имя индекса.|  
|TYPE|**short**|Тип индекса. Может иметь одно из следующих значений.<br /><br /> tableIndexStatistic (0)<br /><br /> tableIndexClustered (1)<br /><br /> tableIndexHashed (2)<br /><br /> tableIndexOther (3)|  
|ORDINAL_POSITION|**short**|Порядковый номер столбца в индексе. Номер первого столбца в таблице равен 1.|  
|COLUMN_NAME|**String**|Имя столбца.|  
|ASC_OR_DESC|**String**|Порядок, используемый в параметрах сортировки индекса. Может иметь одно из следующих значений.<br /><br /> A (по возрастанию)<br /><br /> D (по убыванию)<br /><br /> NULL (неприменимо)<br /><br /> **Примечание**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] всегда возвращает значение A.|  
|CARDINALITY|**int**|Число строк в таблице или уникальных значений в индексе.|  
|PAGES|**int**|Число страниц для хранения индекса или таблицы.|  
|FILTER_CONDITION|**String**|Условие фильтра.<br /><br /> **Примечание**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] всегда возвращает значение NULL.|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getIndexInfo, см. в разделе "sp_indexes (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getIndexInfo для возврата сведений об индексах и статистики для таблицы Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
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
  
  
