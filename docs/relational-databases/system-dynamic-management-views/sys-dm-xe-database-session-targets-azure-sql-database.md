---
title: sys.dm_xe_database_session_targets (база данных SQL Azure) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8978a41b22beb36ccc31d1cfdc0a73eaf2da34ec
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38041022"
---
# <a name="sysdmxedatabasesessiontargets-azure-sql-database"></a>sys.dm_xe_database_session_targets (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о целях сеанса.  
  
||  
|-|  
|**Применяется к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] версии 12 и всех будущих версий.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary(8)**|Адрес сеанса событий в памяти. Имеет отношение "многие к одному" с sys.dm_xe_database_sessions.address. Не допускает значение NULL.|  
|target_name|**nvarchar(60)**|Имя цели в сеансе. Не допускает значение NULL.|  
|target_package_guid|**uniqueidentifier**|Идентификатор GUID пакета, в котором содержится цель. Не допускает значение NULL.|  
|execution_count|**bigint**|Количество выполнений цели для сеанса. Не допускает значение NULL.|  
|execution_duration_ms|**bigint**|Общее время в миллисекундах, в течение которого выполнялась цель. Не допускает значение NULL.|  
|target_data|**nvarchar(max)**|Данные, предоставляемые целью, такие как сведения статистической обработки событий. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW DATABASE STATE.  
  
### <a name="relationship-cardinalities"></a>Количество элементов связей  
  
|От|Чтобы|Связь|  
|----------|--------|------------------|  
|sys.dm_xe_database_session_targets.event_session_address|sys.dm_xe_database_sessions.address|«многие к одному»|  
  
  
