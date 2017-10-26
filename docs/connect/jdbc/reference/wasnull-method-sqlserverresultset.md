---
title: "Метод (SQLServerResultSet) wasNull | Документы Microsoft"
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
- SQLServerResultSet.wasNull
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d37f80ef-d72c-4429-ada3-1d685bdab6d7
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1e787f37570e0475ca0f046b0d7302c7981fa0dd
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="wasnull-method-sqlserverresultset"></a>wasNull метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Проверяет, является ли последнее считанное значение Null.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean wasNull()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если последнее считанное имел значение null. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод wasNull указывается с помощью метода wasNull в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

