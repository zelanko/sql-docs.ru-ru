---
title: Метод setSavepoint () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc2a4613efe6ba8bdc40d124b058e2a47114669a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815902"
---
# <a name="setsavepoint-method-"></a>Метод setSavepoint ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает в текущей транзакции безымянную точку сохранения и возвращает новый объект [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md), который ее представляет.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект точки сохранения.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод setSavePoint указывается с помощью метода setSavePoint в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Метод setSavepoint (SQLServerConnection)](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
