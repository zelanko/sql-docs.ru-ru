---
title: Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 10/31/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.COLUMNMASTERKEY.PAGE.F1
- SQL13.SWB.COLUMNENCRYPTIONKEY.PAGE.F1
- SQL13.SWB.COLUMNMASTERKEY.ROTATION.F1
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c8e23b3f5f291d120a099cae7f3e3e057db8da95
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73595789"
---
# <a name="migrate-data-to-or-from-columns-using-always-encrypted-with-sql-server-import-and-export-wizard"></a>Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server 
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[Мастер импорта и экспорта SQL Server](../../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md) позволяет копировать данные из исходного расположения в целевое. В этом документе описывается использование мастера импорта и экспорта SQL Server, если исходным и (или) целевым расположением является база данных SQL Server, содержащая столбцы, защищенные с помощью [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).

## <a name="migration-scenarios"></a>Сценарии миграции
С помощью мастера импорта и экспорта SQL Server можно реализовать следующие сценарии для переноса данных в зашифрованные столбцы или из них.

### <a name="encrypt-plaintext-data-on-migration"></a>Шифрование данных в виде открытого текста при миграции
Если источник данных содержит данные в виде открытого текста, а назначением является база данных SQL Server с зашифрованными столбцами, воспользуйтесь мастером импорта и экспорта SQL Server, чтобы получить данные в виде открытого текста из источника, зашифровать их и скопировать зашифрованные данные (зашифрованный текст) в зашифрованные столбцы в целевой базе данных. В этом сценарии миграции источником данных может быть любое хранилище данных, которое поддерживает мастер импорта и экспорта SQL Server. Например, это может быть файл, база данных SQL Server или база данных в другой системе баз данных.

