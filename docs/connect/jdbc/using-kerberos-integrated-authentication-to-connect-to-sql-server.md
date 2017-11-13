---
title: "С помощью Kerberos, встроенная проверка подлинности для подключения к SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f26a429563aaf5c079c45b064b4723cb19cada90
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Использование встроенной проверки подлинности Kerberos для подключения к SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], приложение может использовать **authenticationScheme** свойства соединения, чтобы указать, что для подключения к базе данных с использованием встроенной проверки подлинности Kerberos типа 4. В разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) Дополнительные сведения о свойствах. Дополнительные сведения о протоколе Kerberos см. в разделе [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758).  
  
 При использовании встроенной проверки подлинности с помощью Java **Krb5LoginModule**, можно настроить с помощью модуля [класс Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Задает для виртуальных машин Java для IBM следующие свойства:  
  
-   **useDefaultCcache = true**  
  
-   **moduleBanner = false**  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Устанавливает для всех остальных машин Java следующие свойства:  
  
-   **useTicketCache = true**  
  
-   **doNotPrompt = true**  
  
## <a name="remarks"></a>Замечания  
 До появления [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], приложение должно было указывать встроенную проверку подлинности (с помощью Kerberos или NTLM, в зависимости от доступный) с помощью **integratedSecurity** свойства соединения и посредством указания библиотеки  **sqljdbc_auth.dll**, как описано в [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md).  
  
 Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], приложение может использовать **authenticationScheme** свойства соединения, чтобы указать, что для подключения к базе данных с использованием Kerberos интегрированной проверки подлинности с использованием чисто Java Kerberos Реализация:  
  
-   Если требуется встроенная проверка подлинности с помощью **Krb5LoginModule**, вам необходимо указать **integratedSecurity = true** свойство соединения. Следует также указать **authenticationScheme = JavaKerberos** свойство соединения.  
  
-   Чтобы продолжить использование встроенной проверки подлинности с **sqljdbc_auth.dll**, просто укажите **integratedSecurity = true** свойство соединения (и при необходимости **authenticationScheme = NativeAuthentication**).  
  
-   При указании **authenticationScheme = JavaKerberos** , но не указано **integratedSecurity = true**, то драйвер будет использовать **authenticationScheme** Свойство соединения и он будет ожидать искать пользователя имя и пароль в строке подключения.  
  
 При создании подключения с помощью источника данных, можно программно задать схему проверки подлинности с помощью метода setAuthenticationScheme и (необязательно) задайте имя участника-службы для соединений Kerberos с помощью **setServerSpn**.  
  
 Для поддержки проверки подлинности по протоколу Kerberos добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Дополнительные сведения см. в разделе [Трассировка операций драйвера](../../connect/jdbc/tracing-driver-operation.md).  
  
 Следующие рекомендации помогут настроить протокол Kerberos.  
  
