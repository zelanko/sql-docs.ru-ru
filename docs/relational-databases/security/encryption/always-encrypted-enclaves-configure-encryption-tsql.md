---
title: Настройка шифрования столбцов на месте с помощью Transact-SQL | Документация Майкрософт
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
ms.openlocfilehash: b7e8118dc6404bf0f23422e030737403857367d8
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "73595569"
---
# <a name="configure-column-encryption-in-place-with-transact-sql"></a>Настройка шифрования столбцов на месте с помощью Transact-SQL
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

В этой статье описывается использование Always Encrypted с безопасными анклавами для выполнения криптографических операций на месте в столбцах с помощью инструкции [ALTER TABLE](../../../odbc/microsoft/alter-table-statement.md)/`ALTER COLUMN`. Основные сведения о шифровании на месте и общие предварительные требованиях см. в статье [Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-configure-encryption.md).

С помощью инструкции `ALTER TABLE` или `ALTER COLUMN` можно задать целевую конфигурацию шифрования для столбца. При выполнении инструкции безопасный анклав на стороне сервера зашифрует, повторно зашифрует или расшифрует хранящиеся в столбце данные в зависимости от текущей и целевой конфигурации шифрования, указанной в определении столбца в инструкции. 
- Если столбец в настоящий момент не зашифрован, он будет зашифрован, если в определении столбца указано предложение `ENCRYPTED WITH`.
- Если столбец зашифрован, он будет расшифрован (преобразован в столбец с открытым текстом), если в определении столбца не указано предложение `ENCRYPTED WITH`.
- Если столбец зашифрован, он будет повторно зашифрован, если указано предложение `ENCRYPTED WITH`, а указанный тип шифрования столбца или ключ шифрования столбца отличаются от используемого в настоящий момент типа шифрования или ключа шифрования столбца. 

> [!NOTE]
> Криптографические операции нельзя сочетать с другими изменениями в одной инструкции `ALTER TABLE`/`ALTER COLUMN`. Исключением является изменение столбца на `NULL` или `NOT NULL` либо изменение параметров сортировки. Например, вы не можете зашифровать столбец и изменить тип данных столбца в одной инструкции Transact-SQL `ALTER TABLE`/`ALTER COLUMN`. Используйте для этого две отдельных инструкции.

Как и любой запрос, использующий защищенный анклава на стороне сервера, инструкция `ALTER TABLE`/`ALTER COLUMN`, которая инициирует шифрование на месте, должна отправляться через подключение с включенной функцией Always Encrypted и вычислениями анклава. 

В оставшейся части этой статьи описывается запуск шифрования на месте с помощью инструкции `ALTER TABLE`/`ALTER COLUMN` из SQL Server Management Studio. Кроме того, можно выполнить `ALTER TABLE`/`ALTER COLUMN` из приложения. 

