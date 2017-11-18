---
title: "Метод (String, String) getSchemas | Документы Microsoft"
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
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 24176593bf253b1a5482ac5df74a558046148c96
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getschemas-method-string-string"></a>Метод getSchemas (String, String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает имена схем, доступных в текущей базе данных, по указанному имени каталога и имени схемы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public ResultSet getSchemas(java.lang.String catalog,  
                       java.lang.String schemaPattern)  
```  
  
#### <a name="parameters"></a>Параметры  
 *каталог*  
  
 Имя каталога в базе данных. Если это пустая строка, то результат включает схемы без каталога. Если это **null**, имя каталога не используется для поиска.  
  
 *schemaPattern*  
  
 Имя схемы. Если это **null**, имя схемы не используется для поиска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSchemas указывается с помощью метода getSchemas в интерфейсе java.sql.DatabaseMetaData.  
  
 Результирующий набор, возвращенный методом getSchemas содержит следующие сведения:  
  
|Имя|Тип|Description|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**Строковые значения**|Имя схемы.|  
|TABLE_CATALOG|**Строковые значения**|Имя каталога для схемы.|  
  
 Результаты упорядочиваются по значениям TABLE_CATALOG, а затем по значениям TABLE_SCHEM. Каждая строка первым столбцом содержит TABLE_SCHEM, а вторым — TABLE_CATALOG.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

