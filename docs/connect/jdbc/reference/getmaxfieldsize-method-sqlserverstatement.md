---
title: Метод (SQLServerStatement) getMaxFieldSize | Документы Microsoft
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
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 77db7a486929d71492f6dea5494d912805d1dc5a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32836769"
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>getMaxFieldSize метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число байтов, которые могут возвращаться для значений символьных и двоичных столбцов в [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта, созданного этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее максимальное число байтов, которые может содержать столбец, или 0, если не ограничено.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMaxFieldSize указывается с помощью метода getMaxFieldSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
