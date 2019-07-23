---
title: Использование встроенной проверки подлинности Kerberos для соединения с SQL Server | Документы Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 894da21c079b776524c07cab8b8f223bae769aee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916236"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Использование встроенной проверки подлинности Kerberos для подключения к SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos типа 4. Дополнительные сведения о свойствах соединения см. в разделе [Настройка свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) . Дополнительные сведения о протоколе Kerberos см. в разделе [Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758).

При использовании встроенной проверки подлинности в модуле Java **Krb5LoginModule** его можно настроить с помощью [класса Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html).

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для виртуальных машин Java для IBM следующие свойства:

- **useDefaultCcache = true**
- **Модулебаннер = false**

Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] устанавливает для всех остальных машин Java следующие свойства:

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

До, в приложениях можно было указать встроенную проверку подлинности (с использованием Kerberos или NTLM, в зависимости от доступности) с помощью свойства соединения **IntegratedSecurity** и ссылки на **sqljdbc_auth. dll.** [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] описывается в разделе [Создание URL-адреса подключения](../../connect/jdbc/building-the-connection-url.md).

Начиная с версии [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] приложение может с помощью свойства соединения **authenticationScheme** указать, что соединение с базой данных должно выполняться с использованием встроенной проверки подлинности Kerberos с помощью реализации протокола Kerberos исключительно на Java:

- Если требуется встроенная проверка подлинности с помощью **Krb5LoginModule**, необходимо по-прежнему указать свойство соединения **IntegratedSecurity = true** . Затем необходимо также указать свойство соединения **аусентикатионсчеме = жавакерберос** .

- Чтобы продолжить использовать встроенную проверку подлинности с помощью **sqljdbc_auth. dll**, просто укажите свойство соединения **IntegratedSecurity = true** (и, при необходимости, **аусентикатионсчеме = нативеаусентикатион**).

- Если указать **аусентикатионсчеме = жавакерберос** , но не указать **IntegratedSecurity = true**, драйвер будет игнорировать свойство подключения **аусентикатионсчеме** , и оно будет искать имя пользователя и пароль. учетные данные в строке подключения.

Если создание соединения выполняется из источника данных, то можно программно задать схему проверки подлинности с помощью метода **setAuthenticationScheme** и (при необходимости) имя субъекта-службы для подключений Kerberos с помощью метода **setServerSpn**.

Для поддержки проверки подлинности по протоколу Kerberos добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.KerbAuthentication. Дополнительные сведения см. в статье [Трассировка операций драйвера](../../connect/jdbc/tracing-driver-operation.md).

Следующие рекомендации помогут настроить протокол Kerberos.

