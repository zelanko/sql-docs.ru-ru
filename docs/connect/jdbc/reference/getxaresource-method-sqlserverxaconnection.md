---
title: Метод getXAResource (SQLServerXAConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerXAConnection.getXAResource
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1d2828f-fd20-44b0-b796-dc70f77c5b03
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cbad0cdd9fe26c780e3acc5691f9af56e63ce1fe
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801768"
---
# <a name="getxaresource-method-sqlserverxaconnection"></a>Метод getXAResource (SQLServerXAConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает объект [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md), который будет использоваться диспетчером транзакций для управления участием этого объекта [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) в распределенной транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.transaction.xa.XAResource getXAResource()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект XAResource.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод getXAResource указывается с помощью метода getXAResource в интерфейсе javax.sql.XAConnection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Класс SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
