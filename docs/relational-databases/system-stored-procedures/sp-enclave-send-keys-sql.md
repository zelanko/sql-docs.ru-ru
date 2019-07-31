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
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: b4ced2feee2227ba1db492f721f57907069c5d99
ms.sourcegitcommit: 97e94b76f9f48d161798afcf89a8c2ac0f09c584
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2019
ms.locfileid: "68661350"
---
# <a name="spenclavesendkeys----transact-sql"></a>sp_enclave_send_keys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Отправляет все ключи шифрования столбцов с поддержкой анклава в базе данных в анклава, используемый [Always encrypted с безопасными енклавес &#40;ядро СУБД&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

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
  
## <a name="remarks"></a>Примечания

**sp_enclave_send_keys** отправляет ключи шифрования столбца с включенным анклава в анклава, если выполняются все перечисленные ниже условия.

- Анклава включается в экземпляре SQL Server.
- **sp_enclave_send_keys** был вызван из приложения с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиентского драйвера, поддерживающего Always encrypted с безопасным енклавес с помощью подключения к базе данных, в котором включены вычисления Always encrypted и анклава.

## <a name="permissions"></a>Разрешения

 Запрашивать определение **ключа шифрования столбцов** и **просматривать любые разрешения для определения главного ключа столбца** в базе данных.  
  
## <a name="examples"></a>Примеры  
  
```sql
EXEC sp_enclave_send_keys;  
```

## <a name="see-also"></a>См. также

 [Always Encrypted с защищенным &#40;енклавес ядро СУБД&#41;](../../relational-databases/security/encryption/always-encrypted-enclaves.md)   
 [Учебник. Создание и использование индексов в столбцах с поддержкой анклава с использованием случайного шифрования](../security/tutorial-creating-using-indexes-on-enclave-enabled-columns-using-randomized-encryption.md#step-3-create-an-index-with-role-separation)   
 [Вызов операций индексации с использованием кэшированных ключей шифрования столбцов](../security/encryption/configure-always-encrypted-enclaves.md#invoke-indexing-operations-using-cached-column-encryption-keys)   
 [Индексы в столбцах с поддержкой анклава с использованием случайного шифрования](../security/encryption/always-encrypted-enclaves.md#indexes-on-enclave-enabled-columns-using-randomized-encryption)   
 [Рекомендации по миграции AlwaysOn и базы данных](../security/encryption/always-encrypted-enclaves.md#anchorname-1-considerations-availability-groups-db-migration)
