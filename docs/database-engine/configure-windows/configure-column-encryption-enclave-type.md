---
title: Настройка типа анклава для параметра конфигурации сервера Always Encrypted | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 4786c512850d161d9b7ab33f2a12cd0bd077b2bd
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73593824"
---
# <a name="configure-the-enclave-type-for-always-encrypted-server-configuration-option"></a>Настройка типа анклава для параметра конфигурации сервера Always Encrypted
[!INCLUDE [tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx-winonly.md)]

В этой статье описывается, как включить или отключить безопасный анклав для Always Encrypted с безопасными анклавами. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

Параметр конфигурации сервера **тип анклава для шифрования столбцов** определяет тип безопасного анклава, используемого для Always Encrypted. Параметр может принимать одно из следующих значений:  
  
|Значение|Description|  
|-------------------|-----------------| 
|0|**Без безопасного анклава**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] не удается инициализировать безопасный анклав для Always Encrypted. Таким образом, функция Always Encrypted с безопасными анклавами недоступна.|  
|1|**Безопасность на базе виртуализации (VBS)** . [!INCLUDE[ssDE](../../includes/ssde-md.md)] попытается инициализировать анклав с безопасностью на базе виртуализации.

> [!IMPORTANT]
> Изменения в параметре **тип анклава для шифрования столбцов** вступают в силу после перезапуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
   
Вы можете проверить настроенное значение типа анклава и значение типа анклава, действующее в настоящее время, с помощью представления [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md). 

Чтобы убедиться, что действующее значение типа анклава (большее 0) было инициализировано должным образом после последнего перезапуска [!INCLUDE [ssnoversion-md](../../includes/ssnoversion-md.md)], откройте представление [sys.dm_column_encryption_enclave (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-column-encryption-enclave.md):
 - Если представление содержит ровно одну строку, анклав был инициализирован правильно. 
 - Если представление не содержит ни одной строки, проверьте журнал ошибок SQL Server на наличие ошибок инициализации анклава — см. раздел [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](../../relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).

Пошаговые инструкции по настройке анклава VBS см. в разделе [Настройка Always Encrypted с безопасными анклавами в SQL Server](../../relational-databases/security/tutorial-getting-started-with-always-encrypted-enclaves.md#step-3-enable-always-encrypted-with-secure-enclaves-in-sql-server).

## <a name="examples"></a>Примеры  
 В следующем примере включается безопасный анклав и устанавливается тип анклава VBS:

```sql  
sp_configure 'column encryption enclave type', 1;  
GO  
RECONFIGURE;  
GO  
```  

Следующий пример отключает безопасный анклав:  

```sql  
sp_configure 'column encryption enclave type', 0;  
GO  
RECONFIGURE;  
GO  
```  

Следующий запрос получает настроенный тип анклава и тип анклава, действующий в данный момент:

```sql  
USE [master];
GO
SELECT
[value]
, CASE [value] WHEN 0 THEN 'No enclave' WHEN 1 THEN 'VBS' ELSE 'Other' END AS [value_description]
, [value_in_use]
, CASE [value_in_use] WHEN 0 THEN 'No enclave' WHEN 1 THEN 'VBS' ELSE 'Other' END AS [value_in_use_description]
FROM sys.configurations
WHERE [name] = 'column encryption enclave type'; 
```  
## <a name="next-steps"></a>Next Steps
 [Управление ключами для Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves-manage-keys.md)

## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [sys.dm_column_encryption_enclave (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-column-encryption-enclave.md)   
