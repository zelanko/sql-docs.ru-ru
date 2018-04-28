---
title: Метод (SQLServerStatement) getMaxFieldSize | Документы Microsoft
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
apiname:
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: eea3785d97e19b598b2b7c30f75b9a9412d9c1e9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число байтов, которые могут возвращаться для значений символьных и двоичных столбцов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее максимальное число байтов, которые может содержать столбец, или 0, если не ограничено.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMaxFieldSize указывается с помощью метода getMaxFieldSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
