---
title: "Close-метод (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 84a25d64-dd3e-4696-bb5f-4eaf391fab7e
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 905b60125704b51fad9aebfa07ba4c461f64bf12
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="close-method-sqlserverstatement"></a>Close-метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Это освобождает [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) базы данных и ресурсы JDBC вместо ожидания их автоматического освобождения объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод close определяется close-метод в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
