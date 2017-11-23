---
title: "Метод (SQLServerResultSet) isAfterLast | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.isAfterLast
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 19f9d124-3184-4985-8b97-503a8ab8b4f9
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb856719e0225077394df353b14f05b91af9040c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="isafterlast-method-sqlserverresultset"></a>isAfterLast метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сообщает, является ли курсор после последней строки в этом [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isAfterLast()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если курсор находится после последней строки. **false** , если курсор находится в другом месте или если результирующий набор не содержит строк.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isAfterLast указывается с помощью метода isAfterLast в интерфейсе java.sql.ResultSet.  
  
 Если этот метод используется с динамическими курсорами, включая однопроходные курсоры только для чтения, а свойство соединения selectMethod имеет значение cursor, то вызывается исключение.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
