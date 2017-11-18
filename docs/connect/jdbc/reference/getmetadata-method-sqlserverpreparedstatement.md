---
title: "getMetaData метод (SQLServerPreparedStatement) | Документы Microsoft"
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
- SQLServerPreparedStatement.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ed49a53-ed61-4e95-ad67-45957aaabb6a
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fa53555385ae6b23bef278ff4456ee8d5ab7f50f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getmetadata-method-sqlserverpreparedstatement"></a>getMetaData метод (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает [класс SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) , содержащий сведения о столбцах [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект, который будет возвращен при это [ SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) запуска объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ResultSetMetaData getMetaData()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект ResultSetMetaData.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMetaData указывается в методе getMetaData в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

