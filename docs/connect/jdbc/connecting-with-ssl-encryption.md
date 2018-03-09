---
title: "Подключение с шифрованием SSL | Документы Microsoft"
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
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
caps.latest.revision: "18"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: c359bd9c80317302288b56b1a5216b68f30e34ab
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="connecting-with-ssl-encryption"></a>Соединение с помощью SSL-шифрования
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В примерах из этого раздела описывается использование свойств строки соединения, которые разрешают приложениям использовать шифрование SSL в приложении Java. Дополнительные сведения об этих новых соединений строка свойства, такие как **шифрования**, **trustServerCertificate**, **trustStore**,  **trustStorePassword**, и **hostNameInCertificate**, в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 При **шифрования** свойству **true** и **trustServerCertificate** свойству **true**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] не будет проверять [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат. Обычно это требуется для разрешает соединения в тестовой среде, например where [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] экземпляр имеет только самозаверяющий сертификат.  
  
 В следующем примере кода показано, как задать **trustServerCertificate** свойства в строке подключения:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 При **шифрования** свойству **true** и **trustServerCertificate** свойству **false**, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] будет проверена [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат. Проверка сертификата сервера является частью SSL-подтверждения и гарантирует, что для подключения выбран правильный сервер. Чтобы проверить сертификат сервера, необходимо предоставить данные о доверии во время установления соединения с помощью **trustStore** и **trustStorePassword** свойства подключения явным образом или с помощью неявно хранилища доверия базовой виртуальной машины Java (JVM) по умолчанию.  
  
 **TrustStore** свойство указывает путь (включая имя файла) к файлу сертификата trustStore, который содержит список сертификатов, которым доверяет клиент. **TrustStorePassword** свойство указывает пароль, используемый для проверки целостности данных trustStore. Дополнительные сведения об использовании доверенного хранилища JVM по умолчанию см. в разделе [настройки клиента для SSL-шифрования](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md).  
  
 В следующем примере кода показано, как задать **trustStore** и **trustStorePassword** свойства в строке подключения:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 Драйвер JDBC предоставляет дополнительное свойство **hostNameInCertificate**, который указывает имя узла сервера. Значение этого свойства должно совпадать со значением свойства subject сертификата.  
  
 В следующем примере кода демонстрируется использование **hostNameInCertificate** свойства в строке подключения:  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  Кроме того, можно задать значение свойства соединения, используя соответствующую **setter** методы, предоставляемые [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса.  
  
 Если **шифрования** свойству **true** и **trustServerCertificate** свойству **false** и, если имя сервера в Строка подключения не соответствует имени сервера в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL-сертификат выдается следующая ошибка: драйверу не удалось установить безопасное подключение к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , используя шифрование Secure Sockets Layer (SSL). Ошибка «java.security.cert.CertificateException: не удалось проверить имя сервера в сертификате при инициализации SSL».  
  
## <a name="see-also"></a>См. также:  
 [С помощью шифрования SSL](../../connect/jdbc/using-ssl-encryption.md)   
 [Защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
