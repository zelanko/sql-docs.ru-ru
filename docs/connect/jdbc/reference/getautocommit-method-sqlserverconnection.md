---
title: "Метод (SQLServerConnection) getAutoCommit | Документы Microsoft"
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
- SQLServerConnection.getAutoCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: af1f67f4-f568-4e58-abcc-5c809a89b547
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e2c8ee804ede53953f531fe945da39c7c0667cae
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# getAutoCommit метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает текущий режим автоматической фиксации для данного [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
## Синтаксис  
  
```  
  
public boolean getAutoCommit()  
```  
  
## Возвращаемое значение  
 **значение true,** Если включен режим автоматической фиксации, **false** Если это не так.  
  
## Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## Замечания  
 Этот метод getAutoCommit указывается с помощью метода getAutoCommit в интерфейсе java.sql.Connection.  
  
## См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

