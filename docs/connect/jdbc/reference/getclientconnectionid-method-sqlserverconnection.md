---
title: Метод getClientConnectionID (SQLServerConnection) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: bee39c11-733a-461f-92cc-33efcb2af87d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bcd24325ca26bacc9f474e925f99848d68351417
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>Замечания  
 Дополнительные сведения о доступе к диагностической информации в журнале расширенных событий см. в разделе [доступ к диагностической информации в журнале расширенных событий](../../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md).  
  
 В следующем образце кода показано, как получить идентификатор соединения.  
  
```  
Connection con = DriverManager.getConnection(connectionUrl);  
UUID id = ((ISQLServerConnection)con).getClientConnectionId();  
```  
  
 В следующем образце кода показан другой способ получения идентификатора соединения.  
  
```  
SQLServerConnectionPoolDataSource ds = new SQLServerConnectionPoolDataSource();  
ds.setUser("…");  
ds.setPassword("…");  
ds.setServerName("…");  
PooledConnection pcon= ds.getPooledConnection();  
Connection cn = pcon.getConnection();  
UUID conid = ((ISQLServerConnection)cn).getClientConnectionId();  
```  
  
 **getClientConnectionID** работает независимо от того, какая версия сервера устанавливается соединение, но журналы расширенных событий и записи по ошибкам кольцевого буфера соединений будет отсутствовать в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] 2008 R2 и более ранних версий.  
  
 Идентификатор соединения можно найти в журнале расширенных событий, чтобы определить, на сервере ли произошла ошибка (если включена регистрация расширенных событий в журнале для идентификатора соединения). Идентификатор соединения можно также найти в кольцевом буфере соединений ([Устранение неполадок подключения в SQL Server 2008 с помощью кольцевого буфера подключения](http://go.microsoft.com/fwlink/?LinkId=207752)) для определенных ошибок подключения. Если в кольцевом буфере соединений идентификатор соединения отсутствует, то скорее всего возникла сетевая ошибка.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
