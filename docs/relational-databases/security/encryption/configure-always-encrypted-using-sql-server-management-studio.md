---
title: Настройка постоянного шифрования с помощью SSMS
description: Сведения о задачах по настройке баз данных Always Encrypted и управлению ими с помощью SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 10/31/2019
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
ms.openlocfilehash: 7c033cf8200103fe6198661f7ed0e3e2a6c3966a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75557873"
---
# <a name="configure-always-encrypted-using-sql-server-management-studio"></a>Configure Always Encrypted using SQL Server Management Studio (Настройка постоянного шифрования с помощью среды SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В этой статье описываются задачи по использованию [среды SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md) для настройки постоянного шифрования и управления базами данных, использующих постоянное шифрование.

## <a name="security-considerations-when-using-ssms-to-configure-always-encrypted"></a>Вопросы безопасности при использовании SSMS для настройки Always Encrypted

Среда SSMS, используемая для настройки постоянного шифрования, обрабатывает как ключи постоянного шифрования, так и конфиденциальные данные, поэтому ключи и данные отображаются внутри процесса SSMS в виде обычного текста. Таким образом, среду SSMS следует запускать на защищенном компьютере. Если база данных размещена на сервере SQL Server, убедитесь, что среда SSMS запущена на компьютере, отличном от компьютера с экземпляром SQL Server. Поскольку основной задачей функции постоянного шифрования является обеспечение целостности зашифрованных конфиденциальных данных даже в случае нарушения безопасности системы базы данных, выполнение скрипта PowerShell, обрабатывающего ключи или конфиденциальные данные на сервере SQL Server, может снизить или вообще отменить эффект действия функции. Дополнительные рекомендации по безопасности см. в разделе [Security Considerations for Key Management](overview-of-key-management-for-always-encrypted.md#security-considerations-for-key-management)(Вопросы безопасности для управления ключами).

Среда SSMS не поддерживает разделение ролей между теми, кто управляет базами данных (администраторы баз данных), и теми, кто управляет криптографическими секретами и имеет доступ к данным с открытым текстом (администраторы безопасности и (или) администраторы приложений). Если в организации действует разделение ролей, для настройки постоянного шифрования следует использовать PowerShell. Дополнительные сведения см. в разделах [Overview of Key Management for Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md) (Общие сведения об управлении ключами для Always Encrypted) и [Configure Always Encrypted using PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)(Настройка Always Encrypted с помощью PowerShell). 

## <a name="always-encrypted-tasks-using-ssms"></a>Задачи Always Encrypted с использованием SSMS

- [Подготовка к работе ключей Always Encrypted с помощью SQL Server Management Studio](configure-always-encrypted-keys-using-ssms.md)
- [Ротация ключей Always Encrypted с помощью SQL Server Management Studio](rotate-always-encrypted-keys-using-ssms.md)
- [Настройка шифрования столбцов с помощью мастера Always Encrypted](always-encrypted-wizard.md)
- [Настройка шифрования столбцов с помощью Always Encrypted с пакетом приложения уровня данных](configure-always-encrypted-using-dacpac.md)
- [Выполнение запросов к столбцам с помощью Always Encrypted с использованием SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Экспорт и импорт баз данных с помощью Always Encrypted](always-encrypted-migrate-using-bacpac.md)
- [Резервное копирование и восстановление баз данных с помощью Always Encrypted](always-encrypted-migrate-using-backup-restore.md)
- [Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server](always-encrypted-migrate-using-import-export-wizard.md)

## <a name="see-also"></a>См. также:
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Общие сведения об управлении ключами для Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Настройка постоянного шифрования с помощью PowerShell](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)
