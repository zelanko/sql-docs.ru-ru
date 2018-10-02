---
title: Использование встроенной проверки подлинности Kerberos для соединения с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e4f058b1ae9f35df86b1e326c520bd4ebb588c4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47798902"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Использование встроенной проверки подлинности Kerberos для подключения к SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos типа 4. См. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) Дополнительные сведения о свойствах. Дополнительные сведения о протоколе Kerberos см. в разделе [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758).

При использовании встроенной проверки подлинности в модуле Java **Krb5LoginModule** его можно настроить с помощью [класса Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для виртуальных машин Java для IBM следующие свойства:

- **useDefaultCcache = true**
- **moduleBanner = false**

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для всех остальных машин Java следующие свойства:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

До версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)], приложение должно было указывать встроенную проверку подлинности (с помощью Kerberos или NTLM, то в зависимости от доступности) с помощью **integratedSecurity** свойство соединения и посредством указания библиотеки  **sqljdbc_auth.dll**, как описано в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md).

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos с помощью реализации протокола Kerberos исключительно на Java:

- Если необходимо, с помощью встроенной проверки подлинности **Krb5LoginModule**, по-прежнему необходимо указать **integratedSecurity = true** свойство соединения. Следует также указать **значение authenticationScheme = JavaKerberos** свойство соединения.

- Чтобы продолжить использование встроенной проверки подлинности с **sqljdbc_auth.dll**, просто укажите **integratedSecurity = true** свойство соединения (и при необходимости **значение authenticationScheme = NativeAuthentication**).

- Если указать **значение authenticationScheme = JavaKerberos** , но не указано **integratedSecurity = true**, то драйвер не будет **значение authenticationScheme** Свойство соединения и он будет ожидать искать пользователя имя и пароль в строке подключения.

Если создание соединения выполняется из источника данных, то можно программно задать схему проверки подлинности с помощью метода setAuthenticationScheme и (при необходимости) имя субъекта-службы для подключений Kerberos с помощью метода **setServerSpn**.

Для поддержки проверки подлинности по протоколу Kerberos добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Дополнительные сведения см. в статье [Трассировка операций драйвера](../../connect/jdbc/tracing-driver-operation.md).

Следующие рекомендации помогут настроить протокол Kerberos.

