---
title: "Метод (SQLServerResultSet) isLast | Документы Microsoft"
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
apiname: SQLServerResultSet.isLast
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 85d4451f-6392-470e-ab21-78a495b45792
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e006edb5e0fa5945be4c9e86254bbdaaf6a5b460
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="islast-method-sqlserverresultset"></a>isLast метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сообщает, является ли курсор на последнюю строку [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isLast()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если курсор находится в последней строке. **false** , если курсор находится в другом месте или если результирующий набор не содержит строк.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isLast указывается с помощью метода isLast в интерфейсе java.sql.ResultSet.  
  
 Если этот метод используется с однопроходными и динамическими курсорами, вызывается исключение.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
