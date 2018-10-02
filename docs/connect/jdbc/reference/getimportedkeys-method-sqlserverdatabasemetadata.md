---
title: Метод getImportedKeys (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getImportedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: dc8c1a5e-700e-4059-a5ed-5013bbb87fb6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cbb50cd617ba1ce85851c08764f3f80cd90cbe67
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47611632"
---
# <a name="getimportedkeys-method-sqlserverdatabasemetadata"></a>Метод getImportedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов первичного ключа, на которые ссылаются столбцы внешнего ключа таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getImportedKeys(java.lang.String cat,  
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
 Этот метод getImportedKeys указывается с помощью метода getImportedKeys в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getImportedKeys, включает следующие данные:  
  
|Имя|Тип|Описание|  
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
>  Дополнительные сведения о данных, возвращаемых методом getImportedKeys, см. в разделе "sp_fkeys (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано использование метода getImportedKeys для возвращения сведений обо всех первичных ключах, которые ссылаются на внешние ключи таблицы Person.Address в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetImportedKeys(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getImportedKeys("AdventureWorks", "Person", "Address");  
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
  
  
