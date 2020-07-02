---
title: sys. remote_service_bindings (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45e2050a08ce52ba915c0670a4da26a4517a1a3c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85787085"
---
# <a name="sysremote_service_bindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Это представление каталога содержит по одной строке для каждой привязки удаленной службы. 
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя этой привязки удаленной службы. Не допускает значения NULL.|  
|**remote_service_binding_id**|**int**|Идентификатор этой привязки удаленной службы. Не допускает значения NULL.|  
|**principal_id**|**int**|Идентификатор участника базы данных, которому принадлежит эта привязка удаленной службы. Допускает значение NULL.|  
|**remote_service_name**|**nvarchar(256)**|Имя удаленной службы, к которой применяется эта привязка. Допускает значение NULL.|  
|**service_contract_id**|**int**|Идентификатор контракта, к которому применяется эта привязка. Значение, равное 0, является групповым символом, означающим, что эта привязка применяется ко всем контрактам для службы. Не допускает значения NULL.|  
|**remote_principal_id**|**int**|Идентификатор пользователя, указанного в привязке удаленной службы. Компонент Service Broker использует сертификат, принадлежащий этому пользователю, для обмена информацией с указанной службой по указанным контрактам. Допускает значение NULL.|  
|**is_anonymous_on**|**bit**|Эта привязка удаленной службы использует безопасность ANONYMOUS. Сведения о личности пользователя, который начинает диалог, не предоставляются целевой службе. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
