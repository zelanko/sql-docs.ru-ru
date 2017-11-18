---
title: "Метод getSQLXML (java.lang.String) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f56b192a-3255-4215-b552-8e494fbca083
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 21eba6572ba201ae68891cf2c80545d586903290
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsqlxml-method-javalangstring"></a>Метод getSQLXML (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта SQLXML, заданному имени параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.SQLXML getSQLXML(java.lang.String parameterName)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Имя_параметра*  
  
 Объект **строка** , указывающее имя параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSQLXML задается методом getSQLXML в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод getSQLXML &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlservercallablestatement.md)   
 [Элементы SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)  
  
  

