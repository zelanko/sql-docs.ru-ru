---
title: sys. dm_cluster_endpoints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.prod_service: database-engine, big-data-clusters
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_cluster_endpoints
- dm_cluster_endpoints_TSQL
- dm_cluster_endpoints
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cluster_endpoints dynamic management view
ms.assetid: ''
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 95f251db2efe471455d18f4735be99ecee962a7d
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85717510"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. dm_cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/applies-to-version/sqlserver2019.md)]

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|name|`sysname`|Имя службы, предоставляемой извне в кластере больших данных SQL. Уникальный идентификатор для конечной точки. Ключ для этого представления. Не допускает значение NULL. |  
|description|`nvarchar(4000)`|Описание службы. Не допускает значение NULL. |
|endpoint|`sysname`|URL-адрес конечной точки или атрибут соединения. Не допускает значение NULL. |
|protocol_desc|`sysname`|Описание протокола конечной точки |

## <a name="permissions"></a>Разрешения

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] необходимо `VIEW SERVER STATE` разрешение.

## <a name="see-also"></a>См. также

[Что [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)] ](../../big-data-cluster/big-data-cluster-overview.md)?
