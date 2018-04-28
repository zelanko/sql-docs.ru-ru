---
title: Метод jdbcCompliant (SQLServerDriver) | Документы Microsoft
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
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bf5dc875f5f02ffd8e14ae00c738e71797c2b502
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>Метод jdbcCompliant (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Проверяет, что [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] соответствует спецификации JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если драйвер JDBC отвечает минимальным требованиям. В противном случае — **false**.  
  
## <a name="remarks"></a>Замечания  
 Этот метод jdbcCompliant указывается с помощью метода jdbcCompliant в интерфейсе java.sql.Driver.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [Элементы SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [Класс SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
