---
title: "Метод prepareStatement (java.lang.String, int, int, int) | Документы Microsoft"
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
- SQLServerConnection.prepareStatement (java.lang.String, int, int, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b78d2192-f315-4c45-9051-c77059e2c3f4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 11f402ca51215db92774453fa9f97376fe1862b6
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="preparestatement-method-javalangstring-int-int-int"></a>Метод prepareStatement (java.lang.String, int, int, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) объект, который формирует [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекты с заданным типом, параллелизма и возможностью сохранения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.PreparedStatement prepareStatement(java.lang.String sql,  
                                                   int nType,  
                                                   int nConcur,  
                                                   int nHold)  
```  
  
#### <a name="parameters"></a>Параметры  
 *SQL*  
  
 Объект **строка** содержащее инструкцию SQL.  
  
 *nType*  
  
 **Int** , указывающее тип результирующего набора.  
  
 *nConcur*  
  
 **Int** , указывающее тип параллелизма результирующего набора.  
  
 *nHold*  
  
 **Int** , указывающее возможность сохранения результирующего набора.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PreparedStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод prepareStatement указывается с помощью метода prepareStatement в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод prepareStatement &#40; SQLServerConnection &#41;](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

