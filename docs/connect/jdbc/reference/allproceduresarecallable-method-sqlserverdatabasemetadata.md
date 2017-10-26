---
title: "Метод allProceduresAreCallable (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.allProceduresAreCallable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8886137d-455e-497c-afea-4b326eda52f1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f6f8d2e96357171e59d1cfa41344fc190f987bb6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="allproceduresarecallable-method-sqlserverdatabasemetadata"></a>Метод allProceduresAreCallable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сообщает, является ли текущий пользователь имеет разрешения на вызов всех процедур, возвращаемых [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean allProceduresAreCallable()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если пользователь имеет разрешения на вызов всех процедур. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод allProceduresAreCallable указывается с помощью метода allProceduresAreCallable в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

