---
title: Метод (SQLServerConnection) setAutoCommit | Документы Microsoft
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
ms.topic: article
apiname:
- SQLServerConnection.setAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db1e22d2-e53f-474e-8c99-cb1fff7f491a
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7bf6842881256a5de4da2805b2c07c5f64fbeff4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setautocommit-method-sqlserverconnection"></a>setAutoCommit метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает режим автоматической фиксации для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) состояние данного объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setAutoCommit(boolean value)  
```  
  
#### <a name="parameters"></a>Параметры  
 *value*  
  
 **значение true,** для перехода в режим автоматической фиксации для соединения, **false** отключить ее.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setAutoCommit указывается с помощью метода setAutoCommit в интерфейсе java.sql.Connection.  
  
 Если соединение находится в режиме автоматической фиксации, то все инструкции SQL выполняются и фиксируются как отдельные транзакции. В противном случае инструкции SQL группируются в транзакции, завершаемые вызовом либо [фиксации](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md) метода или [отката](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md) метод. По умолчанию новые соединения работают в режиме автоматической фиксации.  
  
 Фиксация выполняется, когда инструкция завершает работу или в момент следующего выполнения (в зависимости от того, какое событие случается первым). В случае использования инструкций, возвращающих [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, инструкция завершается, когда было получено последней строки результирующего набора или закрытием результирующего набора. В сложных случаях одна транзакция может возвращать несколько результатов, помимо значений выходных параметров. В таких случаях фиксация выполняется после получения всех результатов и значений выходных параметров.  
  
 Когда режим автоматической фиксации — **false**, драйвер JDBC неявно запускает новую транзакцию после каждой фиксации.  
  
> [!NOTE]  
>  Если этот метод вызывается в ходе транзакции, эта транзакция фиксируется.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
