---
title: "Метод (SQLServerStatement) setMaxFieldSize | Документы Microsoft"
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
- SQLServerStatement.setMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38f7fc1d-acad-4d10-9fc8-3c0669d93b07
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79a7cd17e2d28fde42bfad8c82fdc4bcde3ef00f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setmaxfieldsize-method-sqlserverstatement"></a>setMaxFieldSize метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает ограничение на максимальное число байтов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) столбца хранятся символьные или двоичные значения заданного числа байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final void setMaxFieldSize(int max)  
```  
  
#### <a name="parameters"></a>Параметры  
 *max*  
  
 **Int** указывает максимальное число байтов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setMaxFieldSize указывается с помощью метода setMaxFieldSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

