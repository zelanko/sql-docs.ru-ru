---
title: "Метод Execute (java.lang.String) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 219d4ff6ff793b244e30ca43582f4d194e7e6a5d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-javalangstring"></a>Метод execute (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которая может возвращать несколько результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** , содержащий инструкции SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если инструкция возвращает результирующий набор. **false** , если она возвращает счетчик обновлений или никаких результатов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод execute указывается с помощью метода execute в интерфейсе java.sql.Statement.  
  
 Этот метод переопределяет [выполнение](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод, который находится в [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) класса.  
  
 Вызов этого метода будет приведет к исключению, поскольку задан в инструкции SQL для объекта SQLServerPreparedStatement при создании объекта.  
  
## <a name="see-also"></a>См. также:  
 [выполнение метода &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

