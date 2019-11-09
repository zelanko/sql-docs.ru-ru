---
title: sys. dm_xe_database_session_targets
titleSuffix: Azure SQL Database
ms.date: 06/10/2016
ms.service: sql-database
ms.prod_service: sql-database
ms.reviewer: ''
ms.topic: language-reference
ms.assetid: 7f353e2a-f8fc-4366-97e4-aa1c49eadaf4
author: MightyPen
ms.author: genemi
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.custom: seo-dt-2019
ms.openlocfilehash: 860faaa6c9e574feda8d5c28be17a265707fd72e
ms.sourcegitcommit: f688a37bb6deac2e5b7730344165bbe2c57f9b9c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/08/2019
ms.locfileid: "73844425"
---
# <a name="sysdm_xe_database_session_targets-azure-sql-database"></a>sys.dm_xe_database_session_targets (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Возвращает сведения о целях сеанса.  
  
||  
|-|  
|**Применимо к**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 и любые будущие версии.|  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|event_session_address|**varbinary (8)**|Адрес сеанса событий в памяти. Имеет связь «многие к одному» с sys. dm_xe_database_sessions. Address. Не допускает значение NULL.|  
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
|sys. dm_xe_database_session_targets. event_session_address|sys. dm_xe_database_sessions. Address|«многие к одному»|  
  
  
