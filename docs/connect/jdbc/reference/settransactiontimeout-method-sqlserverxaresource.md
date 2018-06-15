---
title: Метод setTransactionTimeout (SQLServerXAResource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerXAResource.setTransactionTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 38bf4a1a-6ad3-437c-b9ed-8792ab6dde7e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 143a1102ff6ab1e3c47427ead4adaccdf114eca6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32845669"
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
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
