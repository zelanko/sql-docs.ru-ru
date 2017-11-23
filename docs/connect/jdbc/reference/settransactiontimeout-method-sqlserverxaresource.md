---
title: "Метод setTransactionTimeout (SQLServerXAResource) | Документы Microsoft"
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
apiname: SQLServerXAResource.setTransactionTimeout
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5a0f204b8042f139627b46bb63bf6a4049af9628
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="settransactiontimeout-method-sqlserverxaresource"></a>Метод setTransactionTimeout (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает значение времени ожидания текущей транзакции для данного [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean setTransactionTimeout(int seconds)  
```  
  
#### <a name="parameters"></a>Параметры  
 *секунд*  
  
 **Int** значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если время ожидания задано успешно. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Замечания  
 Этот метод setTransactionTimeout указывается с помощью метода setTransactionTimeout в интерфейсе javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
