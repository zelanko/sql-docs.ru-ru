---
title: Метод getLogWriter (SQLServerDataSource) | Документы Microsoft
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
- SQLServerDataSource.getLogWriter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cde41743-1a5d-4930-91b3-4e5fccc1bc36
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 73fc012d720f320bca24f57edaa95dabc1400cba
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getlogwriter-method-sqlserverdatasource"></a>Метод getLogWriter (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Этот метод предназначен только для внутреннего использования. Дополнительные сведения о ведении журнала см. в разделе [Трассировка операций драйвера](../../../connect/jdbc/tracing-driver-operation.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.PrintWriter getLogWriter()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект PrintWriter.  
  
## <a name="remarks"></a>Замечания  
 Этот метод getLogWriter указывается с помощью метода getLogWriter в интерфейсе javax.sql.DataSource.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
