---
title: Метод (String, String) getSchemas | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 672171ac-976f-4605-9bee-2a5e141d92cb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1ae8055502f62d1cb3843f3076b50fc282a8013
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
 *catalog*  
  
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
  
|Название|Тип|Описание|  
|----------|----------|-----------------|  
|TABLE_SCHEM|**String**|Имя схемы.|  
|TABLE_CATALOG|**String**|Имя каталога для схемы.|  
  
 Результаты упорядочиваются по значениям TABLE_CATALOG, а затем по значениям TABLE_SCHEM. Каждая строка первым столбцом содержит TABLE_SCHEM, а вторым — TABLE_CATALOG.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
