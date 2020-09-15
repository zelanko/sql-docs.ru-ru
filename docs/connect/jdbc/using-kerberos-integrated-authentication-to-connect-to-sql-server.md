---
description: Использование встроенной проверки подлинности Kerberos для подключения к SQL Server
title: Использование встроенной проверки подлинности Kerberos для подключения к SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/29/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1ecbffed0e29bc3a36a1129dbade504c9b03484c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88414600"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Использование встроенной проверки подлинности Kerberos для подключения к SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos типа 4. Дополнительные сведения см. в статье о [настройке свойств подключения](../../connect/jdbc/setting-the-connection-properties.md). Дополнительные сведения см. в статье [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

При использовании встроенной проверки подлинности в модуле Java **Krb5LoginModule** его можно настроить с помощью [класса Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для виртуальных машин Java для IBM следующие свойства:

- **useDefaultCcache = true**
- **moduleBanner = false**

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для всех остальных машин Java следующие свойства:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

В версиях до [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение должно было указывать встроенную проверку подлинности (по протоколу Kerberos или NTLM, в зависимости от доступности этих протоколов) с помощью свойства подключения **integratedSecurity** и посредством указания библиотеки **mssql-jdbc_auth-\<version>-\<arch>.dll**, как описано в статье [Формирование URL-адреса подключения](../../connect/jdbc/building-the-connection-url.md).

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos с помощью реализации протокола Kerberos исключительно на Java:

- Если необходимо выполнить встроенную проверку подлинности с помощью модуля **Krb5LoginModule**, все еще необходимо указывать свойство подключения **integratedSecurity=true**. Следует также указать и свойство подключения **authenticationScheme=JavaKerberos**.

- Чтобы продолжить использование встроенной проверки подлинности с библиотекой **mssql-jdbc_auth-\<version>-\<arch>.dll**, просто укажите свойство подключения **integratedSecurity=true** (можно также указать **authenticationScheme=NativeAuthentication**).

- Если указано свойство **authenticationScheme=JavaKerberos**, но не указано свойство **integratedSecurity=true**, то драйвер не будет использовать свойство подключения **authenticationScheme** и будет искать имя пользователя и пароль в строке подключения.

Если создание соединения выполняется из источника данных, то можно программно задать схему проверки подлинности с помощью метода **setAuthenticationScheme** и (при необходимости) имя субъекта-службы для подключений Kerberos с помощью метода **setServerSpn**.

Для поддержки проверки подлинности по протоколу Kerberos добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Дополнительные сведения см. в статье о [трассировке операций драйвера](../../connect/jdbc/tracing-driver-operation.md).

Следующие рекомендации помогут настроить протокол Kerberos.

1. Установите для параметра **AllowTgtSessionKey** значение 1 в реестре Windows. Дополнительные сведения см. в статье [Разделы реестра протокола Kerberos и параметры конфигурации KDC в Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Убедитесь, что конфигурация Kerberos (файл krb5.conf в среде UNIX) содержит верные указания на область (realm) и KDC в вашей среде.
3. Инициализируйте кэш TGT с помощью kinit или войдя в домен.
4. Когда приложение, использующее свойство **authenticationScheme=JavaKerberos**, запускается в операционной системе Windows Vista или Windows 7, следует использовать стандартную учетную запись пользователя. Но если приложение запускается от имени учетной записи администратора, то оно должно запускаться с правами доступа администратора.

> [!NOTE]  
> Атрибут соединения serverSpn поддерживается только драйвером Microsoft JDBC Driver версии 4.2 или более поздней.

## <a name="service-principal-names"></a>Имена субъектов-служб

Имя участника-службы (service primary name, SPN) — это имя, по которому клиент единственным образом распознает экземпляр службы.

Вы можете указать имя субъекта-службы с помощью свойства соединения **serverSpn** или просто разрешить драйверу сформировать его (по умолчанию). Это свойство имеет следующий формат: MSSQLSvc/fqdn:port\@REALM, где fqdn — это полное доменное имя, port — номер порта, а REALM  — это область Kerberos SQL Server в верхнем регистре. Область из этого свойства является необязательной, если область конфигурации Kerberos по умолчанию совпадает с областью сервера и по умолчанию не включена. Если вы хотите поддерживать сценарии проверки подлинности между областями, в которых область по умолчанию в конфигурации Kerberos отличается от области сервера, необходимо задать имя субъекта-службы с помощью свойства serverSpn.

Например, имя субъекта-службы может выглядеть так: MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ.CORP.CONTOSO.COM

Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:

- [Регистрация имя участника-службы для соединений Kerberos](../../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md)

- [Использование протокола Kerberos в SQL Server](https://docs.microsoft.com/archive/blogs/sql_protocols/using-kerberos-with-sql-server)

> [!NOTE]  
> До версии драйвера JDBC 6.2 для правильного использования протокола проверки подлинности Kerberos между областями необходимо явно задать параметр **serverSpn**.
>
> Начиная с версии 6.2, драйвер по умолчанию сможет создать параметр **serverSpn** даже при использовании протокола проверки подлинности Kerberos между областями. Хотя параметр **serverSpn** также можно использовать явно.

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

Драйвер попытается использовать существующие учетные данные, если они доступны, а затем попытается войти с использованием указанного модуля входа. Поэтому при использовании метода `Subject.doAs` для выполнения кода в определенном контексте будет создано соединение с учетными данными, переданными при вызове `Subject.doAs`.

Дополнительные сведения см. в разделе [Файл конфигурации входа JAAS](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html) и [Класс Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Начиная с версии Microsoft JDBC Driver 6.2, имя файла конфигурации модуля входа можно также передать с помощью свойства подключения `jaasConfigurationName`. Таким образом, каждое подключение получает собственную конфигурацию входа.

## <a name="creating-a-kerberos-configuration-file"></a>Создание файла конфигурации Kerberos

Дополнительные сведения о файлах конфигурации Kerberos см. в разделе [Требования Kerberos](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html).

Ниже приведен образец файла конфигурации домена, где YYYY и ZZZZ — доменные имена.

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

Файл конфигурации домена можно включить с помощью параметра -Djava.security.krb5.conf. Файл конфигурации модуля входа можно включить с помощью параметра **-Djava.security.auth.login.config**.

Например, для запуска приложения можно использовать следующую команду:

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

Начиная с версии 6.2, драйвер Microsoft JDBC поддерживает ограниченное делегирование Kerberos. Делегированные учетные данные можно передать в качестве объекта org.ietf.jgss.GSSCredential. Эти учетные данные используются драйвером для установки подключения.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Подключение Kerberos с использованием имен субъектов и пароля

Начиная с версии 6.2, драйвер Microsoft JDBC может установить подключение Kerberos, используя имя субъекта и пароль, переданные в строке подключения.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Для свойства userName не требуется использование области, если пользователь принадлежит к области default_realm, заданной в файле krb5.conf. Если `userName` и `password` заданы вместе со свойством `integratedSecurity=true;` и `authenticationScheme=JavaKerberos;`, для установки подключения используется значение userName в качестве субъекта Kerberos, а также указанный пароль.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Использование проверки подлинности Kerberos на компьютерах UNIX в том же домене

В этом учебнике предполагается, что уже существует работающая настройка Kerberos. Выполните следующий код на компьютере Windows с работающей проверкой подлинности Kerberos, чтобы убедиться, что упомянутые выше значения верны. В случае успеха код выведет текст Authentication Scheme: KERBEROS (Схема проверки подлинности: KERBEROS) в консоли. Кроме указанных, никакие дополнительные флаги времени выполнения, зависимости или параметры драйверов не требуются. Один и тот же блок кода можно запустить в Linux, чтобы проверить успешные подключения.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. Подключите клиентский компьютер к тому же домену, что и сервер.
2. (Необязательно.) Укажите местоположение билета Kerberos по умолчанию. Это удобно сделать, указав переменную среды `KRB5CCNAME`.
3. Получите билет Kerberos, создав новый или поместив имеющийся в расположение билета Kerberos по умолчанию. Чтобы создать билет, используйте терминал и инициализируйте билет с помощью `kinit USER@DOMAIN.AD`, где USER и DOMAIN.AD — субъект и домен соответственно. Пример: `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Билет будет создан в расположении билета по умолчанию или в пути `KRB5CCNAME`, если он указан.
4. Терминал запросит пароль, который нужно будет ввести.
5. Проверьте учетные данные в билете с помощью `klist` и убедитесь, что учетные данные соответствуют данным, которые вы планируете использовать для проверки подлинности.
6. Запустите приведенный выше пример кода и убедитесь, что проверка подлинности Kerberos прошла успешно.

## <a name="see-also"></a>См. также раздел

[Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
