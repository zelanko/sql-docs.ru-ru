---
title: Безопасность приложения | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 81c57e5ab7ca88267693690992106b5f39e2af82
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69028514"
---
# <a name="application-security"></a>Защита приложений
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
  
## <a name="protecting-server-communication"></a>Защита обмена данными с сервером  
 При использовании драйвера JDBC для связи с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно обезопасить канал связи за счет использования либо протокола IPSEC, либо SSL-шифрования. Можно использовать оба метода.  
  
 Поддержка SSL обеспечивает дополнительный уровень защиты помимо IPSEC. Дополнительные сведения об SSL см. в статье об [использовании SSL-шифрования](../../connect/jdbc/using-ssl-encryption.md).  
  
## <a name="see-also"></a>См. также раздел  
 [Защита приложений JDBC Driver](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
