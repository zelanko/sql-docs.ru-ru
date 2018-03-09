---
title: "Элементы SQLServerXAConnection | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 88fc82e655317b6dadd5795c575d58d8edec3040
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverxaconnection-members"></a>Элементы SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены члены, предоставляемые [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) класса.  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) регистрирует заданный прослушиватель событий будет получать уведомления при возникновении события для этого объекта соединения.|  
|[Закрыть](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) закрывает физическое соединение, представляемое этим объектом соединения.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) создает дескриптор объекта для физического соединения, представляемого данным объектом соединения.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Извлекает [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) , диспетчер транзакций будет использовать для управления участием этого [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) объекта распределенной транзакции.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)) Удаляет заданный прослушиватель событий.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
