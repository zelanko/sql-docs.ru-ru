---
title: Метод (SQLServerStatement) getConnection | Документы Microsoft
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
- SQLServerStatement.getConnection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6f341d0b-265a-415e-abe5-8f408fedbb21
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eacca140b26d6b44e1d4f3d0c018e357d68c0918
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getconnection-method-sqlserverstatement"></a>getConnection метод (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) , создающего это [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.Connection getConnection()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getConnection указывается с помощью метода getConnection в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
