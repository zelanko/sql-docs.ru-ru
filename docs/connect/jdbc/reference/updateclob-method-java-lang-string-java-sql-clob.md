---
title: "Метод updateClob (java.lang.String, java.sql.Clob) | Документы Microsoft"
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
- SQLServerResultSet.updateClob (java.lang.String, java.sql.Clob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5da64915-1c13-44fd-90c0-52168889bae0
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ea8e31b6917758d79b492d571b6e96d3b382c603
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="updateclob-method-javalangstring-javasqlclob"></a>Метод updateClob (java.lang.String, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Обновляет указанный столбец значением java.sql.Clob, указанным по имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void updateClob(java.lang.String columnName,  
                       java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnName*  
  
 Объект **строка** , содержащее имя столбца.  
  
 *clobValue*  
  
 Объект Clob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод updateClob указывается с помощью метода updateClob в интерфейсе java.sql.ResultSet.  
  
## <a name="see-also"></a>См. также:  
 [Метод updateClob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

