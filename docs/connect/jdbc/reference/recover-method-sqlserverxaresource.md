---
title: Метод recover (SQLServerXAResource) | Документы Microsoft
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
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2e30fa3b1fc9d5ab419cd0f8f8b2b7bbcf018b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840479"
---
# <a name="recover-method-sqlserverxaresource"></a>Метод recover (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает список ветвей подготовленной транзакции от диспетчера ресурсов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Параметры  
 *flags*  
  
 **Int** значение, которое может принимать одно из следующих значений: XAResource.TMSTARTRSCAN или XAResource.TMENDRSCAN или XAResource.TMNOFLAGS или XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Xid.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Замечания  
 Этот метод восстановления указывается с помощью метода восстановить в интерфейсе javax.transaction.xa.XAResource.  
  
 Если параметр **флаг** не XAResource.TMSTARTRSCAN или XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, просмотр восстановления должны выполняться.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