Чтобы мастер импорта и экспорта SQL Server мог шифровать данные, необходимо включить функцию Always Encrypted для подключения к целевой базе данных и получить доступ к ключам, защищающим данные в столбцах этой базы данных. Дополнительные сведения см. в разделах [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных](#enable-and-disable-always-encrypted-for-a-database-connection) и [Разрешения для шифрования или расшифровки данных во время миграции](#permissions-for-encrypting-or-decrypting-data-during-migration).

### <a name="decrypt-encrypted-data-on-migration"></a>Расшифровка зашифрованных данных при миграции
При переносе данных, хранящихся в зашифрованных столбцах базы данных SQL Server, настройте мастер импорта и экспорта SQL Server для расшифровки данных и копирования расшифрованных (в виде открытого текста) данных в место назначения. Этим местом может быть любое хранилище данных, поддерживаемое мастером импорта и экспорта SQL Server (например, файл, база данных SQL Server или база данных в другой системе баз данных).

Чтобы мастер импорта и экспорта SQL Server мог расшифровывать данные, необходимо включить функцию Always Encrypted для подключения к базе данных-источнику и получить доступ к ключам, защищающим данные в столбцах этой базы данных. Дополнительные сведения см. в разделах [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных](#enable-and-disable-always-encrypted-for-a-database-connection) и [Разрешения для шифрования или расшифровки данных во время миграции](#permissions-for-encrypting-or-decrypting-data-during-migration).

### <a name="re-encrypt-data-on-migration"></a>Повторное шифрование данных при миграции
При копировании данных из зашифрованных столбцов в базе данных-источнике в зашифрованные столбцы в той же или другой базе данных SQL Server настройте мастер импорта и экспорта SQL Server для расшифровки данных после их получения из источника и их повторного шифрования перед вставкой в зашифрованные столбцы в целевой базе данных. Этот метод следует использовать, если схема целевых столбцов (например, типы данных столбцов, типы шифрования и ключи шифрования столбцов) отличается от схемы исходных столбцов.

Чтобы мастер импорта и экспорта SQL Server мог шифровать и расшифровывать данные, необходимо включить функцию Always Encrypted для подключений к базе данных-источнику и целевой базе данных и получить доступ к ключам, защищающим данные в столбцах этих баз данных. Дополнительные сведения см. в разделах [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных](#enable-and-disable-always-encrypted-for-a-database-connection) и [Разрешения для шифрования или расшифровки данных во время миграции](#permissions-for-encrypting-or-decrypting-data-during-migration).

### <a name="keep-data-encrypted-during-migration"></a>Поддержка зашифрованных данных во время миграции
Если вы копируете данные из зашифрованных столбцов в базе-данных источнике SQL Server в зашифрованные столбцы в той же или другой базе данных SQL Server, и для целевых столбцов используется **точно такая же** схема (включая те же типы данных, типы шифрования и ключи шифрования столбцов), что и для исходных столбцов, настройте мастер импорта и экспорта SQL Server для получения зашифрованного текста из исходных столбцов и вставки зашифрованных данных (зашифрованного текста) в зашифрованный столбец в целевой базе данных SQL Server. 

В этом сценарии для подключения к базе-данных источнику или целевой базе данных SQL Server можно использовать любой поставщик данных, поддерживающий SQL Server. Если для подключения к целевой базе данных используется поставщик, который поддерживает Always Encrypted, необходимо отключить функцию Always Encrypted. Дополнительные сведения см. в разделе [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных](#enable-and-disable-always-encrypted-for-a-database-connection).

Кроме того, параметру `ALLOW_ENCRYPTED_VALUE_MODIFICATIONS` участника базы данных, используемого мастером импорта и экспорта SQL Server для подключения к целевой базе данных, должно быть задано значение `ON`. Этот параметр отключает проверки шифрованных метаданных на сервере в операциях массового копирования, что позволяет мастеру массово вставлять зашифрованные данные в целевую базу данных и при этом не расшифровывать их. Дополнительные сведения см. в статье [Массовая загрузка зашифрованных данных в столбцы, защищенные с помощью Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md).

## <a name="enable-and-disable-always-encrypted-for-a-database-connection"></a>Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных
Если в сценарии миграции требуется, чтобы мастер импорта и экспорта SQL Server мог шифровать и (или) расшифровывать данные, необходимо настроить подключение к базе данных-источнику SQL Server и (или) подключение к целевой базе данных SQL Server с помощью поставщика данных, поддерживающего Always Encrypted. Функцию Always Encrypted также необходимо включить для подключения к базе данных-источнику и (или) целевой базе данных.

Если мастер не должен шифровать или расшифровывать данные для этого подключения, можно использовать любой поставщик данных.

Следующие поставщики данных в мастере импорта и экспорта SQL Server поддерживают Always Encrypted.

- Поставщик данных .NET Framework для SQL Server
  - Убедитесь, что на компьютере, где работает мастер, установлена платформа .NET Framework 4.6.1 или более поздних версий.
  - Чтобы включить функцию Always Encrypted, применяемую для подключения, в окне свойств подключения задайте параметру `Column Encryption Setting` значение `Enabled`. Чтобы отключить функцию Always Encrypted, применяемую для подключения, задайте параметру `Column Encryption Setting` значение `Disabled`. Дополнительные сведения см. в статье [Подключение к SQL Server с помощью поставщика данных .NET Framework для SQL Server](../../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md#connect-to-sql-server-with-the-net-framework-data-provider-for-sql-server) и [Включение Always Encrypted для запросов приложений](develop-using-always-encrypted-with-net-framework-data-provider.md#enabling-always-encrypted-for-application-queries).
- Поставщик данных .NET Framework для ODBC
  - Установите драйвер Microsoft ODBC Driver 13.1 или более поздних версий.
    - Чтобы включить функцию Always Encrypted, применяемую для подключения, в окне свойств подключения задайте параметру `Column Encryption` значение `Enabled`. Чтобы отключить функцию Always Encrypted, применяемую для подключения, задайте параметру `Column Encryption` значение `Disabled`. Дополнительные сведения см. в статьях [Подключение к SQL Server с помощью драйвера ODBC для SQL Server](../../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md#connect-to-sql-server-with-the-odbc-driver-for-sql-server) и [Включение Always Encrypted в приложении ODBC](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#enabling-always-encrypted-in-an-odbc-application).

## <a name="permissions-for-encrypting-or-decrypting-data-during-migration"></a>Разрешения для шифрования и расшифровки данных во время миграции

Чтобы зашифровать или расшифровать данные, хранящиеся в базе данных-источнике или целевой базе данных SQL Server, требуются разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* в целевой базе данных.

Также требуется доступ к главным ключам столбцов, настроенным для столбцов, в которых хранятся предназначенные для шифрования или расшифровки данные.

- **Хранилище сертификатов — локальный компьютер** — требуется доступ на чтение к сертификату, который используется в качестве главного ключа столбца, либо необходимо быть администратором компьютера.
- **Azure Key Vault** — требуются разрешения _get_, _unwrapKey_ и _verify_ к хранилищу, содержащему главный ключ столбца.
- **Поставщик хранилища ключей (CNG)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа в зависимости от конфигурации хранилища и KSP.
- **Поставщик служб шифрования (CAPI)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа в зависимости от конфигурации хранилища и CSP.
Дополнительные сведения см. в разделе [Create and Store Column Master Keys (Always Encrypted)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(Создание и хранение главных ключей столбцов (постоянное шифрование)).

## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с использованием SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>См. также:
- [Постоянное шифрование](always-encrypted-database-engine.md)
- [Экспорт и импорт баз данных с помощью Always Encrypted](always-encrypted-migrate-using-bacpac.md)
- [Резервное копирование и восстановление баз данных с помощью Always Encrypted](always-encrypted-migrate-using-backup-restore.md)
- [Массовая загрузка зашифрованных данных в столбцы с помощью Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md)