1.  Задать **AllowTgtSessionKey** 1 в реестре Windows. Дополнительные сведения см. в разделе [конфигурации KDC в Windows Server 2003 и разделы реестра протокола Kerberos](http://support.microsoft.com/kb/837361).  
  
2.  Убедитесь, что конфигурация Kerberos (файл krb5.conf в среде UNIX) содержит верные указания на область (realm) и KDC в вашей среде.  
  
3.  Инициализируйте кэш TGT с помощью kinit или войдя в домен.  
  
4.  Когда приложение, использующее **authenticationScheme = JavaKerberos** работает в Windows Vista или Windows 7 операционных систем, следует использовать учетную запись обычного пользователя. Но если приложение запускается от имени учетной записи администратора, то оно должно запускаться с правами доступа администратора.  
  
> [!NOTE]  
>  Атрибут соединения serverSpn поддерживается только с Microsoft JDBC Driver 4.2 и более поздних версий.  
  
## <a name="service-principal-names"></a>Имена субъектов-служб  
 Имя участника-службы (service primary name, SPN) — это имя, по которому клиент единственным образом распознает экземпляр службы.  
  
 Можно указать имя участника-службы с помощью **serverSpn** свойство подключения, или просто разрешить драйверу сформировать его (по умолчанию).  Это свойство доступно в формате: "MSSQLSvc/fqdn:port@REALM" где fqdn — это полное доменное имя, port — Номер порта и REALM — это область Kerberos SQL Server в верхнем регистре.  Область из этого свойства является необязательной, если область конфигурации Kerberos по умолчанию совпадает с областью сервера и по умолчанию не включена.  Если вы хотите поддерживать сценарии проверки подлинности между областями, в которых область по умолчанию в конфигурации Kerberos отличается от области сервера, необходимо задать имя субъекта-службы с помощью свойства serverSpn.  
  
 Например, может выглядеть вашего имени участника-службы: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433@ZZZZ.CORP.CONTOSO.COM"  
  
 Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:  
  
-   [Использование проверки подлинности Kerberos в SQL Server](http://support.microsoft.com/kb/319723)  
  
-   [Использование протокола Kerberos в SQL Server](http://go.microsoft.com/fwlink/?LinkId=207814)  

> [!NOTE]  
> Перед 6.2.0 версии драйвера JDBC, для правильного использования Cross сферы Kerberos, необходимо явно задать **serverSpn**.
>
> Начиная с 6.2.0 выпуска, драйвер будет иметь возможность построения **serverSpn** по умолчанию, даже при использовании Cross сферы Kerberos. Несмотря на то, что можно использовать **serverSpn** явно слишком. 
  
## <a name="creating-a-login-module-configuration-file"></a>Создание файла конфигурации модуля входа  
 Можно также указать файл конфигурации Kerberos. Если файл конфигурации не указан, то будут действовать следующие настройки:  
  
 Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule необходимые useTicketCache = true;  
  
 IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule требовал useDefaultCcache = true;  
  
 Если будет использоваться файл конфигурации модуля входа, то файл должен иметь следующий формат:  
  
```  
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```  
  
 Файл конфигурации входа состоит из одной или нескольких записей, каждая из которых описывает, какая из базовых технологий проверки подлинности должна использоваться для конкретного приложения или приложений. Например:  
  
```  
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```  
  
 Так, каждая запись файла конфигурации модуля входа состоит из имени, за которым следует один или несколько элементов, определяемых модулем входа, причем каждый из этих элементов завершается точкой с запятой, а вся группа заключается в скобки. Каждая запись файла конфигурации завершается точкой с запятой.  
  
 Помимо возможности получения драйвером учетных данных Kerberos согласно настройкам, заданным в файле конфигурации модуля входа, драйвер может использовать существующие учетные данные. Это может оказаться полезным в том случае, когда приложению необходимо создавать соединения с учетными данными нескольких пользователей.  
  
 Драйвер попытается использовать существующие учетные данные, если они доступны, а затем попытается войти с использованием указанного модуля входа. Поэтому при использовании метода Subject.doAs для выполнения кода в определенном контексте будет создано соединение с учетными данными, переданными при вызове Subject.doAs.  
  
 Дополнительные сведения см. в разделе [файл конфигурации входа JAAS](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) и [класс Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).  

 Начиная с Microsoft JDBC Driver 6.2, имя файла конфигурации модуля входа при необходимости могут передаваться с помощью jaasConfigurationName свойства подключения, это позволяет иметь собственную конфигурацию входа каждого соединения.
 
## <a name="creating-a-kerberos-configuration-file"></a>Создание файла конфигурации Kerberos  
 Дополнительные сведения о файлах конфигурации Kerberos см. в разделе [требования Kerberos](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).  
  
 Ниже приведен образец файла конфигурации домена, где YYYY и ZZZZ — имена доменов на сайте.  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
  
[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  
  
        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  
  
```  
  
## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>Включение файла конфигурации домена и файла конфигурации модуля входа  
 Файл конфигурации домена можно включить с помощью параметра -Djava.security.krb5.conf. Можно включить файл конфигурации модуля входа с **-Djava.security.auth.login.config**.  
  
 Например, при запуске приложения можно указать следующую командную строку:  
  
```  
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  
  
```  
  
## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Проверка доступности SQL Server по протоколу Kerberos  
 Выполните следующий запрос в среде SQL Server Management Studio:  
  
 **Выберите auth_scheme из sys.dm_exec_connections где session_id = @@spid**  
  
 Убедитесь, что имеются достаточные разрешения для выполнения этого запроса.  

## <a name="constrained-delegation"></a>Ограниченное делегирование
Начиная с Microsoft JDBC Driver 6.2, драйвер поддерживает ограниченное делегирование Kerberos. Делегированные учетные данные могут передаваться в виде объекта org.ietf.jgss.GSSCredential, эти учетные данные используются драйвером для установления соединения. 

```
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Подключение Kerberos с использованием имен участников и пароля
Начиная с Microsoft JDBC Driver 6.2, драйвер может установить Kerberos при передаче соединения с использованием имени участника-службы и пароля в строке подключения. 
```
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```
Свойство username не требуется область, если пользователь принадлежит к default_realm, в файл krb5.conf. Когда `userName` и `password` устанавливается вместе с `integratedSecurity=true;` и `authenticationScheme=JavaKerberos;` свойство соединения устанавливается значение имени пользователя как участника Kerberos вместе с паролем, указанному.
 
## <a name="see-also"></a>См. также:  
 [Подключение к SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  

