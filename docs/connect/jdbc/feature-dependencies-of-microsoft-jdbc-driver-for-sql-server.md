---
title: Зависимости компонентов Microsoft JDBC Driver для SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 57
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70179d55c6aae5fc01c84f0c4af860f86d528a06
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454228"
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Зависимости компонентов Microsoft JDBC Driver для SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

На этой странице перечислены работу библиотеки, от которых зависит Microsoft JDBC Driver для SQL Server. Проект включает следующие зависимости.

## <a name="compile-time"></a>Время компиляции

- `azure-keyvault`: Azure Key Vault Provider для функции Always Encrypted Azure Key Vault (необязательно)
- `adal4j`: Библиотека azure ActiveDirectory для Java для аутентификации Azure Active Directory и Azure Key Vault (необязательно)

## <a name="test-time"></a>Время выполнения теста

Определенных проектов, требующих либо из этих двух функций необходимо явно объявить соответствующие зависимости в их в файл pom:

**_Например:_**  при использовании _функция проверки подлинности Azure Active Directory_, то необходимо повторно объявить _adal4j_ зависимость в файл pom для проекта. См. следующий фрагмент кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>
```

**_Например:_**  при использовании _функция Azure Key Vault_, то необходимо повторно объявить _хранилище ключей azure_ зависимостей и _adal4j_ зависимость в файл pom для проекта. См. следующий фрагмент кода:

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>Требования к зависимостям для JDBC Driver

### <a name="working-with-azure-key-vault-provider"></a>Работа с поставщиком хранилища ключей Azure:

- Драйвер JDBC version 7.0.0 - версиями зависимостей: хранилище ключей Azure (версии 1.0.0), Adal4j (версии 1.6.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- Драйвер JDBC версии 6.4.0 - версиями зависимостей: хранилище ключей Azure (версии 1.0.0), Adal4j (версии 1.4.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Драйвер JDBC версии 6.2.2 - версиями зависимостей: хранилище ключей Azure (версии 1.0.0), Adal4j (версии 1.4.0) и их зависимостей ([пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- Драйвер JDBC версии 6.0.0 - версиями зависимостей: хранилище ключей Azure (версии 0.9.7), Adal4j (версия 1.3.0) и их зависимостей ( [пример приложения](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> С версиями драйвера v6.2.2 и версии 6.4.0 зависимости java для хранилища ключей azure была обновлена до версии 1.0.0. Тем не менее новая версия была несовместима с предыдущей версией (версии 0.9.7) и таким образом нарушает существующую реализацию в драйвере. Новая реализация в драйвере необходимые изменения API, который в свою очередь разбивает клиентских программ, использующих поставщик хранилища ключей Azure.

> Эта проблема была разрешена с последней v7.0.0 версии драйвера, удален конструктор, с помощью механизма проверки подлинности обратного вызова при добавлении обратно поставщик хранилища ключей Azure для обеспечения обратной совместимости.

### <a name="working-with-azure-active-directory-authentication"></a>Использование проверки подлинности Azure Active Directory:

- Драйвер JDBC version 7.0.0 - версиями зависимостей: Ada4j (версии 1.6.0) и его зависимостей
- Драйвер JDBC версии 6.4.0 - версиями зависимостей: Adal4j (версии 1.4.0) и его зависимостей
- Драйвер JDBC версии 6.2.2 - версиями зависимостей: Adal4j (версии 1.4.0) и его зависимостей
- Драйвер JDBC версии 6.0.0 - версиями зависимостей: Adal4j (версия 1.3.0), и его зависимости — в этой версии драйвера, можно подключиться с помощью _ActiveDirectoryIntegrated_ режим проверки подлинности только в операционной системе Windows и использование sqljdbc_auth.dll и библиотеку аутентификации Active Directory для SQL Server (ADALSQL. БИБЛИОТЕКА DLL).

Драйвер версии 6.4.0 и более поздних версий приложения не обязательно с помощью ADALSQL. Библиотека DLL в операционных системах Windows. Для **операционные системы Windows не**, драйвер требует билет Kerberos для работы с проверкой подлинности ActiveDirectoryIntegrated. Дополнительные сведения о том, как подключиться к Active Directory с помощью Kerberos см. в разделе [билет Kerberos, установить на Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac).

Для **операционных систем Windows**, драйвер выполняет поиск sqljdbc_auth.dll по умолчанию и не требует установки билет Kerberos или зависимости библиотек Azure. Тем не менее если sqljdbc_auth.dll недоступна, драйвер ищет билет Kerberos для проверки подлинности в Active Directory, как в других операционных системах.

Пример приложения с помощью этой функции можно найти [здесь](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md).

## <a name="see-also"></a>См. также:

[Репозиторий GitHub для драйвера JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Справка по API драйвера JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
