---
title: sys.remote_service_bindings (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 807cba5d209b52fb78d64f6e25d17591e9152415
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Это представление каталога содержит по одной строке для каждой привязки удаленной службы. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя этой привязки удаленной службы. Не допускает значения NULL.|  
|**remote_service_binding_id**|**int**|Идентификатор этой привязки удаленной службы. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор участника базы данных, которому принадлежит эта привязка удаленной службы. Допускает значение NULL.|  
|**remote_service_name**|**nvarchar(256)**|Имя удаленной службы, к которой применяется эта привязка. Допускает значение NULL.|  
|**service_contract_id**|**int**|Идентификатор контракта, к которому применяется эта привязка. Значение, равное 0, является групповым символом, означающим, что эта привязка применяется ко всем контрактам для службы. Не допускает значения NULL.|  
|**remote_principal_id**|**int**|Идентификатор пользователя, указанного в привязке удаленной службы. Компонент Service Broker использует сертификат, принадлежащий этому пользователю, для обмена информацией с указанной службой по указанным контрактам. Допускает значение NULL.|  
|**is_anonymous_on**|**бит**|Эта привязка удаленной службы использует безопасность ANONYMOUS. Сведения о личности пользователя, который начинает диалог, не предоставляются целевой службе. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
