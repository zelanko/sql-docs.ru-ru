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
ms.openlocfilehash: 4c456336170cd7d4ad7cf37a0eebc52637f0a070
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970224"
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
  
 Класс SQLServerXADataSource представляет соединения с базой данных для использования в распределенных транзакциях (XA). Класс SQLServerXADataSource также поддерживает пулы подключений для физических подключений. Интерфейсы SQLServerXADataSource и SQLServerXAConnection, которые определены в пакете javax. SQL, реализуются с помощью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Объект SQLServerXAConnection представляет соединение из пула, которое может участвовать в распределенной транзакции. Точнее, SQLServerXAConnection расширяет интерфейс SQLServerPooledConnection, добавляя метод [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Этот метод создает объект [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md), который может использоваться диспетчером транзакций для координации работы, выполняемой по этому соединению, с другими участниками распределенной транзакции. Поскольку они расширяют интерфейс SQLServerPooledConnection, объекты SQLServerXAConnection поддерживают все методы объектов SQLServerPooledConnection. Эти объекты представляют многократно используемые физические соединения с базовым источником данных и создают дескрипторы логических соединений, которые можно передавать обратно в приложение JDBC.  
  
 Объекты SQLServerXAConnection создаются объектом SQLServerXADataSource. Объекты SQLServerConnectionPoolDataSource и объекты SQLServerXADataSource похожи, так как они реализуются на уровне источника данных, который является видимым для приложения JDBC. Эта архитектура позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживать распределенные транзакции прозрачным для приложения способом. SQLServerXADataSource можно настроить для интеграции с координатором распределенных транзакций (DTC) [!INCLUDE[msCoName](../../../includes/msconame_md.md)], обеспечивая полноценную поддержку обработки распределенных транзакций.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Справка по API драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
