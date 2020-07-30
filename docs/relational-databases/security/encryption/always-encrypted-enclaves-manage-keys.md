---
title: Управление ключами для Always Encrypted с безопасными анклавами | Документация Майкрософт
ms.custom: ''
ms.date: 10/30/2019
ms.reviewer: vanto
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: security
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 02d919934b8e918bf142dbcf4af8278a54608dfc
ms.sourcegitcommit: 620a868e623134ad6ced6728ce9d03d7d0038fe0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/29/2020
ms.locfileid: "87411080"
---
# <a name="manage-keys-for-always-encrypted-with-secure-enclaves"></a>Управление ключами для Always Encrypted с безопасными анклавами
[!INCLUDE [sqlserver2019-windows-only](../../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Компонент [Always Encrypted с безопасными анклавами](always-encrypted-enclaves.md) расширяет возможности управления ключами для [Always Encrypted](always-encrypted-database-engine.md), представляя ключи с поддержкой анклава: 

- **Главный ключ столбца с поддержкой анклава** — главный ключ столбца, при создании которого в объекте метаданных главного ключа столбца в базе данных было указано свойство `ENCLAVE_COMPUTATIONS`. 
- **Ключ шифрования столбца с поддержкой анклава** — ключ шифрования столбца, зашифрованный с помощью главного ключа столбца с поддержкой анклава. Для вычислений в защищенном анклаве на стороне сервера можно использовать только ключи шифрования столбца с поддержкой анклава. 

Для управления ключами с поддержкой анклава применяются такие же общие рекомендации и процессы, что и для [управления ключами Always Encrypted](overview-of-key-management-for-always-encrypted.md). 

## <a name="managing-keys"></a>Управление ключами

В следующих статьях рассматриваются различные аспекты управления ключами с поддержкой анклава.

- [Подготовка ключей с поддержкой анклава](always-encrypted-enclaves-provision-keys.md)
- [Смена ключей с поддержкой анклава](always-encrypted-enclaves-rotate-keys.md)

## <a name="next-steps"></a>Next Steps
- [Подготовка ключей с поддержкой анклава](always-encrypted-enclaves-provision-keys.md)

## <a name="see-also"></a>См. также:  
- [Общие сведения об управлении ключами для Always Encrypted](overview-of-key-management-for-always-encrypted.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
