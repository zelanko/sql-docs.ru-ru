---
title: "Метод (java.lang.String, java.lang.String) getPooledConnection | Документы Microsoft"
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
- SQLServerConnectionPoolDataSource.getPooledConnection (java.lang.String, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f2e6391d-9aaf-4b09-ae1c-a27c1ada6301
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c62f975b9d9176941906f3ab8b5e5d7d241d14ff
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getpooledconnection-method-javalangstring-javalangstring"></a>Метод getPooledConnection (java.lang.String, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Пытается установить физическое соединение с базой данных, которое может использоваться как соединение из пула, по заданному имени пользователя и паролю.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.sql.PooledConnection getPooledConnection(java.lang.String user,  
                                                      java.lang.String password)  
```  
  
#### <a name="parameters"></a>Параметры  
 *пользователь*  
  
 Объект **строка** , содержащее имя пользователя.  
  
 *passwword*  
  
 Объект **строка** , содержащее пароль.  
  
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
  
  

