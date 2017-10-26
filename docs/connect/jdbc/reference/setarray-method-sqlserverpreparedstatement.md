---
title: "setArray метод (SQLServerPreparedStatement) | Документы Microsoft"
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
- SQLServerPreparedStatement.setArray
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7fb66d4-6a42-43d0-ba68-8514816917cb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 357671600966effa7be58472d5561670bfd4c03a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setarray-method-sqlserverpreparedstatement"></a>setArray метод (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер указанного параметра для заданного объекта массива.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setArray(int i,  
                           java.sql.Array x)  
```  
  
#### <a name="parameters"></a>Параметры  
 *я*  
  
 **Int** указывает номер параметра.  
  
 *x*  
  
 Объект массива.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setArray указывается с помощью метода setArray в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

