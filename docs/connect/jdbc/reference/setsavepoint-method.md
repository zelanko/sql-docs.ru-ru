---
title: Метод setSavepoint () | Документы Microsoft
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
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3cdd64af1adb3dc932a63c99d8d03b09b50ce237
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="setsavepoint-method-"></a>Метод setSavepoint ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает в текущей транзакции неименованную точку сохранения и возвращает новый [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) , представляющий его.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект точки сохранения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setSavePoint указывается с помощью метода setSavePoint в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также  
 [Метод setSavepoint &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
