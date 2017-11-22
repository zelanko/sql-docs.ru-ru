---
title: "Построение URL-адрес подключения | Документы Microsoft"
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
ms.assetid: 44996746-d373-4f59-9863-a8a20bb8024a
caps.latest.revision: "53"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 81176070a9363e54dc469dd050891335edcb92af
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="building-the-connection-url"></a>Формирование URL-адреса соединения
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Обычно URL-адреса соединения выглядят следующим образом:  
  
 `jdbc:sqlserver://[serverName[\instanceName][:portNumber]][;property=value[;property=value]]`  
  
 где:  
  
-   **JDBC:SQLServer: / /** (обязательно) известен как подпротокол и является константой.  
  
-   **serverName** (необязательно) является адресом сервера для подключения. Это может быть DNS, IP-адрес, локальный узел или 127.0.0.1 локального компьютера. Имя сервера необходимо указать в коллекции свойств, если оно не указано в URL-адресе соединения.  
  
-   **instanceName** (необязательно) является экземпляр для соединение с serverName. Подключение выполняется к экземпляру по умолчанию, если не указано другое.  
  
-   **portNumber** (необязательно) — это порт, чтобы соединение с serverName. Значение по умолчанию — 1433. Если соединение выполняется с портом по умолчанию, в URL-адресе необязательно указывать порт или символ ':' перед ним.  
  
    > [!NOTE]  
    >  Для оптимизации производительности соединения при соединении с именованным экземпляром необходимо указать portNumber. Это позволит избежать дополнительного обращения к серверу для определения номера порта. Если используются portNumber и instanceName, portNumber будет иметь более высокий приоритет, и instanceName будет пропущен.  
  
-   **Свойство** (необязательно) является одно или несколько свойств параметров подключения. Дополнительные сведения см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md). Можно указать любое свойство из списка. В качестве разделителей в списке свойств можно использовать точку с запятой (';'), при этом свойства не могут повторяться.  
  
> [!CAUTION]  
>  В целях безопасности не рекомендуется составлять URL-адрес соединения на основе данных пользователей. В URL-адресе необходимо указывать только имя сервера и драйвер. Для указания значений имени пользователя и пароля следует использовать коллекции свойств соединения. Дополнительные сведения о безопасности в приложениях JDBC см. в разделе [защита приложений драйвера JDBC](../../connect/jdbc/securing-jdbc-driver-applications.md).  
  
## <a name="connection-examples"></a>Примеры соединения  
 Подключитесь к базе данных по умолчанию на локальном компьютере с помощью имени пользователя и пароля:  
  
 `jdbc:sqlserver://localhost;user=MyUserName;password=*****;`  
  
> [!NOTE]  
>  Хотя в предыдущем примере в строке подключения указывались имя пользователя и пароль, следует использовать встроенную безопасность, так как она более надежна. Дополнительные сведения см. в разделе [соединение с помощью встроенной проверки подлинности](#Connectingintegrated) далее в этом разделе.  
  
 Следующая строка подключения показан пример того, как подключиться к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью встроенной проверки подлинности и Kerberos из приложения, работающего в любой операционной системе, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]:  
  
```  
jdbc:sqlserver://;servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos  
```  
  
 Подключитесь к базе данных по умолчанию на локальном компьютере с помощью встроенной проверки подлинности:  
  
 `jdbc:sqlserver://localhost;integratedSecurity=true;`  
  
 Подключитесь к именованной базе данных на удаленном сервере:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Подключитесь к удаленному серверу с использованием порта по умолчанию:  
  
 `jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 Подключитесь, указав настраиваемое имя приложения:  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;applicationName=MyApp;`  
  
## <a name="named-and-multiple-sql-server-instances"></a>Именованные и множественные экземпляры SQL Server  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]обеспечивает возможность установки нескольких экземпляров на одном сервере. Все экземпляры идентифицируются с помощью специального имени. Для подключения к именованному экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], либо можно указать номер порта именованного экземпляра (рекомендуется), или можно указать имя экземпляра в качестве свойства URL-адреса JDBC или **datasource** свойство. Если имя экземпляра или свойство номера порта не указано, создается соединение с экземпляром по умолчанию. См. следующие примеры.  
  
 Чтобы использовать номер порта, выполните следующие действия:  
  
 `jdbc:sqlserver://localhost:1433;integratedSecurity=true;<more properties as required>;`  
  
 Чтобы использовать свойство URL-адреса JDBC, выполните следующие действия:  
  
 `jdbc:sqlserver://localhost;instanceName=instance1;integratedSecurity=true;<more properties as required>;`  
  
## <a name="escaping-values-in-the-connection-url"></a>Экранирование значений в URL-адресе соединения  
 Может потребоваться преобразование определенных частей значений URL-адреса соединения из-за включения специальных символов, таких как пробелы, точек с запятой и кавычек. Драйвер JDBC поддерживает преобразование этих значений, если они заключены в скобки. Например, {;} указывает на преобразование точки с запятой.  
  
 Преобразованные значения могут содержать специальные символы (особенно '=', ';', '[]' и пробелы), но не могут содержать скобок. Значения, которые необходимо преобразовать, и значения, содержащие скобки, следует добавить к коллекции свойств.  
  
> [!NOTE]  
>  Пустое пространство внутри скобок является литералом и не усекается.  
  
##  <a name="Connectingintegrated"></a>Соединение с помощью встроенной проверки подлинности Windows  
 Драйвер JDBC поддерживает использование встроенной проверки подлинности типа 2 в операционных системах Windows с использованием свойства строки соединения integratedSecurity. Чтобы использовать встроенную проверку подлинности, скопируйте файл sqljdbc_auth.dll в системный каталог Windows на компьютере, на котором установлен драйвер JDBC.  
  
 Файлы sqljdbc_auth.dll устанавливаются в следующем местоположении:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \auth\  
  
 Для любой операционной системы, поддерживаемые [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], в разделе [с помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md) описание это компонент, добавленный в [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] , позволяет приложению для подключения к База данных при использовании встроенной проверки подлинности Kerberos типа 4.  
  
> [!NOTE]  
>  При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64.  
  
 Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. Например, если драйвер JDBC установлен в каталоге по умолчанию, можно указать местоположение файла DLL, использовав следующий аргумент виртуальной машины (VM) при запуске приложения Java:  
  
 `-Djava.library.path=C:\Microsoft JDBC Driver 4.0 for SQL Server\sqljdbc_<version>\enu\auth\x86`  
  
## <a name="connecting-with-ipv6-addresses"></a>Соединение с помощью IPv6-адресов  
 Драйвер JDBC поддерживает использование IPv6-адресов с коллекцией свойств соединения и свойством строки соединения serverName. Исходное значение serverName, такое как jdbc:*sqlserver*://*serverName*, не поддерживается для IPv6-адресов в строках соединения. С помощью имени для *serverName* вместо неизмененного IPv6-адреса будет достаточно для всех вариантов подключения. Следующие примеры можно использовать как дополнительные источники сведений.  
  
 **Использование свойства serverName**  
  
 `jdbc:sqlserver://;serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1;integratedSecurity=true;`  
  
 **Для использования свойства коллекции**  
  
 `Properties pro = new Properties();`  
  
 `pro.setProperty("serverName", "serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1");`  
  
 `Connection con = DriverManager.getConnection("jdbc:sqlserver://;integratedSecurity=true;", pro);`  
  
## <a name="see-also"></a>См. также:  
 [Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
