---
title: Метод executeQuery (java.lang.String) | Документы Microsoft
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
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 492cda13e6481a31915b85940d78847e3782205f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="executequery-method-javalangstring"></a>Метод executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и возвращает один [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLServerResultSet.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод executeQuery указывается с помощью метода executeQuery в интерфейсе java.sql.Statement.  
  
 Этот метод переопределяет [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод, который находится в [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) класса.  
  
 Вызов этого метода будет приведет к исключению, поскольку задан в инструкции SQL для объекта SQLServerPreparedStatement при создании объекта.  
  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) создается, если выводит заданную инструкцию SQL, отличное от одной [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="see-also"></a>См. также  
 [Метод executeQuery &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
