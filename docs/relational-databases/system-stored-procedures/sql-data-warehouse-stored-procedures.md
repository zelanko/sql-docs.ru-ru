---
description: Хранимые процедуры Azure синапсе Analytics
title: Хранимые процедуры Azure синапсе Analytics
ms.custom: ''
ms.date: 03/15/2017
ms.service: sql-data-warehouse
ms.subservice: design
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 02e04dfe-d565-4e45-b427-b8e89c958ba3
author: ronortloff
ms.author: rortloff
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 080808c2f32990070ab630042a00e2173f0440a2
ms.sourcegitcommit: 76ab3b57718341c6057613c9bd38cf82fb17786e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92059542"
---
# <a name="azure-synapse-analytics-stored-procedures"></a>Хранимые процедуры Azure синапсе Analytics
[!INCLUDE [asa](../../includes/applies-to-version/asa.md)]

  [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] предоставляет встроенные процедуры, которые можно использовать для выполнения операций, связанных с ролями базы данных. [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] включает следующие системные процедуры:  
  
<a name="AggregateFunctions"></a>[sp_datatype_info_90 &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-datatype-info-90-sql-data-warehouse.md)  
  
 [sp_pdw_add_network_credentials &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)  
  
 [sp_pdw_database_encryption &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-sql-data-warehouse.md)  
  
 [sp_pdw_database_encryption_regenerate_system_keys &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-database-encryption-regenerate-system-keys-sql-data-warehouse.md)  
  
 [sp_pdw_log_user_data_masking &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-log-user-data-masking-sql-data-warehouse.md)  
  
 [sp_pdw_remove_network_credentials &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)  
  
 [sp_special_columns_100 &#40;Azure синапсе Analytics&#41;](../../relational-databases/system-stored-procedures/sp-special-columns-100-sql-data-warehouse.md)  
  
> [!NOTE]  
>  Некоторые дополнительные системные хранимые процедуры используются только в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или через клиентские API и не предназначены для общего использования клиентами. Эти процедуры перечислены в [системных хранимых процедурах (Transact-SQL)](./system-stored-procedures-transact-sql.md). Эти процедуры могут быть изменены, а совместимость не гарантируется. Все процедуры в списке недоступны в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые функции &#40;&#41;Transact-SQL ](~/relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
  
