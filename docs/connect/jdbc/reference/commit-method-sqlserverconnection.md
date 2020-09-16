---
description: Метод commit (SQLServerConnection)
title: Метод commit (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50fe66c673f443c7c69e26ca608562794950558f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438036"
---
# <a name="commit-method-sqlserverconnection"></a>Метод commit (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Фиксация всех изменений, выполненных после предыдущей операции фиксации или отката, и снятие в базе данных всех блокировок, удерживаемых в настоящее время данным объектом [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод commit определяется методом commit в интерфейсе java.sql.Connection.  
  
 Этот метод следует использовать, только если отключен режим автоматической фиксации.  
  
 Заметьте, что если клиент запускает транзакцию вручную, а затем по какой-либо причине SQL Server выполняет откат этой транзакции, то этот метод завершает работу с ошибкой и вызывает исключение. Например, если клиент вызывает хранимую процедуру, которая явно вызывает команду ROLLBACK TRANSACTION, а затем клиент вызывает метод commit, то вызывается исключение. Кроме того, если в SQL Server происходит ошибка достаточного уровня серьезности (16 и выше) для отката ручной транзакции, запущенной клиентом, то последующий вызов метода commit приведет к созданию исключения.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
