---
title: sp_enclave_send_keys (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/26/2019
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
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 6540cdd36cccba4f5a7ccb3beddf31ce00cd9107
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394146"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys    (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Отправляет все поддержкой анклава столбца ключей шифрования в базе данных анклава, используемые [всегда зашифрованы с помощью безопасного enclaves &#40;СУБД&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

## <a name="syntax"></a>Синтаксис  
  
```
sp_enclave_send_keys
[ ;]  
```

## <a name="arguments"></a>Аргументы

Эта хранимая процедура не имеет аргументов.

## <a name="return-value"></a>Возвращаемое значение

Эта хранимая процедура не возвращает никакого значения.
  
## <a name="result-sets"></a>Результирующие наборы

Эта хранимая процедура имеет не результирующих наборов.
  
## <a name="remarks"></a>Примечания

**sp_enclave_send_keys** отправляет ключей шифрования столбцов с поддержкой анклава анклава, если выполняются все следующие условия:

- Анклава включена в экземпляре SQL Server.
- **sp_enclave_send_keys** был вызван из приложения с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер клиента, поддерживая Always Encrypted с безопасной enclaves, с помощью подключения к базе данных с Always Encrypted и анклава вычислений включен.

## <a name="permissions"></a>Разрешения

 Требовать **VIEW ANY COLUMN ENCRYPTION KEY DEFINITION** и **VIEW ANY COLUMN MASTER KEY DEFINITION** разрешения в базе данных.  
  
## <a name="examples"></a>Примеры  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>См. также

 [Всегда зашифрованы с помощью безопасного enclaves &#40;компонент Database Engine&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Учебник. Создание и использование индексов для столбцов с поддержкой анклава, с помощью случайного шифрования](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Вызвать с помощью ключей шифрования столбцов кэшированных операций индексирования](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Индексы для столбцов с поддержкой Анклава, с помощью случайного шифрования](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Рекомендации по AlwaysOn и перенос базы данных](../security/encryption/always-encrypted-enclaves.md#considerations-for-alwayson-and-database-migration)
