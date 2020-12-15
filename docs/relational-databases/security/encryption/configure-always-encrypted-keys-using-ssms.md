---
title: Подготовка к работе ключей Always Encrypted с помощью SQL Server Management Studio | Документация Майкрософт
description: Узнайте, как подготавливать главные ключи столбцов и ключи шифрования столбцов для работы функции Always Encrypted с помощью SQL Server Management Studio.
ms.custom: ''
ms.date: 10/01/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.COLUMNMASTERKEY.PAGE.F1
- SQL13.SWB.COLUMNENCRYPTIONKEY.PAGE.F1
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 35f08a014fd1abbc8af6db994ba4c2d9b85a0bd4
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97405719"
---
# <a name="provision-always-encrypted-keys-using-sql-server-management-studio"></a>Подготовка к работе ключей Always Encrypted с помощью SQL Server Management Studio
[!INCLUDE [SQL Server Azure SQL Database](../../../includes/applies-to-version/sql-asdb.md)]

В этой статье описаны действия по подготовке главных ключей столбцов и ключей шифрования столбцов для работы функции Always Encrypted с помощью [SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md).

Обзор управления ключами Always Encrypted, включая общие рекомендации и важные вопросы безопасности, см. в разделе [Общие сведения об управлении ключами Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).

<a name="provisioncmk"></a>
## <a name="provision-column-master-keys-with-the-new-column-master-key-dialog"></a>Подготовка главных ключей столбцов в диалоговом окне "Новый главный ключ столбца"

В диалоговом окне **Новый главный ключ столбца** можно создать главный ключ столбца или выбрать существующий ключ в хранилище ключей, а также создать метаданные главного ключа столбца для сгенерированного или выбранного ключа в базе данных.

1.  С помощью **обозревателя объектов** перейдите к папке **Безопасность > Ключи постоянного шифрования** в базе данных.
2.  Щелкните правой кнопкой мыши папку **Главные ключи столбцов** и выберите **Создать главный ключ столбца…** . 
3.  В диалоговом окне **Новый главный ключ столбца** введите имя объекта метаданных главного ключа столбца.
4.  Выберите хранилище ключей.
    - **Хранилище сертификатов — текущий пользователь** — указывает расположение хранилища сертификатов текущего пользователя в хранилище сертификатов Windows, которое является личным хранилищем. 
    - **Хранилище сертификатов — локальный компьютер** — указывает расположение хранилища сертификатов локального компьютера в хранилище сертификатов Windows. 
    - **Azure Key Vault** — потребуется войти в Azure (щелкните **Вход**). Выполнив вход, можно выбрать одну из подписок Azure и хранилище ключей.
    - **Поставщик хранилища ключей (KSP)**  — указывает хранилище ключей, которое доступно через поставщик хранилища ключей (KSP), реализующий API криптографии следующего поколения (CNG). Как правило, этот тип хранилища является аппаратным модулем безопасности (HSM). После выбора этого параметра необходимо выбрать поставщик KSP. По умолчанию выбран **поставщик хранилища ключей Microsoft Software Key Store Provider** . Чтобы использовать главный ключ столбца, хранящийся в HSM, выберите KSP для устройства (он должен быть установлен и настроен на компьютере до открытия диалогового окна).
    -   **Поставщик служб шифрования (CSP)**  — хранилище ключей, доступное через поставщик служб шифрования (CSP), который реализует Cryptography API (CAPI). Как правило, это хранилище является аппаратным модулем безопасности (HSM). После выбора этого параметра необходимо выбрать поставщик CSP.  Чтобы использовать главный ключ столбца, хранящийся в HSM, выберите CSP для устройства (он должен быть установлен и настроен на компьютере до открытия диалогового окна).
    
    > [!NOTE]
    > Так как CAPI — это устаревший API, параметр "Поставщик служб шифрования" отключен по умолчанию. Его можно включить, создав значение CAPI Provider Enabled DWORD в разделе **[HKEY_CURRENT_USER\Software\Microsoft\Microsoft SQL Server\sql13\Tools\Client\Always Encrypted]** реестра Windows и установив для него 1. Если хранилище ключей не поддерживает CNG, вместо CAPI следует использовать CNG.
   
    Дополнительные сведения о хранилищах ключей см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

5. Если вы используете [!INCLUDE [sssqlv15-md](../../../includes/sssqlv15-md.md)], и для экземпляра SQL Server настроен безопасный анклав, можно установить флажок **Разрешить вычисления анклава**, чтобы включить для главного ключа поддержку анклава. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md). 

    > [!NOTE]
    > Флажок **Разрешить вычисления анклава** не отображается, если в экземпляре SQL Server не выполнена правильная настройка безопасных анклавов.

6.  Выберите существующий ключ в хранилище ключей либо нажмите кнопку **Создать ключ** или **Создать сертификат** , чтобы создать ключ в хранилище ключей. 
7.  Нажмите кнопку **ОК** , и новый ключ появится в списке. 

После завершения работы с диалоговым окном среда SQL Server Management Studio создаст метаданные для главного ключа столбца в базе данных. Для выполнения этой задачи в диалоговом окне создается и запускается инструкция [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md) .

::: moniker range=">=sql-server-ver15"

При включении поддержки анклава для главного ключа столбца среда SSMS также подписывает метаданные с помощью главного ключа столбца. 

