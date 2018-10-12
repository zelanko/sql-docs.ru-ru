---
title: Метод getProcedureColumns (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getProcedureColumns
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0df8fe-3cd6-46e4-ae3c-dc23c35676b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c239a16728538acece726c1d0b4722d9c2977765
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734702"
---
# <a name="getprocedurecolumns-method-sqlserverdatabasemetadata"></a>Метод getProcedureColumns (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает описание параметров и столбцов результата хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getProcedureColumns(java.lang.String sCatalog,  
                                              java.lang.String sSchema,  
                                              java.lang.String proc,  
                                              java.lang.String col)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCatalog*  
  
 Значение типа **String**, содержащее имя каталога. Задание значения NULL для этого параметра указывает на то, что имя каталога использовать не нужно.  
  
 *sSchema*  
  
 Значение типа **String**, содержащее шаблон имени схемы. Задание значения NULL для этого параметра указывает на то, что имя схемы использовать не нужно.  
  
 *proc*  
  
 Значение типа **String**, содержащее шаблон имени процедуры.  
  
 *col*  
  
 Значение типа **String**, содержащее шаблон имени столбца. Для каждого столбца возвращается строка при задании значения NULL для этого параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getProcedureColumns указывается с помощью метода getProcedureColumns в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращаемый методом getProcedureColumns, включает следующие данные:  
  
|Имя|Тип|Описание|  
|----------|----------|-----------------|  
|PROCEDURE_CAT|**String**|Имя базы данных, в которой находится указанная хранимая процедура.|  
|PROCEDURE_SCHEM|**String**|Схема для хранимой процедуры.|  
|PROCEDURE_NAME|**String**|Имя хранимой процедуры.|  
|COLUMN_NAME|**String**|Имя столбца.|  
|COLUMN_TYPE|**short**|Тип столбца. Может иметь одно из следующих значений.<br /><br /> procedureColumnUnknown (0)<br /><br /> procedureColumnIn (1)<br /><br /> procedureColumnInOut (2)<br /><br /> procedureColumnOut (4)<br /><br /> procedureColumnReturn (5)<br /><br /> procedureColumnResult (3)|  
|DATA_TYPE|**smallint**|Тип данных SQL из java.sql.Types.|  
|TYPE_NAME|**String**|Имя типа данных.|  
|PRECISION|**int**|Общее количество значащих цифр.|  
|LENGTH|**int**|Длина данных в байтах.|  
|SCALE|**short**|Количество цифр справа от десятичной запятой.|  
|RADIX|**short**|Основание системы счисления для числовых типов.|  
|NULLABLE|**short**|Указывает, может ли столбец содержать значение NULL. Может иметь одно из следующих значений.<br /><br /> procedureNoNulls (0)<br /><br /> procedureNullable (1)<br /><br /> procedureNullableUnknown (2)|  
|REMARKS|**String**|Описание этого столбца процедуры.<br /><br /> <br /><br /> **Примечание**. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|COLUMN_DEF|**String**|Значение по умолчанию для столбца.|  
|SQL_DATA_TYPE|**smallint**|Этот столбец содержит то же значение, что и столбец **DATA_TYPE**, за исключением типов данных **datetime** и ISO **interval**.|  
|SQL_DATETIME_SUB|**smallint**|Дополнительный код **datetime** ISO **interval**, если значение **SQL_DATA_TYPE** равно **SQL_DATETIME** или **SQL_INTERVAL**. Для типов данных, отличных от **datetime** и ISO **интервал**, этот столбец равен NULL.|  
|CHAR_OCTET_LENGTH|**int**|Максимальный размер столбца в байтах.|  
|ORDINAL_POSITION|**int**|Индекс столбца в таблице.|  
|IS_NULLABLE|**String**|Указывает, допускает ли столбец значения NULL.|  
|SS_TYPE_CATALOG_NAME|**String**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_TYPE_SCHEMA_NAME|**String**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_UDT_CATALOG_NAME|**String**|Определяемый пользователем тип с полным именем.|  
|SS_UDT_SCHEMA_NAME|**String**|Имя каталога, в котором определено имя коллекции схем XML. Если не удается найти имя каталога, то эта переменная содержит пустую строку.|  
|SS_UDT_ASSEMBLY_TYPE_NAME|**String**|Имя схемы, в которой определено имя коллекции схем XML. Если не удается найти имя схемы, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_CATALOG_NAME|**String**|Имя коллекции схем XML. Если не удается найти имя, значением является пустая строка.|  
|SS_XML_SCHEMACOLLECTION_SCHEMA_NAME|**String**|Имя каталога, содержащего определяемый пользователем тип.|  
|SS_XML_SCHEMACOLLECTION_NAME|**String**|Имя схемы, содержащей определяемый пользователем тип.|  
|SS_DATA_TYPE|**tinyint**|Тип данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используемый расширенными хранимыми процедурами.<br /><br /> <br /><br /> **Примечание**. Дополнительные сведения о типах данных, возвращаемых [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], см. в разделе "Типы данных (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
  
> [!NOTE]  
>  Дополнительные сведения о данных, возвращаемых методом getProcedureColumns, см. в разделе "sp_sproc_columns (Transact-SQL)" электронной документации по [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="example"></a>Пример  
 Следующий пример показывает использование метода getProcedureColumns для возврата сведений о хранимой процедуре uspGetBillOfMaterials в образце базы данных [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)].  
  
```  
public static void executeGetProcedureColumns(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getProcedureColumns(null, null, "uspGetBillOfMaterials", null);  
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
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
