---
title: Зависимости компонентов Microsoft JDBC Driver для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8316978e0122fe800dbd5af592b2ed57506873b6
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66781947"
---
# <a name="feature-dependencies-of-the-microsoft-jdbc-driver-for-sql-server"></a>Зависимости компонентов Microsoft JDBC Driver для SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье перечислены библиотеки, от которых зависит Microsoft JDBC Driver для SQL Server. Проект включает в себя следующие зависимости.

## <a name="compile-time"></a>Время компиляции

 - `com.microsoft.azure:azure-keyvault` : поставщик Azure Key Vault для функции Always Encrypted Azure Key Vault (необязательно).
 - `com.microsoft.azure:azure-keyvault-webkey` : поставщик Azure Key Vault для функции Always Encrypted Azure Key Vault (необязательно).
 - `com.microsoft.azure:adal4j` : библиотека Azure Active Directory для Java для функции проверки подлинности Azure Active Directory и функции Azure Key Vault (необязательно).
 - `com.microsoft.rest:client-runtime` : библиотека Azure Active Directory для Java для функции проверки подлинности Azure Active Directory и функции Azure Key Vault (необязательно).
- `org.osgi:org.osgi.core`: основная библиотека OSGi для поддержки платформы OSGi.
- `org.osgi:org.osgi.compendium`: библиотека-справочник OSGi для поддержки платформы OSGi.

## <a name="test-time"></a>Время тестирования

В конкретных проектах, для которых требуется какая-либо из предыдущих функций, необходимо явно объявить соответствующие зависимости в файле POM.

**Например:** при использовании функцией проверки подлинности Azure Active Directory, необходимо повторно объявить `adal4j` зависимость в файл POM для проекта. См. следующий фрагмент кода.

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
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

**Например:** при использовании функцией Azure Key Vault, необходимо повторно объявить `azure-keyvault` зависимостей и `adal4j` зависимость в файл POM для проекта. См. следующий фрагмент кода.

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.2.2.jre11</version>
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

### <a name="working-with-the-azure-key-vault-provider"></a>Использование поставщика Azure Key Vault

- JDBC Driver версии 7.2.2. Версии зависимостей: Azure-Keyvault (версия 1.2.0), Azure-Keyvault-Webkey (версия 1.2.0), Adal4j (версия 1.6.3), Client-Runtime-for-AutoRest (1.6.5) и их зависимости ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-7.0.md)).
- JDBC Driver версии 7.0.0. Версии зависимостей: Azure-Keyvault (версия 1.0.0), Adal4j (версия 1.6.0) и их зависимости ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-7.0.md)).
- JDBC Driver версии 6.4.0. Версии зависимостей: Azure-Keyvault (версия 1.0.0), Adal4j (версия 1.4.0) и их зависимости ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md)).
- JDBC Driver версии 6.2.2. Версии зависимостей: Azure-Keyvault (версия 1.0.0), Adal4j (версия 1.4.0) и их зависимости ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md)).
- JDBC Driver версии 6.0.0. Версии зависимостей: Azure-Keyvault (версия 0.9.7), Adal4j (версия 1.3.0) и их зависимости ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md)).

> [!NOTE]
> В версиях драйвера 6.2.2 и 6.4.0 зависимость azure-keyvault-java была обновлена ​​до версии 1.0.0. Однако новая версия была несовместима с предыдущей версией (0.9.7) и ломает существующую реализацию в драйвере. Новая реализация в драйвере требовала изменений API, что, в свою очередь, нарушало работу клиентских программ, использующих поставщик Azure Key Vault.
>
> Эта проблема решена с помощью последней версии драйвера (7.0.0). Удаленный конструктор, который использовал механизм обратного вызова для проверки подлинности, добавлен обратно в поставщик Azure Key Vault для обратной совместимости.

### <a name="working-with-azure-active-directory-authentication"></a>Использование проверки подлинности Azure Active Directory:

- JDBC Driver версии 7.2.2. Версии зависимостей: Adal4j (версия 1.6.3), Client-Runtime-for-AutoRest (1.6.5) и их зависимости.
- JDBC Driver версии 7.0.0. Версии зависимостей: Adal4j (версии 1.6.0) и его зависимости.
- JDBC Driver версии 6.4.0. Версии зависимостей: Adal4j (версии 1.4.0) и его зависимости.
- JDBC Driver версии 6.2.2. Версии зависимостей: Adal4j (версии 1.4.0) и его зависимости.
- JDBC Driver версии 6.0.0. Версии зависимостей: Adal4j (версии 1.3.0) и его зависимости. В этой версии драйвера вы можете подключиться с помощью режима проверки подлинности _ActiveDirectoryIntegrated_ только в операционной системе Windows с помощью sqljdbc_auth.dll и библиотеки проверки подлинности Active Directory для SQL Server (ADALSQL.DLL).

Начиная с версии драйвера 6.4.0, использование ADALSQL.DLL в операционной системе Windows для приложений не обязательно. Для *операционных систем, отличных от Windows*, для работы с проверкой подлинности ActiveDirectoryIntegrated драйверу требуется билет Kerberos. Дополнительные сведения о подключении к Active Directory с помощью Kerberos см. в разделе [Задать билет Kerberos в Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Для *операционной системы Windows* драйвер по умолчанию ищет файл sqljdbc_auth.dll и не требует установки билетов Kerberos или зависимостей библиотеки Azure. Если файл sqljdbc_auth.dll недоступен, драйвер ищет билет Kerberos для проверки подлинности в Active Directory, как и в других операционных системах.

Вы можете получить [образец приложения](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md), использующего эту функцию.

## <a name="see-also"></a>См. также раздел

[Репозиторий GitHub по JDBC Driver](https://github.com/microsoft/mssql-jdbc)  
[Справочник интерфейса драйвера JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
