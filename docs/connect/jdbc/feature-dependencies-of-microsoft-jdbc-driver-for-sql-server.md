---
title: Зависимости компонентов Microsoft JDBC Driver для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1b9d9fea0f211809fd65b65459d50daa7a85db88
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736955"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Зависимости компонентов Microsoft JDBC Driver для SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье перечислены библиотеки, от которых зависит Microsoft JDBC Driver для SQL Server. Проект включает следующие зависимости.

## <a name="compile-time"></a>Время компиляции

 - `com.microsoft.azure:azure-keyvault`. Azure Key Vault Provider для функции Always Encrypted Azure Key Vault (необязательно)
 - `com.microsoft.azure:azure-keyvault-webkey`. Azure Key Vault Provider для функции Always Encrypted Azure Key Vault (необязательно)
 - `com.microsoft.azure:adal4j`. Azure Active Directory библиотеки для Java для аутентификации Azure Active Directory и Azure Key Vault (необязательно)
 - `com.microsoft.rest:client-runtime`. Azure Active Directory библиотеки для Java для аутентификации Azure Active Directory и Azure Key Vault (необязательно)
- `org.osgi:org.osgi.core`. Библиотека ядра OSGi для поддержки OSGi Framework.
- `org.osgi:org.osgi.compendium`. Библиотека OSGi пособие для поддержки OSGi Framework.

## <a name="test-time"></a>Время выполнения теста

Определенных проектов, для которых требуется одно из вышеперечисленных функций необходимо явно объявить соответствующие зависимости в их в файл POM.

**Например:** при использовании функцией проверки подлинности Azure Active Directory, необходимо повторно объявить `adal4j` зависимость в файл POM для проекта. См. следующий фрагмент кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.0.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>
```

**Например:** при использовании функцией Azure Key Vault, необходимо повторно объявить `azure-keyvault` зависимостей и `adal4j` зависимость в файл POM для проекта. См. следующий фрагмент кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.0.jre11</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.3</version>
</dependency>

<dependency>
    <groupId>com.microsoft.rest</groupId>
    <artifactId>client-runtime</artifactId>
    <version>1.6.5</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.2.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault-webkey</artifactId>
    <version>1.2.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Требования к зависимостям для JDBC Driver

### <a name="working-with-the-azure-key-vault-provider"></a>Работа с поставщиком хранилища ключей Azure:

- Драйвер JDBC версии 7.2.0 - версиями зависимостей: Хранилище ключей Azure (версии 1.2.0), Azure-Keyvault-Webkey (версии 1.2.0), Adal4j (версия 1.6.3), клиент среды выполнения — для AutoRest (1.6.5) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample.md))
- Драйвер JDBC version 7.0.0 - версиями зависимостей: Azure-Keyvault (версии 1.0.0), Adal4j (версии 1.6.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample.md))
- Драйвер JDBC версии 6.4.0 - версиями зависимостей: Azure-Keyvault (версии 1.0.0), Adal4j (версии 1.4.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Драйвер JDBC версии 6.2.2 - версиями зависимостей: Azure-Keyvault (версии 1.0.0), Adal4j (версии 1.4.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Драйвер JDBC версии 6.0.0 - версиями зависимостей: Azure-Keyvault (версии 0.9.7), Adal4j (версия 1.3.0) и их зависимостей ( [пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> С драйвером версии 6.2.2 и 6.4.0 зависимости java для хранилища ключей azure была обновлена до версии 1.0.0. Тем не менее новая версия была несовместима с предыдущей версией (0.9.7) и разбивает существующую реализацию в драйвере. Новая реализация в драйвере необходимые изменения API, который в свою очередь разбивает клиентских программ, использующих поставщик хранилища ключей Azure.
>
> Эта проблема устранена с последней версией драйвера (7.0.0). Удален конструктор, который используется механизм обратного вызова проверки подлинности добавляется обратно в поставщик хранилища ключей Azure для обеспечения обратной совместимости.

### <a name="working-with-azure-active-directory-authentication"></a>Использование проверки подлинности Azure Active Directory:

- Драйвер JDBC версии 7.2.0 - версиями зависимостей: Adal4j (версия 1.6.3), клиент среды выполнения — для AutoRest (1.6.5) и их зависимости
- Драйвер JDBC version 7.0.0 - версиями зависимостей: Adal4j (версии 1.6.0) и его зависимостей
- Драйвер JDBC версии 6.4.0 - версиями зависимостей: Adal4j (версии 1.4.0) и его зависимостей
- Драйвер JDBC версии 6.2.2 - версиями зависимостей: Adal4j (версии 1.4.0) и его зависимостей
- Драйвер JDBC версии 6.0.0 - версиями зависимостей: Adal4j (версия 1.3.0) и его зависимости. В этой версии драйвера, вы можете подключиться с помощью _ActiveDirectoryIntegrated_ режим проверки подлинности только в операционной системе Windows и с помощью sqljdbc_auth.dll и библиотеку аутентификации Active Directory (SQL Server ADALSQL. БИБЛИОТЕКА DLL).

Драйвер версии 6.4.0 и далее приложения не обязательно выделять с помощью ADALSQL. Библиотека DLL в операционных системах Windows. Для *отличных от Windows ОС*, драйвер требует билет Kerberos для работы с проверкой подлинности ActiveDirectoryIntegrated. Дополнительные сведения о том, как подключиться к Active Directory с помощью Kerberos см. в разделе [билет Kerberos, задайте в Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Для *операционных систем Windows*, драйвер выполняет поиск sqljdbc_auth.dll по умолчанию и не требует установки билет Kerberos или зависимости библиотек Azure. Если sqljdbc_auth.dll недоступна, драйвер выполняет поиск билет Kerberos для проверки подлинности в Active Directory, как в других операционных системах.

Вы можете получить [пример приложения](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) , использующий эту функцию.

## <a name="see-also"></a>См. также раздел

[Репозиторий GitHub драйвера JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Справочник интерфейса драйвера JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
