---
title: sys. conversation_priorities (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- conversation_priorities_TSQL
- conversation_priorities
- sys.conversation_priorities_TSQL
- sys.conversation_priorities
dev_langs:
- TSQL
helpviewer_keywords:
- conversations [Service Broker], priorities
- Service Broker, conversations
- sys.conversation_priorities catalog view
ms.assetid: 7cbb9171-3310-4aae-8458-755c882d6462
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0c0d365978fa8c8c336040db50655e96234ecb22
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85887628"
---
# <a name="sysconversation_priorities-transact-sql"></a>sys.conversation_priorities (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Содержит по строке для каждого приоритета диалога, созданного в базе данных, которая имеет следующий вид: 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|Priority_id|**int**|Число, которое однозначно определяет приоритет диалога. Не допускает значения NULL.|  
|name|**sysname**|Имя приоритета диалога. Не допускает значения NULL.|  
|service_contract_id|**int**|Идентификатор контракта, указанного для приоритета диалога. Может быть соединен со столбцом service_contract_id в представлении sys.service_contracts. Допускает значение NULL.|  
|local_service_id|**int**|Идентификатор службы, которая указана в качестве локальной службы для приоритета диалога. Этот столбец может быть присоединен к столбцу service_id в представлении sys. Services. Допускает значение NULL.|  
|remote_service_name|**nvarchar(256)**|Имя службы, которая указана в качестве удаленной службы для приоритета диалога. Допускает значение NULL.|  
|priority|**tinyint**|Уровень приоритета, заданный для этого приоритета диалога. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере приоритеты диалогов перечисляются с помощью соединений, чтобы отобразить имена контрактов и локальных служб.  
  
```  
SELECT scp.name AS priority_name,  
       ssc.name AS contract_name,  
       ssvc.name AS local_service_name,  
       scp.remote_service_name,  
       scp.priority AS priority_level  
FROM sys.conversation_priorities AS scp  
    INNER JOIN sys.service_contracts AS ssc  
       ON scp.service_contract_id = ssc.service_contract_id  
    INNER JOIN sys.services AS ssvc  
       ON scp.local_service_id = ssvc.service_id  
ORDER BY priority_name, contract_name,  
         local_service_name, remote_service_name;  
  
```  
  
## <a name="see-also"></a>См. также  
 [ALTER BROKER PRIORITY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-broker-priority-transact-sql.md)   
 [CREATE BROKER PRIORITY (Transact-SQL)](../../t-sql/statements/create-broker-priority-transact-sql.md)   
 [DROP Service BROKER PRIORITY &#40;&#41;Transact-SQL](../../t-sql/statements/drop-broker-priority-transact-sql.md)   
 [sys. Services &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-services-transact-sql.md)   
 [sys. service_contracts &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-service-contracts-transact-sql.md)  
  
  
