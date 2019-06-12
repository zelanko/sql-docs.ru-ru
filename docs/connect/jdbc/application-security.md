---
title: Безопасность приложений | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 832cb6991ad095ba13226f80408fbd919db00623
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66770437"
---
# <a name="application-security"></a>Безопасность приложений
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] важно обеспечить безопасность приложения. В следующих разделах приводится информация о том, как можно обезопасить работу приложения.  
  
## <a name="using-java-policy-permissions"></a>Использование разрешений политики Java  
 При использовании драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] важно задать обязательные разрешения политики Java, необходимые драйверу JDBC. Среда Java Runtime Environment обеспечивает расширенную модель безопасности, которую можно использовать во время выполнения, чтобы определить, имеет ли поток доступ к ресурсу. Файлы политики безопасности могут управлять этим доступом. Сами файлы политики управляются администратором развертывания и системным администратором контейнера, однако разрешения, перечисленные в этом разделе, оказывают влияние на работу драйвера JDBC.  
  
 Типичное разрешение в файле политики выглядит следующим образом.  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 Следующее основание кода должно быть ограничено до основания кода драйвера JDBC, чтобы обеспечить наименьшее число привилегий.  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  Код «file:/install_dir/lib/-« ссылается на каталог установки драйвера JDBC.  
  
## <a name="protecting-server-communication"></a>Защита связи сервера  
 При использовании драйвера JDBC для связи с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обезопасить канал связи за счет использования либо протокола IPSEC, либо SSL-шифрования. Можно использовать оба метода.  
  
 Поддержка SSL обеспечивает дополнительный уровень защиты помимо IPSEC. Дополнительные сведения об использовании SSL см. в разделе [с помощью SSL-шифрование](../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>См. также:  
 [Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
