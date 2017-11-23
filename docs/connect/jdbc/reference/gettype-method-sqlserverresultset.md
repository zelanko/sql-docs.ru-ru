---
title: "getType метод (SQLServerResultSet) | Документы Microsoft"
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
apiname: SQLServerResultSet.getType
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: ffbc4a02-e851-431c-bc1a-7ab381d982bb
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 29c2307a452dbbbc1055facc2b4eedeb2829b852
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="gettype-method-sqlserverresultset"></a>getType метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает тип курсора этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getType()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** указывает текущий тип курсора, который может быть одним из следующих значений:  
  
 ResultSet.TYPE_FORWARD_ONLY  
  
 ResultSet.TYPE_SCROLL_INSENSITIVE  
  
 ResultSet.TYPE_SCROLL_SENSITIVE  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getType указывается с помощью метода getType в интерфейсе java.sql.ResultSet.  
  
 Этот метод позволяет определить фактический тип курсора. Если в приложении выбран тип TYPE_FORWARD_ONLY или используется тип курсора по умолчанию, то возвращается значение TYPE_FORWARD_ONLY.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
