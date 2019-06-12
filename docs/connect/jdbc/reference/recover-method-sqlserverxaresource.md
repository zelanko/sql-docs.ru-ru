---
title: Метод recover (SQLServerXAResource) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1ca9d0fede758b99f442a9553e4266e79fa81134
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794031"
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
  
## <a name="remarks"></a>Remarks  
 Этот метод recover определен с помощью метода recover в интерфейсе javax.transaction.xa.XAResource.  
  
 Если параметр **флаг** не XAResource.TMSTARTRSCAN или XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, ход выполнения должен выполняться просмотр восстановления.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
