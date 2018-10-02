---
title: Класс SQLServerXADataSource | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa85b61a67655fbf363c1927b48cd79f8ff841ce
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47774422"
---
# <a name="sqlserverxadatasource-class"></a>Класс SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет фабрику для объектов [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md), предназначенных для внутреннего использования.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Реализует:** javax.sql.XADataSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Remarks  
 Объект, который реализует интерфейс SQLServerXADataSource, обычно регистрируется в службе имен, которая использует интерфейс JNDI.  
  
 Класс SQLServerXADataSource представляет соединения с базой данных для использования в распределенных транзакциях (XA). Класс SQLServerXADataSource также поддерживает организацию пулов для физических соединений. Интерфейсы SQLServerXADataSource и SQLServerXAConnection, которые определены в пакете javax.sql, реализуются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Объект SQLServerXAConnection представляет соединение из пула, которое может участвовать в распределенной транзакции. Точнее, SQLServerXAConnection расширяет интерфейс SQLServerPooledConnection, добавляя метод [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Этот метод создает объект [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md), который может использоваться диспетчером транзакций для координации работы, выполняемой по этому соединению, с другими участниками распределенной транзакции. Так как они расширяют интерфейс SQLServerPooledConnection, SQLServerXAConnection объекты поддерживают все методы объектов SQLServerPooledConnection. Эти объекты представляют многократно используемые физические соединения с базовым источником данных и создают дескрипторы логических соединений, которые можно передавать обратно в приложение JDBC.  
  
 SQLServerXAConnection объекты создаются объектом SQLServerXADataSource. SQLServerConnectionPoolDataSource объекты и объекты SQLServerXADataSource похожи, так как они реализуются под уровнем источника данных, который является видимым для приложения JDBC. Эта архитектура позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживать распределенные транзакции прозрачным для приложения способом. SQLServerXADataSource можно настроить для интеграции с координатором распределенных транзакций (DTC) [!INCLUDE[msCoName](../../../includes/msconame_md.md)], обеспечивая полноценную поддержку обработки распределенных транзакций.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
