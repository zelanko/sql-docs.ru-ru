---
title: sys. dm_column_encryption_enclave (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/11/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: system-objects
ms.topic: language-reference
author: jaszymas
ms.author: jaszymas
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: f41a5f704a50924a882e220786ac8cafc090237a
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279580"
---
# <a name="sysdm_column_encryption_enclave-transact-sql"></a>sys.dm_column_encryption_enclave (Transact-SQL)
[!INCLUDE [sqlserver2019-windows-only](../../includes/applies-to-version/sqlserver2019-windows-only.md)]

Возвращает счетчики производительности для безопасного анклава для Always Encrypted. Дополнительные сведения см. в статье [Always Encrypted с безопасными анклавами](../security/encryption/always-encrypted-enclaves.md).

Если анклава настроен и правильно инициализирован после последнего перезапуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , представление содержит ровно одну строку. Если анклава не настроен или не был правильно инициализирован, представление не возвращает никаких строк. 

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|current_enclave_session_count|**int**|Текущее количество клиентских сеансов, использующих анклава.|  
|current_column_encryption_key_count|**int**|Число ключей шифрования столбцов, которые в настоящее время содержатся в анклава.|  
|current_memory_size_kb|**bigint**|Размер памяти анклава в КБ|  
|total_evicted_session_count|**bigint**|Общее число сеансов анклава, удаленных с момента последнего перезапуска сервера.|   
  
## <a name="permissions"></a>Разрешения  
Требуется разрешение `VIEW SERVER STATE`.   
  
## <a name="examples"></a>Примеры  
 
```sql  
SELECT * FROM sys.dm_column_encryption_enclave;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Настройка типа анклава для параметра конфигурации сервера Always Encrypted](../../database-engine/configure-windows/configure-column-encryption-enclave-type.md)
  
  