1. Задайте **AllowTgtSessionKey** 1 в реестре Windows. Дополнительные сведения см. в статье [Разделы реестра протокола Kerberos и параметры конфигурации KDC в Windows Server 2003](http://support.microsoft.com/kb/837361).
2. Убедитесь, что конфигурация Kerberos (файл krb5.conf в среде UNIX) содержит верные указания на область (realm) и KDC в вашей среде.
3. Инициализируйте кэш TGT с помощью kinit или войдя в домен.
4. Когда приложение, использующее свойство **authenticationScheme=JavaKerberos**, запускается в операционной системе Windows Vista или Windows 7, следует использовать стандартную учетную запись пользователя. Но если приложение запускается от имени учетной записи администратора, то оно должно запускаться с правами доступа администратора.

> [!NOTE]  
> Атрибут соединения serverSpn поддерживается только драйвером Microsoft JDBC Driver версии 4.2 или более поздней.

## <a name="service-principal-names"></a>Имена субъектов-служб

Имя участника-службы (service primary name, SPN) — это имя, по которому клиент единственным образом распознает экземпляр службы.

Вы можете указать имя субъекта-службы с помощью свойства соединения **serverSpn** или просто разрешить драйверу сформировать его (по умолчанию). Это свойство имеет вид "MSSQLSvc/fqdn:port\@REALM", где fqdn — это полное доменное имя, port — номер порта, а REALM — это область Kerberos SQL Server в верхнем регистре. Область из этого свойства является необязательной, если область конфигурации Kerberos по умолчанию совпадает с областью сервера и по умолчанию не включена. Если вы хотите поддерживать сценарии проверки подлинности между областями, в которых область по умолчанию в конфигурации Kerberos отличается от области сервера, необходимо задать имя субъекта-службы с помощью свойства serverSpn.

Например, может выглядеть ваши имя участника-службы: «MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ. CORP. CONTOSO.COM»

Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:

- [Как использовать проверку подлинности по протоколу Kerberos в SQL Server](http://support.microsoft.com/kb/319723)

- [Использование протокола Kerberos в SQL Server](http://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> До выхода версии 6.2 драйвера JDBC, правильное использование Cross сферы Kerberos, необходимо явно задать **serverSpn**.
>
> Начиная с версии 6.2, будут иметь возможность создавать драйвер **serverSpn** по умолчанию, даже при использовании Cross сферы Kerberos. Несмотря на то, что можно использовать **serverSpn** явно слишком.

## <a name="creating-a-login-module-configuration-file"></a>Создание файла конфигурации модуля входа

Можно также указать файл конфигурации Kerberos. Если файл конфигурации не указан, то будут действовать следующие настройки:

Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

Если будет использоваться файл конфигурации модуля входа, то файл должен иметь следующий формат:

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

Файл конфигурации входа состоит из одной или нескольких записей, каждая из которых описывает, какая из базовых технологий проверки подлинности должна использоваться для конкретного приложения или приложений. Например,

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

Так, каждая запись файла конфигурации модуля входа состоит из имени, за которым следует один или несколько элементов, определяемых модулем входа, причем каждый из этих элементов завершается точкой с запятой, а вся группа заключается в скобки. Каждая запись файла конфигурации завершается точкой с запятой.

Помимо возможности получения драйвером учетных данных Kerberos согласно настройкам, заданным в файле конфигурации модуля входа, драйвер может использовать существующие учетные данные. Это может оказаться полезным в том случае, когда приложению необходимо создавать соединения с учетными данными нескольких пользователей.

Драйвер попытается использовать существующие учетные данные, если они доступны, а затем попытается войти с использованием указанного модуля входа. Поэтому при использовании метода Subject.doAs для выполнения кода в определенном контексте будет создано соединение с учетными данными, переданными при вызове Subject.doAs.

Дополнительные сведения см. в разделе [Файл конфигурации входа JAAS](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) и [Класс Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Начиная с Microsoft JDBC Driver 6.2, имя файла конфигурации модуля входа при необходимости могут передаваться с помощью jaasConfigurationName свойства подключения, это позволяет иметь собственную конфигурацию входа каждого подключения.

## <a name="creating-a-kerberos-configuration-file"></a>Создание файла конфигурации Kerberos

Дополнительные сведения о файлах конфигурации Kerberos см. в разделе [Требования Kerberos](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Ниже приведен образец файла конфигурации домена, где YYYY и ZZZZ — имена доменов на сайте.

```ini
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

Файл конфигурации домена можно включить с помощью параметра -Djava.security.krb5.conf. Вы можете включить файл конфигурации модуля входа с **-Djava.security.auth.login.config**.

Например, при запуске приложения можно указать следующую командную строку:

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Проверка доступности SQL Server по протоколу Kerberos

Выполните следующий запрос в среде SQL Server Management Studio:

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

Убедитесь, что имеются достаточные разрешения для выполнения этого запроса.

## <a name="constrained-delegation"></a>Ограниченное делегирование

Начиная с Microsoft JDBC Driver 6.2, драйвер поддерживает ограниченное делегирование Kerberos. Делегированные учетные данные могут передаваться в виде объекта org.ietf.jgss.GSSCredential, эти учетные данные используются драйвером для подключения.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Подключения Kerberos с использованием имен участников и пароля

Начиная с Microsoft JDBC Driver 6.2, драйвер можно установить Kerberos при передаче соединения, с помощью имени субъекта и пароля в строке подключения.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Свойство username не требует области, если пользователь принадлежит к default_realm, в файл krb5.conf. Когда `userName` и `password` устанавливается вместе с `integratedSecurity=true;` и `authenticationScheme=JavaKerberos;` , подключение устанавливается с указанием имени как участник Kerberos вместе с введенного пароля.

## <a name="see-also"></a>См. также:

[Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
