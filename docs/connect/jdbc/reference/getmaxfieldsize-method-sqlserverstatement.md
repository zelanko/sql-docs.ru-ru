---
title: Метод getMaxFieldSize (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxFieldSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed7bbcb8-660b-4e9b-8241-e216c42826f9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de123b3c6c8f0105a7280c87a4983fadc657ad93
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47795612"
---
# <a name="getmaxfieldsize-method-sqlserverstatement"></a>Метод getMaxFieldSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает максимальный размер (в байтах) для возвращаемых значений символьных и двоичных столбцов в объекте [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданном объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getMaxFieldSize()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, показывающее максимальное число байтов, которые может содержать столбец, либо значение 0, если ограничение отсутствует.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxFieldSize указывается с помощью метода getMaxFieldSize в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-methods.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
