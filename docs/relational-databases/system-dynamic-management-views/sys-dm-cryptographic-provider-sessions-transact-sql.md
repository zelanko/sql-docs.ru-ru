---
title: sys.dm_cryptographic_provider_sessions (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_cryptographic_provider_sessions
- dm_cryptographic_provider_sessions_TSQL
- sys.dm_cryptographic_provider_sessions_TSQL
- dm_cryptographic_provider_sessions
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_sessions dynamic management function
ms.assetid: 9a4de02b-1a07-4850-979a-0861fddb7f9d
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 739c1fe64814ab53bfcf166cacac2d21655df8d1
ms.sourcegitcommit: 7019ac41524bdf783ea2c129c17b54581951b515
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34463670"
---
# <a name="sysdmcryptographicprovidersessions-transact-sql"></a>sys.dm_cryptographic_provider_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об открытых сеансах для поставщика служб шифрования.  
 
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.dm_cryptographic_provider_sessions(session_identifier)  
```  
  
## <a name="arguments"></a>Аргументы  
 *session_identifier*  
 Целое число, указывающее сеансы для возврата:  
  
 0 = только текущее соединение;  
  
 1 = все криптографические соединения.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**provider_id**|**int**|Идентификационный номер поставщика служб шифрования.|  
|**session_handle**|**varbytes(8)**|Дескриптор сеанса с криптографической защитой.|  
|**Удостоверение**|**nvarchar(128)**|Идентификатор, используемый для проверки подлинности поставщика служб шифрования.|  
|**spid**|**короткий**|Идентификатор SPID сеанса для соединения. Дополнительные сведения см. в статье [@@SPID (Transact-SQL)](../../t-sql/functions/spid-transact-sql.md).|  
  
## <a name="remarks"></a>Примечания  
 **Sys.dm_cryptographic_provider_sessions** представление доступно public для текущего соединения. Чтобы просмотреть все криптографические соединения, необходимо иметь **УПРАВЛЕНИЯ** разрешений сервера.  
  
## <a name="see-also"></a>См. также  
 [Представления каталога безопасности (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Расширенное управление ключами (EKM)](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER (Transact-SQL)](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [Иерархия средств шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
