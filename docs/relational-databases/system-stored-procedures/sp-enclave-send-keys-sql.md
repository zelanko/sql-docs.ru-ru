---
title: sp_enclave_send_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/19/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: vanto
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_enclave_send_keys
- sp_enclave_send_keys_TSQL
- sys.sp_enclave_send_keys
- sys.sp_enclave_send_keys_TSQL
helpviewer_keywords:
- sp_enclave_send_keys
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 57a7af110956bdf557ad751723f2497b6aa3ede0
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279568"
---
# <a name="sp_enclave_send_keys-transact-sql"></a>sp_enclave_send_keys (Transact-SQL)
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Отправляет ключи шифрования столбцов, определенные в базе данных, в защищенную анклава на стороне сервера, используемую с [Always encrypted с защищенным енклавес](../security/encryption/always-encrypted-enclaves.md).

`sp_enclave_send_keys`отправляются только те ключи, которые являются анклава и шифруют столбцы, использующие случайное шифрование и имеющие индексы. Для обычного пользовательского запроса драйвер клиента предоставляет анклава с ключами, необходимыми для вычислений в запросе. `sp_enclave_send_keys`отправляет все ключи шифрования столбцов, определенные в базе данных и используемые для индексов зашифрованных столбцов. 

`sp_enclave_send_keys`предоставляет простой способ отправки ключей в анклава и заполнения кэша ключей шифрования столбцов для последующих операций индексирования. Используйте `sp_enclave_send_keys` , чтобы включить:
- DBA для перестроения или изменения индексов или статистики по зашифрованным столбцам базы данных, если DBA не имеет доступа к главным ключам столбцов. См. раздел [вызов операций индексирования с использованием кэшированных ключей шифрования столбцов](../security/encryption/always-encrypted-enclaves-create-use-indexes.md#invoke-indexing-operations-using-cached-column-encryption-keys).
- [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)]для завершения восстановления индексов в зашифрованных столбцах. См. раздел [Восстановление базы данных](../security/encryption/always-encrypted-enclaves.md#database-recovery).
- Приложение, использующее .NET Framework поставщик данных для SQL Server для выполнения групповой загрузки данных в зашифрованные столбцы.

Для успешного вызова необходимо `sp_enclave_send_keys` подключиться к базе данных, используя Always encrypted и вычисления анклава, включенные для подключения к базе данных. Кроме того, необходимо иметь доступ к главным ключам столбцов, защищать ключи шифрования столбцов, отправку, а также разрешения на доступ к метаданным ключа Always Encrypted в базе данных. 

## <a name="syntax"></a>Синтаксис  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Аргументы

Эта хранимая процедура не имеет аргументов.

## <a name="return-value"></a>Возвращаемое значение

Эта хранимая процедура не имеет возвращаемого значения.
  
## <a name="result-sets"></a>Результирующие наборы

Эта хранимая процедура не имеет результирующих наборов.
  
## <a name="permissions"></a>Разрешения

 Требуются `VIEW ANY COLUMN ENCRYPTION KEY DEFINITION` разрешения и `VIEW ANY COLUMN MASTER KEY DEFINITION` в базе данных.  
  
## <a name="examples"></a>Примеры  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>См. также
- [Always Encrypted с безопасными анклавами](../security/encryption/always-encrypted-enclaves.md) 
 
- [Создание и использование индексов в столбцах с помощью Always Encrypted с безопасными анклавами](../security/encryption/always-encrypted-enclaves-create-use-indexes.md)

- [Учебник. Создание и использование индексов в столбцах с поддержкой анклава с использованием случайного шифрования](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md)
