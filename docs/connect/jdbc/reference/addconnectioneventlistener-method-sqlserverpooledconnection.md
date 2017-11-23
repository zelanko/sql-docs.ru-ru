---
title: "Метод addConnectionEventListener (SQLServerPooledConnection) | Документы Microsoft"
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
apiname: SQLServerPooledConnection.addConnectionEventListener
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 142830a8-8d4e-48ca-911d-85bf195ca4fe
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e61412a763568c6daced9efb22c72c11d85f3f37
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="addconnectioneventlistener-method-sqlserverpooledconnection"></a>Метод addConnectionEventListener (SQLServerPooledConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Регистрирует заданный прослушиватель событий будет получать уведомления при возникновении события на этом [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void addConnectionEventListener(javax.sql.ConnectionEventListener listener)  
```  
  
#### <a name="parameters"></a>Параметры  
 *прослушиватель*  
  
 Объект ConnectionEventListener.  
  
## <a name="remarks"></a>Замечания  
 Этот метод addConnectionEventListener указывается с помощью метода addConnectionEventListener в интерфейсе javax.sql.PooledConnection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-methods.md)   
 [Элементы SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-members.md)   
 [Класс SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)  
  
  
