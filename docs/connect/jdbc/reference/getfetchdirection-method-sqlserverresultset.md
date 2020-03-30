---
title: Метод getFetchDirection (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f56893764392236d563fa2b9a236f55e67e13595
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983251"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>Метод getFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение направления выборки для этого объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает текущее направление выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getFetchDirection задается с помощью метода getFetchDirection в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает значение FETCH_FORWARD для однопроходных курсоров, последнее значение, заданное вызовом метода [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) для курсоров других типов, и значение FETCH_UNKNOWN для этих типов курсоров, если метод setFetchDirection не вызывался.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
