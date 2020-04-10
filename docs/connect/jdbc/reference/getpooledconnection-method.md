---
title: Метод getPooledConnection () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnectionPoolDataSource.getPooledConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: aad6c325-3398-462c-aa6e-201dc89fa5ef
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b5e9a0c596989aca073e323df8a9ec92f8fa03b4
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80925229"
---
# <a name="getpooledconnection-method-"></a>Метод getPooledConnection ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Устанавливает физическое соединение с базой данных, которое будет использоваться в пулах соединений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public javax.sql.PooledConnection getPooledConnection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md).  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Remarks  
 Этот метод getPooledConnection задается с помощью метода getPooledConnection в интерфейсе javax.sql.ConnectionPoolDataSource.  
  
## <a name="see-also"></a>См. также:  
 [getPooledConnection](../../../connect/jdbc/reference/getpooledconnection-method-sqlserverconnectionpooldatasource.md)   
 [Методы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-methods.md)   
 [Элементы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Класс SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
  