1. Задайте для **алловтгтсессионкэй** значение 1 в реестре для Windows. Дополнительные сведения см. в статье [Разделы реестра протокола Kerberos и параметры конфигурации KDC в Windows Server 2003](https://support.microsoft.com/kb/837361).
2. Убедитесь, что конфигурация Kerberos (файл krb5.conf в среде UNIX) содержит верные указания на область (realm) и KDC в вашей среде.
3. Инициализируйте кэш TGT с помощью kinit или войдя в домен.
4. Когда приложение, использующее свойство **authenticationScheme=JavaKerberos**, запускается в операционной системе Windows Vista или Windows 7, следует использовать стандартную учетную запись пользователя. Но если приложение запускается от имени учетной записи администратора, то оно должно запускаться с правами доступа администратора.

> [!NOTE]  
> Атрибут соединения serverSpn поддерживается только драйвером Microsoft JDBC Driver версии 4.2 или более поздней.

## <a name="service-principal-names"></a>Имена субъектов-служб

Имя участника-службы (service primary name, SPN) — это имя, по которому клиент единственным образом распознает экземпляр службы.

Вы можете указать имя субъекта-службы с помощью свойства соединения **serverSpn** или просто разрешить драйверу сформировать его (по умолчанию). Это свойство имеет вид "MSSQLSvc/fqdn:port\@REALM", где fqdn — это полное доменное имя, port — номер порта, а REALM — это область Kerberos SQL Server в верхнем регистре. Область из этого свойства является необязательной, если область конфигурации Kerberos по умолчанию совпадает с областью сервера и по умолчанию не включена. Если вы хотите поддерживать сценарии проверки подлинности между областями, в которых область по умолчанию в конфигурации Kerberos отличается от области сервера, необходимо задать имя субъекта-службы с помощью свойства serverSpn.

Например, имя субъекта-службы может выглядеть следующим образом: "MSSQLSvc/some/Server. zzz. Corp. contoso.\@com: 1433 ZZZZ. Корпорация. CONTOSO.COM "

Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:

- [Как использовать проверку подлинности по протоколу Kerberos в SQL Server](https://support.microsoft.com/kb/319723)

- [Использование протокола Kerberos в SQL Server](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> До 6,2 версии драйвера JDBC для правильного использования междоменного протокола Kerberos необходимо явно задать **serverSpn**.
>
> Начиная с версии 6,2 драйвер будет по умолчанию создавать **serverSpn** , даже если используется межсферная Kerberos. Хотя он также может использовать **serverSpn** явным образом.

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

Начиная с версии Microsoft JDBC Driver 6,2, имя файла конфигурации модуля входа может быть передано с помощью свойства `jaasConfigurationName`Connection, что позволяет каждому соединению иметь собственную конфигурацию входа.

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

Файл конфигурации домена можно включить с помощью параметра -Djava.security.krb5.conf. Файл конфигурации модуля входа можно включить с параметром **-Джава. Security. auth. Login. config**.

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

Начиная с Microsoft JDBC Driver 6,2 драйвер поддерживает ограниченное делегирование Kerberos. Делегированные учетные данные можно передать в качестве объекта org. IETF. жгсс. Гсскредентиал. Эти учетные данные используются драйвером для установления соединения.

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Подключение Kerberos с использованием имен участников и пароля

Начиная с драйвера Microsoft JDBC Driver 6,2 драйвер может установить подключение Kerberos, используя имя участника и пароль, переданные в строке подключения.

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Свойство UserName не требует использования области, если пользователь принадлежит к default_realm, заданному в файле krb5. conf. Если `userName` параметр `password` и задан вместе со `integratedSecurity=true;` свойством и `authenticationScheme=JavaKerberos;` , то соединение устанавливается со значением username в качестве участника Kerberos, а также с указанным паролем.

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>Использование проверки подлинности Kerberos на компьютерах UNIX в том же домене

В этом учебнике предполагается, что уже существует работающая программа установки Kerberos. Выполните следующий код на компьютере Windows с работающей проверкой подлинности Kerberos, чтобы убедиться, что упомянутые выше значения верны. При успешном выполнении кода в консоли будет напечатана "схема проверки подлинности: KERBEROS". Никакие дополнительные флаги времени выполнения, зависимости или параметры драйверов не требуются за пределами указанных. Один и тот же блок кода можно запустить в Linux, чтобы проверить успешные подключения.

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

1. Домен присоедините клиентский компьютер к тому же домену, что и сервер.
2. Используемых Задайте расположение билета Kerberos по умолчанию. Это наиболее удобно сделать, задав `KRB5CCNAME` переменную среды.
3. Получите билет Kerberos, создав новый или поместив существующий в расположение билета Kerberos по умолчанию. Чтобы создать билет, просто используйте терминал и инициализируйте билет, используя `kinit USER@DOMAIN.AD` "User" и "Domain". AD "— основной субъект и домен, соответственно. Пример: `kinit SQL_SERVER_USER03@MICROSOFT.COM`. Билет будет создан в расположении билета по умолчанию или в `KRB5CCNAME` указанном пути.
4. Терминал запросит пароль, введите пароль.
5. Проверьте учетные данные в билете `klist` с помощью и подтвердите учетные данные, которые вы хотите использовать для проверки подлинности.
6. Запустите приведенный выше пример кода и убедитесь, что проверка подлинности Kerberos прошла успешно.

## <a name="see-also"></a>См. также:

[Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
