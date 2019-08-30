---
title: Использование проверки подлинности NTLM для подключения к SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: lilgreenbird
ms.author: v-susanh
manager: kenvh
ms.openlocfilehash: 2fab4794544ada07e0bf5e690da35b72ad6b7421
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026105"
---
# <a name="using-ntlm-authentication-to-connect-to-sql-server"></a>Использование проверки подлинности NTLM для подключения к SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Позволяет приложению использовать свойство соединения **аусентикатионсчеме**, чтобы указать, что ему требуется подключение к базе данных с использованием проверки подлинности NTLM v2. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 

Для проверки подлинности NTLM также используются следующие свойства:

- **домен = имя_домена** используемых
- **пользователь = имя пользователя**
- **пароль = password**
- **integratedSecurity = true**

Кроме **домена**, другие свойства являются обязательными, драйвер выдает ошибку, если она отсутствует при использовании свойства **NTLM** аусентикатионсчеме. 

Дополнительные сведения о свойствах соединения см. [в разделе Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md). Дополнительные сведения о протоколе проверки подлинности Microsoft NTLM см. в разделе [Microsoft NTLM](https://docs.microsoft.com/windows/desktop/SecAuthN/microsoft-ntlm).

## <a name="remarks"></a>Remarks

Описание параметров SQL Server, управляющих поведением проверки подлинности NTLM, см. в разделе [Сетевая безопасность: уровень проверки подлинности LAN Manager](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-security-lan-manager-authentication-level) . 

## <a name="logging"></a>Ведение журнала

Для поддержки аутентификации NTLM добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.NTLMAuthentication. Дополнительные сведения см. в статье [Трассировка операций драйвера](../../connect/jdbc/tracing-driver-operation.md).

## <a name="datasource"></a>DataSource

При использовании источника данных для создания подключений свойства NTLM могут быть заданы программно с помощью **сетаусентикатионсчеме**, **сетдомаин**и (необязательно) **сетсерверспн**.

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("NTLM");
ds.setDomain("<domainName>");
ds.setUser("<userName>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setServerSpn("<serverSpn");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

## <a name="service-principal-names"></a>Имена субъектов-служб

Имя участника-службы (service primary name, SPN) — это имя, по которому клиент единственным образом распознает экземпляр службы.

Вы можете самостоятельно указать имя субъекта-службы с помощью свойства подключения **serverSpn** или разрешить драйверу создать его (вариант по умолчанию). Это свойство имеет вид MSSQLSvc/fqdn:port\@REALM, где fqdn — это полное доменное имя, port — номер порта, а REALM — область SQL Server в верхнем регистре. Область этого свойства является необязательной, так как область по умолчанию совпадает с областью сервера.

Например, имя субъекта-службы может выглядеть следующим образом: "MSSQLSvc/some/Server. zzz. Corp. contoso. com: 1433"

Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:

- [Поддержка имени субъекта-службы в клиентских соединениях](https://docs.microsoft.com/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections?view=sql-server-2017)

> [!NOTE]  
> Атрибут соединения serverSpn поддерживается только драйвером Microsoft JDBC Driver версии 4.2 или более поздней.

> Перед выпуском драйвера JDBC 6,2 необходимо явно задать **serverSpn**. Начиная с версии 6,2, драйвер по умолчанию сможет создать **serverSpn** , хотя он также может использовать **serverSpn** явным образом.

## <a name="security-risks"></a>Угрозы безопасности

Протокол NTLM — это старый протокол проверки подлинности с различными уязвимостями, который представляет угрозу безопасности. Он основан на относительно слабой криптографической схеме и уязвим для различных атак. Он заменяется на Kerberos, что является гораздо более безопасным и рекомендуемым. Проверку подлинности NTLM следует использовать только в безопасной доверенной среде или в случае, если Kerberos не может использоваться.

Поддерживает [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] только протокол NTLM версии 2, который содержит некоторые улучшения безопасности по сравнению с исходным протоколом v1. Ит'сс также рекомендуется включить расширенную защиту или использовать шифрование SSL для повышения безопасности. 

Дополнительные сведения о включении расширенной защиты и см. в следующих статьях:

- [Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)

Дополнительные сведения о подключении с помощью SSL-шифрования см. в следующих статьях:

- [Подключение с помощью SSL-шифрования](../../connect/jdbc/connecting-with-ssl-encryption.md)

> [!NOTE]
> Для выпуска 7,4 Включение расширенной **защиты** и шифрование не поддерживается.

## <a name="see-also"></a>См. также раздел

[Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
