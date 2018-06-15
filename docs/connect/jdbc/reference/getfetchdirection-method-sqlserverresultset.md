---
title: Метод (SQLServerResultSet) getFetchDirection | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 594d59adc33decf67118fd680d6aeaa32a38ebe7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32834619"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection метод (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение направления выборки для этого [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** указывает текущее направление выборки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getFetchDirection указывается с помощью метода getFetchDirection в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает значение FETCH_FORWARD однонаправленные курсоры, последний параметр, внесенные с помощью вызова [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) метод для курсоров других типов и будет возвращать FETCH_UNKNOWN этих типов курсоров, если метод setFetchDirection никогда не вызывается.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
