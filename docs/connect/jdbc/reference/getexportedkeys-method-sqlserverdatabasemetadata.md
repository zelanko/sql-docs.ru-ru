---
title: Метод getExportedKeys (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getExportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 26888e61-b243-4a1b-922c-c0a451dcff4d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e89d65955c5637bcd566d48b6e54bcae50397d88
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983311"
---
# <a name="getexportedkeys-method-sqlserverdatabasemetadata"></a>Метод getExportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов внешнего ключа, который ссылается на столбцы первичного ключа заданной таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getExportedKeys(java.lang.String cat,  
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
 Этот метод getExportedKeys задается с помощью метода getExportedKeys в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getExportedKeys, включает следующие данные:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|PKTABLE_CAT|**String**|Имя каталога, содержащего таблицу первичного ключа.|  
|PKTABLE_SCHEM|**String**|Имя схемы таблицы первичного ключа.|  
|PKTABLE_NAME|**String**|Имя таблицы первичного ключа.|  
|PKCOLUMN_NAME|**String**|Имя столбца первичного ключа.|  
|FKTABLE_CAT|**String**|Имя каталога, содержащего таблицу внешнего ключа.|  
|FKTABLE_SCHEM|**String**|Имя схемы таблицы внешнего ключа.|  
|FKTABLE_NAME|**String**|Имя таблицы внешнего ключа.|  
|FKCOLUMN_NAME|**String**|Имя столбца внешнего ключа.|  
|KEY_SEQ|**short**|Порядковый номер столбца в первичном ключе из нескольких столбцов.|  
|UPDATE_RULE|**short**|Действие, применяемое к внешнему ключу, если операцией SQL является операция обновления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|DELETE_RULE|**short**|Действие, применяемое к внешнему ключу, если операцией SQL является операция удаления. Может иметь одно из следующих значений.<br /><br /> importedKeyNoAction (3)<br /><br /> importedKeyCascade (0)<br /><br /> importedKeySetNull (2)<br /><br /> importedKeySetDefault (4)<br /><br /> importedKeyRestrict (1)|  
|FK_NAME|**String**|Имя внешнего ключа.|  
|PK_NAME|**String**|Имя первичного ключа.|  
|DEFERRABILITY|**short**|Указывает, можно ли отложить вычисление ограничения внешнего ключа до фиксации. Может иметь одно из следующих значений.<br /><br /> importedKeyInitiallyDeferred (5)<br /><br /> importedKeyInitiallyImmediate (6)<br /><br /> importedKeyNotDeferrable (7)|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getExportedKeys, см. в разделе "sp_fkeys (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getExportedKey для возвращения сведений обо всех внешних ключах, которые ссылаются на первичные ключи таблицы Person.Contact в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetExportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getExportedKeys("AdventureWorks", "Person", "Contact");  
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
  
  
