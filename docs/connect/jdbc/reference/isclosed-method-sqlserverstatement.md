---
title: "Метод isClosed (SQLServerStatement) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fdd47545dcf4962eca79dc764b03f63f72d20343
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="isclosed-method-sqlserverstatement"></a>Метод isClosed (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект был закрыт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** при этом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объект был закрыт, **false** если он все еще открыт.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isClosed указывается с помощью isClosed метода в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
