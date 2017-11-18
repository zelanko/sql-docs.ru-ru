---
title: "Метод End (SQLServerXAResource) | Документы Microsoft"
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
- SQLServerXAResource.end
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e6418b27-793b-4b36-8dfb-756aec7bcbba
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6a668ca4119fbad7200c662ced70721669b63308
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="end-method-sqlserverxaresource"></a>Метод end (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Завершает работу, выполняемую от имени ветви транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void end(javax.transaction.xa.Xid xid,  
                int flags)  
```  
  
#### <a name="parameters"></a>Параметры  
 *XID*  
  
 Объект Xid.  
  
 *флаги*  
  
 **Int** значение.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Замечания  
 Этот метод end указывается с помощью метода end в интерфейсе javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

