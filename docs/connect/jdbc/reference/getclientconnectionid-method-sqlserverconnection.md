---
description: Метод getClientConnectionID (SQLServerConnection)
title: Метод getClientConnectionID (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 84d4ac45655231430d444781738d47de57f732b8
ms.sourcegitcommit: 827ad02375793090fa8fee63cc372d130f11393f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/04/2020
ms.locfileid: "89480778"
---
# <a name="getclientconnectionid-method-sqlserverconnection"></a>Метод getClientConnectionID (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает идентификатор соединения для последней попытки соединения, вне зависимости от того, была ли она успешной.  
  
## <a name="syntax"></a>Синтаксис  
  
``` 
public Java.util.UUID SQLServerConnection.getClientConnectionID();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 16-байтовый идентификатор GUID, представляющий идентификатор соединения для последней попытки соединения. Значение NULL, если после инициирования запроса на соединение и подтверждения перед выполнением входа произошла ошибка.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 См. сведения о [получении доступа к диагностической информации в журнале расширенных событий](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 В следующем образце кода показано, как получить идентификатор соединения.  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 В следующем образце кода показан другой способ получения идентификатора соединения.  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("...");  
ds.setPassword("...");  
ds.setServerName("...");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 Метод **getClientConnectionID** будет работать независимо от того, с какой версией сервера устанавливается соединение, но журналы расширенных событий и записи по ошибкам кольцевого буфера соединений отсутствуют в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2008 R2 и предыдущих версиях.  
  
 Идентификатор соединения можно найти в журнале расширенных событий, чтобы определить, на сервере ли произошла ошибка (если включена регистрация расширенных событий в журнале для идентификатора соединения). Для некоторых ошибок идентификатор соединения можно также найти в кольцевом буфере соединений ([Устранение неполадок подключения в SQL Server 2008 с помощью кольцевого буфера соединений](https://docs.microsoft.com/archive/blogs/sql_protocols/connectivity-troubleshooting-in-sql-server-2008-with-the-connectivity-ring-buffer)). Если в кольцевом буфере соединений идентификатор соединения отсутствует, то скорее всего возникла сетевая ошибка.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
