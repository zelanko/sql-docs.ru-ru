---
title: "Метод getPooledConnection () | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerConnectionPoolDataSource.getPooledConnection ()
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: aad6c325-3398-462c-aa6e-201dc89fa5ef
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a35e2b75f0de79a010483b1a7240c2721eb5f5a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getpooledconnection-method-"></a>Метод getPooledConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает физическое соединение с базой данных, которое будет использоваться в пулах соединений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.sql.PooledConnection getPooledConnection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод getPooledConnection указывается с помощью метода getPooledConnection в интерфейсе javax.sql.ConnectionPoolDataSource.  
  
## <a name="see-also"></a>См. также:  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Методы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Элементы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Класс SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
