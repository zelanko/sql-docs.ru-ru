---
title: Метод recover (SQLServerXAResource) | Документация Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b78165b8c199a04d716d18614e6fb56232eca429
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923112"
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
  
 Значение типа **int**, которое может принимать следующие значения: XAResource.TMSTARTRSCAN или XAResource.TMENDRSCAN или XAResource.TMNOFLAGS или XAResource.TMSTARTTRSCAN | XAResource.TMENDRSCAN.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект Xid.  
  
## <a name="exceptions"></a>Исключения  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>Remarks  
 Этот метод recover определен с помощью метода recover в интерфейсе javax.transaction.xa.XAResource.  
  
 Если параметр **flag** имеет значение, отличное от XAResource.TMSTARTRSCAN или XAResource.TMSTARTRSCAN | XAResource.TMENDRSCAN, скорее всего в текущий момент выполняется сканирование восстановления.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [Элементы SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [Класс SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
