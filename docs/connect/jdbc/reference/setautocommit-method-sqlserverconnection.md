---
title: Метод setAutoCommit (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 517ce61f011de7cf5915c88895b9795b08767b20
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47761572"
---
# <a name="setautocommit-method-sqlserverconnection"></a>Метод setAutoCommit (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает режим автоматической фиксации для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) в указанное состояние.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 Значение **true**, чтобы включить режим автоматической фиксации для подключения, и значение **false**, чтобы отключить его.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setAutoCommit указывается с помощью метода setAutoCommit в интерфейсе java.sql.Connection.  
  
 Если соединение находится в режиме автоматической фиксации, то все инструкции SQL выполняются и фиксируются как отдельные транзакции. В противном случае инструкции SQL группируются в транзакции, завершаемые вызовом метода [commit](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md) или [rollback](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md). По умолчанию новые соединения работают в режиме автоматической фиксации.  
  
 Фиксация выполняется, когда инструкция завершает работу или в момент следующего выполнения (в зависимости от того, какое событие случается первым). Транзакции, которые возвращают объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), завершаются после получения последней строки результирующего набора или в момент закрытия результирующего набора. В сложных случаях одна транзакция может возвращать несколько результатов, помимо значений выходных параметров. В таких случаях фиксация выполняется после получения всех результатов и значений выходных параметров.  
  
 Если режим автоматической фиксации имеет значение **false**, драйвер JDBC неявно запускает новую транзакцию после каждой фиксации.  
  
> [!NOTE]  
>  Если этот метод вызывается в ходе транзакции, эта транзакция фиксируется.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
