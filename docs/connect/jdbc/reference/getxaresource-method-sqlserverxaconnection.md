---
title: "Метод getXAResource (SQLServerXAConnection) | Документы Microsoft"
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
apiname:
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 78999ece74ad80f7d4ce107484d225cc1ab6f4f6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getxaresource-method-sqlserverxaconnection"></a>Метод getXAResource (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) , диспетчер транзакций будет использовать для управления [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) участие объекта в распределенной транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект XAResource.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод getXAResource указывается с помощью метода getXAResource в интерфейсе javax.sql.XAConnection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Класс SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  

