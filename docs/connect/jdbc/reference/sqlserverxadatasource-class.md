---
title: Класс SQLServerXADataSource | Документы Microsoft
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
ms.topic: article
ms.assetid: 95fc7b07-2498-4a7e-8f7f-ee0d86b598b4
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7745863cfa6ad05d5aefa85b865751fe3f11f392
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlserverxadatasource-class"></a>Класс SQLServerXADataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет фабрику для [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) объектов, которые используется для внутренних целей.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** [SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)  
  
 **Реализует:** javax.sql.XADataSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerXADataSource  
```  
  
## <a name="remarks"></a>Замечания  
 Объект, реализующий интерфейс SQLServerXADataSource обычно регистрируется в службе имен, использующего именования Java и каталог интерфейс JNDI.  
  
 Класс SQLServerXADataSource предоставляет подключения базы данных для использования в распределенных транзакциях (XA). Класс SQLServerXADataSource также поддерживает организацию пулов для физических соединений. Интерфейсы SQLServerXADataSource и SQLServerXAConnection, которые определены в пакете javax.sql, реализуются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
 Объект SQLServerXAConnection представляет соединение из пула, которые могут участвовать в распределенной транзакции. Точнее, SQLServerXAConnection расширяет интерфейс SQLServerPooledConnection, добавляя метод [getXAResource](../../../connect/jdbc/reference/getxaresource-method-sqlserverxaconnection.md). Этот метод создает [SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md) объекта, который может использоваться диспетчером транзакций для координации работы, выполняемой по этому соединению, с другими участниками распределенной транзакции. Так как они расширяют интерфейс SQLServerPooledConnection, SQLServerXAConnection объекты поддерживают все методы объектов SQLServerPooledConnection. Эти объекты представляют многократно используемые физические соединения с базовым источником данных и создают дескрипторы логических соединений, которые можно передавать обратно в приложение JDBC.  
  
 SQLServerXAConnection объекты создаются объектом SQLServerXADataSource. Объекты SQLServerConnectionPoolDataSource и SQLServerXADataSource похожи, поскольку они реализуются под уровнем источника данных, который является видимым для приложения JDBC. Эта архитектура позволяет [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] поддерживает распределенные транзакции, в результате которого прозрачно для приложения. Можно настроить для интеграции с SQLServerXADataSource [!INCLUDE[msCoName](../../../includes/msconame_md.md)] координатора распределенных транзакций (DTC), обеспечивая полноценную поддержку обработки распределенных транзакций.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