> [!NOTE]
> В настоящее время средства, отличные от SSMS, включая командлет [Invoke-Sqlcmd](https://docs.microsoft.com/powershell/module/sqlserver/invoke-sqlcmd) в модуле SqlServer PowerShell и [sqlcmd](../../../tools/sqlcmd-utility.md), не поддерживают использование `ALTER TABLE`/`ALTER COLUMN` для криптографических операций на месте.

## <a name="perform-in-place-encryption-with-transact-sql-in-ssms"></a>Выполнение шифрования на месте с помощью Transact-SQL в среде SSMS
### <a name="pre-requisites"></a>Предварительные требования
- Предварительные требования см. в статье [Настройка шифрования столбцов на месте с помощью Always Encrypted с защищенными анклавами](always-encrypted-enclaves-configure-encryption.md).
- SQL Server Management Studio 18.3 или более поздние версии.

### <a name="steps"></a>Шаги
1. Откройте окно запроса с поддержкой вычислений в анклаве и Always Encrypted для подключения к базе данных. Дополнительные сведения см. в разделе [Включение и отключение функции Always Encrypted, применяемой для подключения к базе данных ](always-encrypted-query-columns-ssms.md#en-dis).
2. В окне запроса выполните инструкцию `ALTER TABLE`/`ALTER COLUMN`, указав в предложении `ENCRYPTED WITH` ключ шифрования столбца с поддержкой анклава. Если столбец является строковым столбцом (например, `char`, `varchar`, `nchar`, `nvarchar`), также может потребоваться изменить тип сортировки на BIN2. 
    
    > [!NOTE]
    > Если главный ключ столбца хранится в Azure Key Vault, вам может быть предложено выполнить вход в Azure.

3. Очистите кэш планов от всех пакетов и хранимых процедур, которые обращаются к таблице, чтобы обновить сведения о параметрах шифрования. 
 
    ```sql
    ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
    ```
    > [!NOTE]
    > Если вы не удалите план затронутого запроса из кэша, первое выполнение запроса после шифрования может завершиться сбоем.

    > [!NOTE]
    > Внимательно используйте `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE` или `DBCC FREEPROCCACHE` для очистки кэша планов, так как эта операция может привести к временному ухудшению производительности запросов. Чтобы свести к минимуму негативное влияние очистки кэша, вы можете выборочно удалять планы только для затронутых запросов.

4.  Вызовите [sp_refresh_parameter_encryption](../../system-stored-procedures/sp-refresh-parameter-encryption-transact-sql.md), чтобы обновить метаданные параметров каждого модуля (хранимая процедура, функция, представление, триггер), которые сохранены в [sys.parameters](../..//system-catalog-views/sys-parameters-transact-sql.md) и могут быть аннулированы в результате шифрования столбцов.

### <a name="examples"></a>Примеры
#### <a name="encrypting-a-column-in-place"></a>Шифрование столбца на месте
В приведенном ниже примере предполагается:
- `CEK1` — это ключ шифрования столбцов с поддержкой анклава.
- Столбец `SSN` содержит открытый текст и в настоящее время использует сортировку базы данных по умолчанию Latin1, и параметры сортировки, отличные от BIN2 (например, `Latin1_General_CI_AI_KS_WS`).

Инструкция шифрует столбец `SSN`, используя случайное шифрование и ключ шифрования столбцов с поддержкой анклава на месте. Она также перезаписывает сортировку базы данных по умолчанию соответствующими (в той же кодовой странице) параметрами сортировки BIN2.

Операция выполняется в сети (`ONLINE = ON`). Также обратите внимание на вызов `ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE`, который восстанавливает планы запросов, затронутые изменением схемы таблицы.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char] COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1], ENCRYPTION_TYPE = Randomized, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL
WITH
(ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

#### <a name="re-encrypt-a-column-in-place-to-change-encryption-type"></a>Повторное шифрование столбца на месте для изменения типа шифрования
В приведенном ниже примере предполагается:
- `SSN` столбец зашифрован с помощью детерминированного шифрования и ключа шифрования столбца с поддержкой анклава `CEK1`.
- Текущие параметры сортировки, установленные на уровне столбца, имеют тип `Latin1_General_BIN2`.

Приведенная ниже инструкция повторно шифрует столбец с помощью случайного шифрования и того же ключа (`CEK1`).

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK1]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

#### <a name="re-encrypt-a-column-in-place-to-rotate-a-column-encryption-key"></a>Повторное шифрование столбца на месте для смены ключа шифрования столбца
В приведенном ниже примере предполагается:
- `SSN` столбец зашифрован с помощью случайного шифрования и ключа шифрования столбца с поддержкой анклава `CEK1`.
- `CEK2` — это ключ шифрования столбца с поддержкой анклава (отличный от `CEK1`).
- Текущие параметры сортировки, установленные на уровне столбца, имеют тип `Latin1_General_BIN2`.

Приведенная ниже инструкция повторно шифрует столбец с помощью `CEK2`.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
ENCRYPTED WITH (COLUMN_ENCRYPTION_KEY = [CEK2]
, ENCRYPTION_TYPE = Randomized
, ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256') NOT NULL;
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```
#### <a name="decrypt-a-column-in-place"></a>Расшифровка столбца на месте
В приведенном ниже примере предполагается:
- `SSN` столбец зашифрован с помощью ключа шифрования столбца с поддержкой анклава.
- Текущие параметры сортировки, установленные на уровне столбца, имеют тип `Latin1_General_BIN2`.

Приведенная ниже инструкция расшифровывает столбец (и сохраняет неизмененные параметры сортировки). Кроме того, в той же инструкции можно изменить параметры сортировки, например на параметры сортировки, отличные от BIN2.

```sql
ALTER TABLE [dbo].[Employees]
ALTER COLUMN [SSN] [char](11) COLLATE Latin1_General_BIN2
WITH (ONLINE = ON);
GO
ALTER DATABASE SCOPED CONFIGURATION CLEAR PROCEDURE_CACHE;
GO
```

## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-query-columns.md)
- [Создание и использование индексов в столбцах с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-create-use-indexes.md)
- [Разработка приложений с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-client-development.md)

## <a name="see-also"></a>См. также:  
- [Настройка шифрования столбцов на месте с помощью Always Encrypted с безопасными анклавами](always-encrypted-enclaves-configure-encryption.md)
- [Включение Always Encrypted с безопасными анклавами для существующих зашифрованных столбцов](always-encrypted-enclaves-enable-for-encrypted-columns.md)
- [Руководство. Начало работы с Always Encrypted с безопасными анклавами с использованием SSMS](../tutorial-getting-started-with-always-encrypted-enclaves.md)