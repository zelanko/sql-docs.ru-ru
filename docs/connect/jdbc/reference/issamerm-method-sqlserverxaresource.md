---
title: "Метод isSameRM (SQLServerXAResource) | Документы Microsoft"
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
- SQLServerXAResource.isSameRM
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bfa24c46-b7cf-470a-afa1-52301847a448
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 27cc769b71dffcb47c1575c73c778fbd43e73656
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="issamerm-method-sqlserverxaresource"></a>Метод isSameRM (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Определяет, является ли экземпляр диспетчера ресурсов, представленного целевого объекта совпадает с экземпляром диспетчера ресурсов, которые представлены в заданном объекте XAResource.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isSameRM(javax.transaction.xa.XAResource xares)  
```  
  
#### <a name="parameters"></a>Параметры  
 *xares*  
  
 Объект XAResource.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если экземпляры совпадают. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Замечания  
 Этот метод фиксации указывается с помощью метода фиксации в интерфейсе javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  

