---
title: Метод getCrossReference (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getCrossReference
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 099dd0bf-b017-479d-9696-f5b06f4c6bf9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bae60cb90c0459b5a221f88f463cfda0a520f47e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600862"
---
# <a name="getcrossreference-method-sqlserverdatabasemetadata"></a>Метод getCrossReference (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание столбцов внешнего ключа в заданной таблице внешнего ключа, который ссылается на столбцы первичного ключа заданной таблицы первичного ключа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getCrossReference(java.lang.String cat1,  
                                            java.lang.String schem1,  
                                            java.lang.String tab1,  
                                            java.lang.String cat2,  
                                            java.lang.String schem2,  
                                            java.lang.String tab2)  
```  
  
#### <a name="parameters"></a>Параметры  
 *cat1*  
  
 Значение типа **String**, содержащее имя каталога для таблицы, которая содержит первичный ключ.  
  
 *schem1*  
  
 Значение типа **String**, содержащее имя схемы для таблицы, которая содержит первичный ключ.  
  
 *tab1*  
  
 Значение типа **String**, содержащее имя таблицы для таблицы, которая содержит первичный ключ.  
  
 *Cat2*  
  
 Значение типа **String**, содержащее имя каталога для таблицы, которая содержит внешний ключ.  
  
 *schem2*  
  
 Значение типа **String**, содержащее имя схемы для таблицы, которая содержит внешний ключ.  
  
 *tab2*  
  
 Значение типа **String**, содержащее имя таблицы для таблицы, которая содержит внешний ключ.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getCrossReference указывается с помощью метода getCrossReference в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getCrossReference, включает следующие данные:  
  
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
>  Дополнительные сведения о данных, возвращаемых методом getCrossReference, см. в разделе "sp_fkeys (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать метод getCrossReference для возвращения сведений о связи между таблицами Person.Contact и HumanResources.Employee по первичному и внешнему ключу в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetCrossReference(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getCrossReference("AdventureWorks", "Person", "Contact", null, "HumanResources", "Employee");  
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
  
  
