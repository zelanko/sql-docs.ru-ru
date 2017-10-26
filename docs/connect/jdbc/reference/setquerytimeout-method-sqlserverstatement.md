---
title: "Метод (SQLServerStatement) setQueryTimeout | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerStatement.setQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c513265-cd0c-4b38-9494-94458c17a16d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7bab9110f94820055812ead62014b993115d84e2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setquerytimeout-method-sqlserverstatement"></a>setQueryTimeout метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает количество секунд, драйвер будет ожидать [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) указанное число секунд выполнения объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setQueryTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Параметры  
 *секунд*  
  
 **Int** , указывающее количество секунд ожидания, или 0, если не ограничено.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setQueryTimeout указывается с помощью метода setQueryTimeout в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

