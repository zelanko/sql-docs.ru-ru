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
ms.topic: conceptual
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
ms.openlocfilehash: 38a9bf912c0a967a29c8a6ff3543418d1c29b957
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  
