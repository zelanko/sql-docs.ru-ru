---
title: Метод getSQLStateType (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e9090d0632c82a811d0c03fdc98dae44c0a732db
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Метод getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, равно ли состояние SQLSTATE, возвращенное методом SQLException.getSQLState, X/Open (теперь называется Open Group), SQL CLI, SQL99 (JDBC 3.0) или SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее тип SQLSTATE, который может принимать одно из следующих значений:  
  
-   Для Java Runtime Environment верси 5.0: Если **xopenStates** соединения свойству **true**, этот метод возвращает DatabaseMetaData.sqlStateXOpen. В противном случае DatabaseMetaData.sqlStateSQL99.  
  
-   Для Java Runtime Environment версии 6.0: Если **xopenStates** соединения свойству **true**, этот метод возвращает DatabaseMetaData.sqlStateXOpen. В противном случае DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSQLStateType указывается с помощью метода getSQLStateType в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
