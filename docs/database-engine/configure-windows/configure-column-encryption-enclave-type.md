---
title: Параметр конфигурации сервера "column encryption enclave type" | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: security
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
author: jaszymas
ms.author: jaszymas
manager: craigg
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 961cf4a634f134f3bd41858a8157db0e8f6cb45f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47782392"
---
# <a name="column-encryption-enclave-type-server-configuration-option"></a>Параметр конфигурации сервера "column encryption enclave type"
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

  Используйте параметр **column encryption enclave type**, чтобы включить или отключить безопасный анклав для Always Encrypted.  Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../../relational-databases/security/encryption/always-encrypted-enclaves.md).

 В следующей таблице перечислены возможные значения **column encryption enclave type**:  
  
|Значение|Описание|  
|-------------------|-----------------|  
|0|**Без безопасного анклава**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] не удается инициализировать безопасный анклав для Always Encrypted. Таким образом, функция Always Encrypted с безопасными анклавами недоступна.|  
|1|**Безопасность на базе виртуализации (VBS)**. [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет инициализировать безопасный анклав (безопасный анклав памяти VBS) для Always Encrypted.|    

> [!IMPORTANT]
> Изменения в параметре **column encryption enclave type** вступают в силу после перезапуска экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
   
## <a name="examples"></a>Примеры  
 Следующий пример включает безопасный анклав:  

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

## <a name="see-also"></a>См. также:  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
  
