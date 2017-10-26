---
title: "Метод getQueryTimeout (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fff7b7d5310caf4ea57d929037c82aff1ae3f024
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getquerytimeout-method-sqlserverstatement"></a>Метод getQueryTimeout (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает количество секунд [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] будет ожидать это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) выполнения объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее количество секунд, драйвер JDBC будет ожидать, или 0, если не ограничено.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getQueryTimeout указывается с помощью метода getQueryTimeout в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

