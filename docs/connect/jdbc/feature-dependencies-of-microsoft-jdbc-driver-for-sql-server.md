---
title: "Функция зависимости драйвера Microsoft JDBC для SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 02/28/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 703a27220a80744c46ca0bc7667756cec1ab6596
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/02/2018
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Зависимости компонентов драйвера Microsoft JDBC для SQL Server
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

 Эта страница содержит список библиотек, от которых зависит Microsoft JDBC Driver for SQL Server. Проект включает следующие зависимости.
 
 ## <a name="compile-time"></a>Время компиляции
 - `azure-keyvault` : Azure поставщика хранилища ключей для функции всегда зашифрованы хранилище ключей Azure (необязательно)
 - `adal4j` : Библиотека azure ActiveDirectory для Java для проверки подлинности Azure Active Directory функции и хранилище ключей Azure (необязательно)

 ##  <a name="test-time"></a>Время выполнения теста
Конкретных проектов, для которых требуется одно из двух описанных функций, необходимо явно объявить соответствующих зависимостей в pom-файла:

***Например:*** при использовании *функция проверки подлинности Azure Active Directory*, вам нужно повторно объявить *adal4j* зависимостей в pom-файла проекта. См. в следующем фрагменте кода: 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>
```

***Например:*** при использовании *функция хранилища ключей Azure* вам нужно повторно объявить *azure keyvault* зависимостей и *adal4j* зависимостей в вашей pom-файла проекта. См. в следующем фрагменте кода: 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```
 
 ## <a name="dependency-requirements-for-the-jdbc-driver"></a>Требования к зависимостям для драйвера JDBC

 ### <a name="azure-keyvault-feature"></a>Функция Keyvault Azure:
- Драйвер JDBC версии 6.0.0 
    - Версии зависимостей: Azure-Keyvault (версия 0.9.7), Adal4j (версия 1.3.0) и их зависимостей ( [образец приложения](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))
- Драйвер JDBC версии 6.2.2 и выше (включая последнюю 6.4.0)
    - Версии зависимостей: Azure-Keyvault (версия 1.0.0), Adal4j (версия 1.4.0) и их зависимостей ([образец приложения](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))

> [!NOTE]
>   Начиная с v6.2.2 зависимостей azure keyvault-java обновляется до версии 1.0.0. Тем не менее новая версия несовместима с предыдущей версии (версия 0.9.7) и поэтому разрывы существующую реализацию в драйвере. Новая реализация в драйвере требует изменения API, которые в свою очередь прервать выполнение программы клиента, которые используют хранилище ключей Azure.

  
 ### <a name="azure-active-directory-authentication"></a>Проверка подлинности Azure Active Directory:
- Драйвер JDBC версии 6.0.0 
    - Версии зависимостей: Adal4j (версия 1.3.0) и его зависимостей
        - В этой версии драйвера можно подключиться при помощи *ActiveDirectoryIntegrated* режим проверки подлинности только в Windows, операционной системе и использовании sqljdbc_auth.dll и библиотеку аутентификации Active Directory (SQL Server ADALSQL. БИБЛИОТЕКА DLL). 
- Драйвер JDBC версии 6.4.0
    - Версии зависимостей: Adal4j (версия 1.4.0) и его зависимостей
        - В этой версии драйвера приложение не требует использования ADALSQL. БИБЛИОТЕКИ DLL. В зависимости от операционной системы. Для **операционные системы Windows не**, драйвер требует билет Kerberos для работы с проверкой подлинности ActiveDirectoryIntegrated. В разделе [билет Kerberos, задайте в Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) для получения дополнительных сведений. Для **операционных систем Windows**, драйвера по умолчанию проверяет sqljdbc_auth.dll загружается и не требует установки или adal4j зависимостей билета Kerberos. Однако если sqljdbc_auth.dll не загружен, драйвер ведет себя так же, как операционных систем, отличных от Windows и требует установки, как описано в следующем примере: пример приложения с помощью этой функции можно найти [здесь](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md) .

 ## <a name="see-also"></a>См. также  
 [Репозитории GitHub драйвера JDBC](https://github.com/microsoft/mssql-jdbc)  
 [Справочник по API для драйвера JDBC](../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  