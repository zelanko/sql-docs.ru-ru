---
title: Метод getConcurrency (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5d0d59186e15dc07d1d4e91ac673c456ec592d01
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67952826"
---
# <a name="getconcurrency-method-sqlserverresultset"></a>Метод getConcurrency (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает режим параллелизма этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает тип параллелизма. Возможны следующие значения:  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getConcurrency задается с помощью метода getConcurrency в интерфейсе java.sql.ResultSet.  
  
 Используемый тип параллелизма определяется объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), который создал результирующий набор.  
  
 Этот метод позволяет определить фактический тип параллелизма. Если в приложении выбрано значение CONCUR_READ_ONLY или CONCUR_UPDATABLE, будут возвращены эти значения. Если в приложении используется параллелизм по умолчанию, будет возвращено значение CONCUR_READ_ONLY.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
