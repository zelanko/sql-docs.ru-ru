---
title: Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/10/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b4f794e66e881ddeb36c724fc583d95a42bce33d
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411460"
---
# <a name="configure-column-encryption-in-place-using-always-encrypted-with-secure-enclaves"></a>Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами 
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

[Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) поддерживает криптографические операции над столбцами базы данных на месте — внутри безопасного анклава в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Шифрование на месте устраняет необходимость перемещения данных для таких операций за пределы базы данных, что делает криптографические операции более быстрыми и надежными. 

> [!NOTE]
> Несмотря на преимущества шифрования на месте в плане производительности, криптографические операции в больших таблицах могут занимать много времени и потреблять значительные ресурсы и потенциально влиять на производительность и доступность приложений.

Шифрование на месте позволяет также активировать операции шифрования с помощью инструкции [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md), что невозможно без анклава.

## <a name="prerequisites"></a>предварительные требования
Ниже приведены поддерживаемые криптографические операции и требования для ключей шифрования столбцов, используемых для этих операций.
- Шифрование столбца с открытым текстом. Ключ шифрования столбца, используемый для шифрования столбца, должен поддерживать анклав.
- Повторное шифрование зашифрованного столбца с помощью нового типа шифрования или (и) нового ключа шифрования столбца. Ключ шифрования текущего столбца и новый ключ шифрования столбца (если он отличается от текущего) оба должны поддерживать анклав.
- Расшифровка зашифрованного столбца. Ключ шифрования столбца, защищающий столбец, должен поддерживать анклав.

Сведения о том, как проверить, что ключи шифрования столбцов поддерживают анклав, см. в разделе [Управление ключами для Always Encrypted с безопасными анклавами](always-encrypted-enclaves-manage-keys.md).

Для шифрования на месте также требуется экземпляр SQL Server с правильно инициализированным безопасным анклавом. См. [Настройка типа анклава для параметра конфигурации сервера Always Encrypted](../../../database-engine/configure-windows/configure-column-encryption-enclave-type.md).

Пользователь или приложение, запускающее криптографические операции, должны иметь разрешения на внесение изменений схемы в таблицу, содержащую затрагиваемые столбцы, и на доступ к главным ключам столбцов, используемым в операции, и к соответствующим метаданным ключа в базе данных.

Шифрование на месте можно активировать только с помощью инструкции [ALTER TABLE ALTER COLUMN (Transact-SQL)](../../../t-sql/statements/alter-table-transact-sql.md) из среды SQL Server Management Studio или другого пользовательского приложения. См. [Настройка шифрования столбцов на месте с помощью Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md).

> [!NOTE]
> В настоящее время мастер [Always Encrypted](always-encrypted-wizard.md) и командлет [Set-SqlColumnEncryption](https://docs.microsoft.com/powershell/module/sqlserver/set-sqlcolumnencryption) не поддерживают шифрование на месте и всегда загружают данные для криптографических операций, даже если ваша конфигурация соответствует приведенным выше требованиям. 

## <a name="next-steps"></a>Next Steps
- [Настройка шифрования столбцов на месте с помощью Transact-SQL](always-encrypted-enclaves-configure-encryption-tsql.md)
- [Создание и использование индексов в столбце с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-create-use-indexes.md)
- [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md)
