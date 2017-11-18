---
title: "Метод getBigDecimal (java.lang.String) (SQLServerResultSet) | Документы Microsoft"
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
- SQLServerResultSet.getBigDecimal (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b0ded929-d5f5-4573-bf75-ce5bd32328a5
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 33ea6d61fd5abc2a85a6b430b7c28dc0117cfbb2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring-sqlserverresultset"></a>Метод getBigDecimal (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение имени заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.math.BigDecimal с полной точностью.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBigDecimal указывается с помощью метода getBigDecimal в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBigDecimal &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

