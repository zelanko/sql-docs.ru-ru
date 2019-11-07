---
title: Экспорт и импорт баз данных с помощью Always Encrypted | Документация Майкрософт
ms.custom: ''
ms.date: 10/30/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1f2f44a6cf1172b779160d4ee17e584c7a7b2452
ms.sourcegitcommit: 312b961cfe3a540d8f304962909cd93d0a9c330b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2019
ms.locfileid: "73595809"
---
# <a name="export-and-import-databases-using-always-encrypted"></a>Экспорт и импорт баз данных с помощью Always Encrypted 
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В этой статье описывается экспорт и импорт баз данных, содержащих столбцы, защищенные с помощью [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md).

При экспорте базы данных все данные, хранящиеся в зашифрованных столбцах, извлекаются из базы данных в зашифрованном виде (как зашифрованный текст) и помещаются в итоговый файл [BACPAC](../../data-tier-applications/data-tier-applications.md) Итоговый BACPAC также содержит метаданные для ключей постоянного шифрования.

При импорте BACPAC в базу данных зашифрованные данные из BACPAC загружаются в базу данных и происходит повторное создание метаданных ключа постоянного шифрования. 

Если ваше приложение настроено для выполнения запросов к зашифрованным столбцам, хранящимся в базе данных-источнике (экспортированной), не требуется выполнять никаких особых действий, чтобы позволить приложению запрашивать зашифрованные данные в целевой базе данных, так как ключи в обеих базах данных идентичны.

Подробные сведения об экспорте и импорте базы данных см. в следующих статьях:
- [Экспорт приложения уровня данных](../../data-tier-applications/export-a-data-tier-application.md)
- [Импорт файла BACPAC для создания новой пользовательской базы данных](../../data-tier-applications/import-a-bacpac-file-to-create-a-new-user-database.md)
- [Экспорт базы данных SQL Azure в BACPAC-файл](https://docs.microsoft.com/azure/sql-database/sql-database-export)
- [Импорт BACPAC-файла в базу данных в Базе данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-import)
- [SqlPackage.exe](../../../tools/sqlpackage.md)

## <a name="permissions-for-migrating-databases-with-encrypted-columns"></a>Разрешения на перенос баз данных с зашифрованными столбцами

Требуются разрешения *ALTER ANY COLUMN MASTER KEY* и *ALTER ANY COLUMN ENCRYPTION KEY* для базы данных-источника. Требуются разрешения *ALTER ANY COLUMN MASTER KEY*, *ALTER ANY COLUMN ENCRYPTION KEY*, *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION DEFINITION* для целевой базы данных.

Доступ к главным ключам столбцов, настроенным для зашифрованных столбцов, не требуется, так как во время операций экспорта и импорта данные остаются зашифрованными.

## <a name="next-steps"></a>Next Steps
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>См. также:
- [Постоянное шифрование](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Резервное копирование и восстановление баз данных с помощью Always Encrypted ](always-encrypted-migrate-using-backup-restore.md)
- [Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server](always-encrypted-migrate-using-import-export-wizard.md)
- [Массовая загрузка зашифрованных данных в столбцы с помощью Always Encrypted](migrate-sensitive-data-protected-by-always-encrypted.md)