---
title: COMMIT-метод (SQLServerConnection) | Документы Microsoft
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
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8999c0bf7a7be89cead090bbbfd4d2ae767217a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="commit-method-sqlserverconnection"></a>COMMIT-метод (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Фиксирует все изменения, внесенные с момента предыдущей операции фиксации или отката постоянной и снимает базе данных все блокировки, удерживаемые в настоящее время это [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод фиксации указывается с помощью метода фиксации в интерфейсе java.sql.Connection.  
  
 Этот метод следует использовать, только если отключен режим автоматической фиксации.  
  
 Заметьте, что если клиент запускает транзакцию вручную, а затем по какой-либо причине SQL Server выполняет откат этой транзакции, то этот метод завершает работу с ошибкой и вызывает исключение. Например исключение возникает в том случае, если клиент вызывает хранимую процедуру, которая явно вызывает команду ROLLBACK TRANSACTION, и затем клиент вызывает метод commit. Кроме того, если SQL Server происходит ошибка достаточного уровня серьезности (16 и выше) для отката, инициированное клиентом ручной транзакции; Следующий вызов метода фиксации возникает исключение.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
