---
title: Элементы SQLServerXAConnection | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b61dabd-369b-460c-8450-9fe424f76541
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1d465b21146d656fe04e25dd3ce08356af93b501
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926984"
---
# <a name="sqlserverxaconnection-members"></a>Элементы SQLServerXAConnection
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  В следующих таблицах перечислены доступные элементы класса [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md).  
  
## <a name="constructors"></a>Конструкторы  
 Нет.  
  
## <a name="fields"></a>Поля  
 Нет.  
  
## <a name="inherited-fields"></a>Наследуемые поля  
 Нет.  
  
## <a name="methods"></a>Методы  
  
|Имя|Description|  
|----------|-----------------|  
|[addConnectionEventListener](../../../connect/jdbc/reference/addconnectioneventlistener-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)). Регистрирует заданный прослушиватель событий для получения уведомлений о событии в этом объекте Connection.|  
|[close](../../../connect/jdbc/reference/close-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)). Закрывает физическое соединение, представляемое этим объектом Connection.|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)). Создает дескриптор объекта для физического соединения, представляемого этим объектом Connection.|  
|[getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md)|Возвращает объект [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md), который будет использоваться диспетчером транзакций для управления участием этого объекта [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) в распределенной транзакции.|  
|[removeConnectionEventListener](../../../connect/jdbc/reference/removeconnectioneventlistener-method-sqlserverpooledconnection.md)|(Наследуется от [SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)). Удаляет заданный прослушиватель событий.|  
  
## <a name="inherited-methods"></a>Наследуемые методы  
  
|Класс, из которого наследуется:|Методы|  
|---------------------------|-------------|  
|com.microsoft.sqlserver.jdbc.SQLServerPooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
|java.lang.Object|clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait|  
|javax.sql.PooledConnection|addConnectionEventListener, close, getConnection, removeConnectionEventListener|  
  
## <a name="see-also"></a>См. также:  
 [Класс SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)  
  
  
