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
ms.openlocfilehash: c3d4b2132c3bbcf5612faa5f319a5358f158e2b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977987"
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
 Этот метод getXAResource задается методом getXAResource в интерфейсе javax. SQL. XAConnection.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-methods.md)   
 [Элементы SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-members.md)   
 [Класс SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