::: moniker-end

### <a name="permissions-for-provisioning-a-column-master-key"></a>Разрешения на подготовку главного ключа столбца

Для создания главного ключа столбца в диалоговом окне необходимо разрешение *ALTER ANY COLUMN MASTER KEY* в базе данных. Чтобы использовать диалоговое окно для создания нового главного ключа столбца или использования существующего из хранилища ключей, могут потребоваться разрешения на хранилище ключей или (и) ключа:
- **Хранилище сертификатов — локальный компьютер** — требуется доступ на чтение к сертификату, который используется в качестве главного ключа столбца, либо необходимо быть администратором компьютера.
- **Azure Key Vault** — для выбора и использования ключа требуются разрешения *получение* и *список*, для создания нового ключа — *создание*. Чтобы настроить поддержку анклава для главного ключа столбца, вам также потребуется разрешение *подпись* для создания сигнатуры метаданных ключа.
- **Поставщик хранилища ключей (CNG)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и KSP.
- **Поставщик служб шифрования (CAPI)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и CSP.

Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

<a name="provisioncek"></a> 
## <a name="provision-column-encryption-keys-with-the-new-column-encryption-key-dialog"></a>Подготовка ключей шифрования столбцов в диалоговом окне "Новый ключ шифрования столбца"

В диалоговом окне **Ключ шифрования нового столбца** можно создать ключ шифрования столбца, зашифровать его с помощью главного ключа столбца, а также создать метаданные ключа шифрования столбца в базе данных.

1.  С помощью **обозревателя объектов** перейдите к папке **Безопасность &gt; Ключи постоянного шифрования** в базе данных.
2.  Щелкните правой кнопкой мыши папку **Ключи шифрования столбцов** и выберите **Создать ключ шифрования столбца...** 
3.  В диалоговом окне **Новый ключ шифрования столбца** введите имя объекта метаданных ключа шифрования столбца.
4.  Выберите объект метаданных, который представляет ваш главный ключ столбца в базе данных.
5.  Нажмите кнопку **ОК**. 

После завершения работы с диалоговым окном среда SQL Server Management Studio создаст ключ шифрования столбца, а затем извлечет метаданные для главного ключа столбца, выбранного в базе данных. После этого среда SSMS с помощью метаданных главного ключа столбца получит доступ в хранилище ключей, содержащее ваш главный ключ столбца, и зашифрует ключ шифрования столбца. Наконец, среда SSMS создаст данные метаданных для нового шифрования столбца в базе данных, сформировав и выполнив инструкцию [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md).

### <a name="permissions-for-provisioning-a-column-encryption-key"></a>Разрешения на подготовку ключа шифрования столбца

Для создания метаданных ключа шифрования столбца и для доступа к метаданным главного ключа столбца необходимы разрешения *ALTER ANY COLUMN ENCRYPTION KEY* и *VIEW ANY COLUMN MASTER KEY DEFINITION* для базы данных.
Чтобы получить доступ к хранилищу ключей и использовать главный ключ столбца, вам могут потребоваться указанные далее разрешения для хранилища ключей и (или) ключа.
- **Хранилище сертификатов — локальный компьютер** — требуется доступ на чтение к сертификату, который используется в качестве главного ключа столбца, либо необходимо быть администратором компьютера.
- **Хранилище ключей Azure** — требуются разрешения *get*, *unwrapKey*, *wrapKey*, *sign* и *verify* к хранилищу, содержащему главный ключ столбца.
- **Поставщик хранилища ключей (CNG)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и KSP.
- **Поставщик служб шифрования (CAPI)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и CSP.

Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

## <a name="provision-always-encrypted-keys-using-the-always-encrypted-wizard"></a>Подготовка ключей Always Encrypted с помощью мастера Always Encrypted

Мастер [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-wizard.md) — это средство для шифрования, расшифровки и повторного шифрования выбранных столбцов базы данных. Хотя он может использовать и уже настроенные ключи, он также позволяет создать новый главный ключ столбца и новое шифрование столбца. 

## <a name="next-steps"></a>Next Steps
- [Настройка шифрования столбцов с помощью мастера Always Encrypted](always-encrypted-wizard.md)
- [Настройка шифрования столбцов с помощью Always Encrypted с пакетом приложения уровня данных](configure-always-encrypted-using-dacpac.md)
- [Ротация ключей Always Encrypted с помощью SQL Server Management Studio](rotate-always-encrypted-keys-using-ssms.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)
- [Перенос данных в столбцы или из них с помощью Always Encrypted с использованием мастера импорта и экспорта SQL Server](always-encrypted-migrate-using-import-export-wizard.md)

## <a name="see-also"></a>См. также:
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Общие сведения об управлении ключами для Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)
- [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)
- [Настройка функции Always Encrypted с помощью SQL Server Management Studio](configure-always-encrypted-using-sql-server-management-studio.md)
- [Подготовка ключей Always Encrypted с помощью PowerShell](configure-always-encrypted-keys-using-powershell.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
- [DROP COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/drop-column-master-key-transact-sql.md)
- [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md)
- [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md)
- [DROP COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/drop-column-encryption-key-transact-sql.md) 
- [sys.column_master_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
- [sys.column_encryption_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)
