---
title: "insertRow метод (SQLServerResultSet) | Документы Microsoft"
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
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9297b57b1ad4ded2611fadb1034a61046e3a4d25
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="insertrow-method-sqlserverresultset"></a>insertRow метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Добавляет содержимое строки вставки в это [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов к базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод insertRow указывается с помощью метода insertRow в интерфейсе java.sql.ResultSet.  
  
 В момент вызова этого метода курсор должен располагаться в строке вставки. После вызова этого метода курсор остается в строке вставки, а результирующий набор остается в режиме вставки.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
