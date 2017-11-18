---
title: "Метод getBigDecimal (java.lang.String) | Документы Microsoft"
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
- SQLServerCallableStatement.getBigDecimal (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d0b29b48-9663-4de4-9fc2-82bc30e44aed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 815ed2b2460a4b492868074f5e11e607f0effe70
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getbigdecimal-method-javalangstring"></a>Метод getBigDecimal (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта java.math.BigDecimal с полной точностью по заданному имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.math.BigDecimal getBigDecimal(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getBigDecimal указывается с помощью метода getBigDecimal в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getBigDecimal &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getbigdecimal-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

