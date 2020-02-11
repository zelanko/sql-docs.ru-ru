---
title: sys. remote_logins (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_logins_TSQL
- remote_logins
- remote_logins_TSQL
- sys.remote_logins
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_logins catalog view
ms.assetid: 38477e91-d084-4df7-b1de-b930c5580189
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 371f8e2bf9a5d67d68e9c1d48502bf3fa2f81db6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67904569"
---
# <a name="sysremote_logins-transact-sql"></a>sys.remote_logins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает по строке для каждого соответствия между локальным и удаленным именем входа. Это представление каталога используется для сопоставления принимаемых локальных имен входа, якобы полученных от соответствующего сервера, с действительным локальным именем входа.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|Идентификатор сервера в **sys. Servers**. Это имя предоставляется соединением с «удаленным» сервером.|  
|**remote_name**|**имеет sysname**|Имя входа, которое предоставляет соединение для сопоставления. Если это значение равно NULL, используется имя входа, указанное в соединении.|  
|**local_principal_id**|**int**|Идентификатор сервера-участника, которому сопоставляется имя входа. Если это значение равно 0, удаленное имя входа сопоставляется такому же имени.|  
|**modify_date**|**datetime**|Дата последнего изменения связанного имени входа.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога связанных серверов &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
