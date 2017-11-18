---
title: "Метод setBigDecimal (SQLServerCallableStatement) | Документы Microsoft"
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
- SQLServerCallableStatement.setBigDecimal
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b50a920c-3839-40f0-9411-c60bbc2a9f34
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0f54854c66ca0dc2d438a625e8ae4e8bd9701855
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="setbigdecimal-method-sqlservercallablestatement"></a>Метод setBigDecimal (SQLServerCallableStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Задает номер указанного параметра для заданного объекта BigDecimal.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void setBigDecimal(java.lang.String sCol,  
                          java.math.BigDecimal bd)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sCol*  
  
 Объект **строка** , содержащее имя параметра.  
  
 *BD*  
  
 Объект BigDecimal.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setBigDecimal указывается с помощью метода setBigDecimal в интерфейсе java.sql.CallableStatement.  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  

