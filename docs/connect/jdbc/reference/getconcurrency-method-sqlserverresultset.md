---
title: Метод (SQLServerResultSet) getConcurrency | Документы Microsoft
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
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5ec09e1ec8c8611c46280a39361b75e652b748d2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getconcurrency-method-sqlserverresultset"></a>getConcurrency метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает режим параллелизма этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее тип параллелизма, который может принимать одно из следующих значений:  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getConcurrency указывается с помощью метода getConcurrency в интерфейсе java.sql.ResultSet.  
  
 Используемый тип параллелизма определяется [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта, который создал результирующий набор.  
  
 Этот метод позволяет определить фактический тип параллелизма. Если в приложении выбрано значение CONCUR_READ_ONLY или CONCUR_UPDATABLE, будут возвращены эти значения. Если в приложении используется параллелизм по умолчанию, будет возвращено значение CONCUR_READ_ONLY.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
