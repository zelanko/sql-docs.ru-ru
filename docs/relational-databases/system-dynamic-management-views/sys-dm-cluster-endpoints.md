---
title: sys. DM _cluster_endpoints (Transact-SQL) | Документация Майкрософт
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
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 05076a6b694ff5861c5a7862b1f8f913ddb67fd6
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73536173"
---
# <a name="sysdm_cluster_endpoints-transact-sql"></a>sys. DM _cluster_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|имя|`sysname`|Имя службы, предоставляемой извне в кластере больших данных SQL. Уникальный идентификатор для конечной точки. Ключ для этого представления. Не допускает значение NULL. |  
|description|`nvarchar(4000)`|Описание службы. Не допускает значение NULL. |
|конечная точка|`sysname`|URL-адрес конечной точки или атрибут соединения. Не допускает значение NULL. |
|protocol_desc|`sysname`|Описание протокола конечной точки |

## <a name="permissions"></a>Разрешения

Для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также раздел

Что такое [!INCLUDE[big-data-clusters-2019](../../includes/ssbigdataclusters-ss-nover.md)](.. /.. /Биг-Дата-клустер/Биг-Дата-клустер-овервиев.МД)?
