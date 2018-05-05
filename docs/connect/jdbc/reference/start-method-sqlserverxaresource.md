---
title: Метод Start (SQLServerXAResource) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerXAResource.start
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 33c90213-92f7-416b-b2fa-67a1afe64e97
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e496ad274ed6a75e2f25636e8bc2e1a2fa5aa3fc
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="start-method-sqlserverxaresource"></a>Метод start (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Начинает работу от имени ветви транзакции, указанной в объекте Xid.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void start(javax.transaction.xa.Xid xid,  
                  int flags)  
```  
  
#### <a name="parameters"></a>Параметры  
 *XID*  
  
 Объект Xid.  
  
 *flags*  
  
 **Int** значение.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Замечания  
 Этот метод запуска указывается с помощью метода start в интерфейсе javax.transaction.xa.XAResource.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
