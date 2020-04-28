---
title: sys. Credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/06/2020
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.credentials
- sys.credentials_TSQL
- credentials_TSQL
- credentials
dev_langs:
- TSQL
helpviewer_keywords:
- sys.credentials catalog view
ms.assetid: ea48cf80-904a-4273-a950-6d35b1b0a1b6
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f87378897256f8b4fae26b30263577bedede6175
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "80752889"
---
# <a name="syscredentials-transact-sql"></a>sys.credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-asdw-pdw-md.md)]

  Возвращает одну строку для каждого учетного данных уровня сервера.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|credential_id|**int**|Идентификатор учетных данных. Уникально в пределах сервера.|  
|name|**sysname**|Имя учетных данных. Уникально в пределах сервера.|  
|credential_identity|**nvarchar(4000)**|Имя применяемого идентификатора. Обычно это пользователь Windows. Это имя не обязательно должно быть уникальным.|  
|create_date|**datetime**|Время создания учетных данных.|  
|modify_date|**datetime**|Время последнего изменения учетных данных.|  
|target_type|**nvarchar (100)**|Тип учетных данных. Возвращает значение NULL для традиционных учетных данных и значение CRYPTOGRAPHIC PROVIDER для учетных данных, сопоставленных с поставщиком служб шифрования. Дополнительные сведения о поставщиках управления внешними ключами см. в разделе [Расширенное управление ключами &#40;расширенный ](../../relational-databases/security/encryption/extensible-key-management-ekm.md)доступ к&#41;.|  
|target_id|**int**|Идентификатор объекта, с которым сопоставлены учетные данные. Возвращает значение 0 для традиционных учетных данных и значение, отличное от 0, для учетных данных, сопоставленных с поставщиком служб шифрования. Дополнительные сведения о поставщиках управления внешними ключами см. в разделе [Расширенное управление ключами &#40;расширенный ](../../relational-databases/security/encryption/extensible-key-management-ekm.md)доступ к&#41;.|  

## <a name="remarks"></a>Remarks  
Учетные данные уровня базы данных см. в разделе [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md).
  
## <a name="permissions"></a>Разрешения  
 Требуется `VIEW ANY DEFINITION` разрешение или `ALTER ANY CREDENTIAL` разрешение. Кроме того, участнику не должно быть отказано `VIEW ANY DEFINITION` в разрешении.  
  
## <a name="see-also"></a>См. также:  
 [sys. database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [Учетные данные &#40;ядро СУБД&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Участники (ядро СУБД)](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)  
  
  
