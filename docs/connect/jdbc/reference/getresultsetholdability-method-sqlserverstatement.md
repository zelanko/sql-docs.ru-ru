---
title: "Метод (SQLServerStatement) getResultSetHoldability | Документы Microsoft"
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
apiname: SQLServerStatement.getResultSetHoldability
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 053549ee-2018-47ab-9538-789dac2b150a
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3b9f9051512f95da78c15a4f36aa3427e247789c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getresultsetholdability-method-sqlserverstatement"></a>getResultSetHoldability метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает результирующий набор удержания для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты, созданные этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее возможность сохранения результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getResultSetHoldability указывается с помощью метода getResultSetHoldability в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
