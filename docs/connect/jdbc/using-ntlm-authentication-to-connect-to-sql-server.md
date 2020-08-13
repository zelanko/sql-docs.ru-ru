---
title: Использование проверки подлинности NTLM для подключения к SQL Server
description: Узнайте, как установить подключение к базе данных SQL с помощью проверки подлинности NTLM посредством драйвера JDBC.
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
ms.openlocfilehash: 93b4956b70e6e81e215da4fcde61a3a3287b50ec
ms.sourcegitcommit: cb620c77fe6bdefb975968837706750c31048d46
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86393152"
---
# <a name="using-ntlm-authentication-to-connect-to-sql-server"></a>Использование проверки подлинности NTLM для подключения к SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] позволяет приложению использовать свойство подключения ** authenticationScheme**, чтобы указать, что подключение к базе данных должно устанавливаться с использованием проверки подлинности NTLM v2. 

Для проверки подлинности NTLM также используются следующие свойства:

- **domain = domainName** (необязательно).
- **user = userName**.
- **пароль = password**
- **integratedSecurity = true**.

Все свойства, кроме **domain**, являются обязательными. Драйвер выдаст ошибку, если они отсутствуют, когда используется свойство authenticationScheme **NTLM**. 

Дополнительные сведения о настройке свойств подключения см. [здесь](../../connect/jdbc/setting-the-connection-properties.md). Дополнительные сведения о протоколе проверки подлинности Microsoft NTLM см. [здесь](https://docs.microsoft.com/windows/desktop/SecAuthN/microsoft-ntlm).

## <a name="remarks"></a>Remarks

В статье [Безопасность сети: уровень проверки подлинности LAN Manager](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-security-lan-manager-authentication-level) приведено описание параметров сервера SQL Server, которые управляют поведением проверки подлинности NTLM. 

## <a name="logging"></a>Logging

Для поддержки аутентификации NTLM добавлено новое средство ведения журнала — com.microsoft.sqlserver.jdbc.internals.NTLMAuthentication. Дополнительные сведения см. в статье [Трассировка операций драйвера](../../connect/jdbc/tracing-driver-operation.md).

## <a name="datasource"></a>DataSource

При использовании источника данных для создания подключений свойства NTLM можно задать программно. Можно использовать **setAuthenticationScheme**, **setDomain** и (необязательно) **setServerSpn**.

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

Например, имя субъекта-службы может выглядеть так: "MSSQLSvc/some-server.zzz.corp.contoso.com:1433".

Дополнительные сведения об именах субъектов-служб (SPN) см. в разделах:

- [Поддержка имени субъекта-службы в клиентских соединениях](https://docs.microsoft.com/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections?view=sql-server-2017)

> [!NOTE]  
> Атрибут соединения serverSpn поддерживается только драйвером Microsoft JDBC Driver версии 4.2 или более поздней.

> До версии драйвера JDBC 6.2 между областями необходимо явно задать параметр **serverSpn**. Начиная с версии 6.2, драйвер по умолчанию сможет создать параметр **serverSpn**, хотя он также может использовать параметр **serverSpn** явно.

## <a name="security-risks"></a>Угрозы безопасности

Протокол NTLM — это устаревший протокол проверки подлинности с различными уязвимостями, который представляет угрозу безопасности. Он основан на относительно слабой криптографической схеме и подвержен различным атакам. Это протокол заменен на Kerberos, который является гораздо более безопасным и рекомендуемым. Проверку подлинности NTLM следует использовать только в безопасной доверенной среде или в случае, если Kerberos не может использоваться.

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает только протокол NTLM v2, который содержит некоторые улучшения безопасности по сравнению с исходным протоколом v1. Рекомендуется также включить расширенную защиту или использовать шифрование SSL для повышения безопасности. 

Дополнительные сведения о включении расширенной защиты см. в следующих статьях:

- [Соединение с компонентом Database Engine с использованием расширенной защиты](../../database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection.md)

Дополнительные сведения о подключении с шифрованием SSL см. в статье:

- [Подключение с помощью SSL-шифрования](../../connect/jdbc/connecting-with-ssl-encryption.md)

> [!NOTE]
> Для выпуска 7.4 одновременное включение расширенной защиты **и** шифрования не поддерживается.

## <a name="see-also"></a>См. также раздел

[Подключение к SQL Server с помощью JDBC Driver](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
