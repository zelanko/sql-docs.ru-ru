---
title: "Метод (SQLServerConnection) isClosed | Документы Microsoft"
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
- SQLServerConnection.isClosed
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3560ab18-4350-4d02-9716-439f0c2f7142
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 634a402f06005c7235755988adf1435d38da0313
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="isclosed-method-sqlserverconnection"></a>isClosed метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, является ли это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объект был закрыт.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** значение Если соединение закрыто **false** Если это не так.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод isClosed указывается с помощью isClosed метода в интерфейсе java.sql.Connection.  
  
 Проверяет состояние вызванного объекта SQLServerConnection. Соединение закрывается, если [закрыть](../../../connect/jdbc/reference/close-method-sqlserverconnection.md) вызова метода, или если произошли определенные неустранимые ошибки. Этот метод будет возвращать **true** только когда она вызывается после вызова метода close.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

