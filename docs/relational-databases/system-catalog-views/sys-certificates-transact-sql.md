---
title: sys. Certificates (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- certificates
- certificates_TSQL
- sys.certificates_TSQL
- sys.certificates
dev_langs:
- TSQL
helpviewer_keywords:
- sys.certificates catalog view
ms.assetid: e5046102-a65c-401e-b80d-05636884dec9
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08193bd8f9b6dfd3aace80315c75bbb88e076f3a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "75255843"
---
# <a name="syscertificates-transact-sql"></a>sys.certificates (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает строку для каждого сертификата в базе данных.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя сертификата. Уникален в пределах базы данных.|  
|**certificate_id**|**int**|Идентификатор сертификата. Уникален в пределах базы данных.|  
|**principal_id**|**int**|Идентификатор участника базы данных, владеющего сертификатом.|  
|**pvt_key_encryption_type**|**char (2)**|Способ шифрования закрытого ключа.<br /><br /> NA = сертификат не имеет закрытого ключа.<br /><br /> MK = закрытый ключ зашифрован главным ключом.<br /><br /> MK = закрытый ключ зашифрован пользовательским паролем.<br /><br /> MK = закрытый ключ зашифрован главным ключом службы.|  
|**pvt_key_encryption_type_desc**|**nvarchar(60)**|Описание способа шифрования закрытого ключа.<br /><br /> NO_PRIVATE_KEY<br /><br /> ENCRYPTED_BY_MASTER_KEY<br /><br /> ENCRYPTED_BY_PASSWORD<br /><br /> ENCRYPTED_BY_SERVICE_MASTER_KEY|  
|**is_active_for_begin_dialog**|**bit**|Если значение равно 1, то данный сертификат применяется для инициализации зашифрованных диалоговых окон службы.|  
|**issuer_name**|**nvarchar (442)**|Имя поставщика сертификата.|  
|**cert_serial_number**|**nvarchar (64)**|Регистрационный номер сертификата.|  
|**трансляцию**|**varbinary(85)**|Идентификатор SID имени входа для данного сертификата.|  
|**string_sid**|**nvarchar(128)**|Строковое представление идентификатора SID имени входа для данного сертификата|  
|**Тема**|**nvarchar(4000)**|Субъект сертификата.|  
|**expiry_date**|**datetime**|Дата окончания срока действия сертификата.|  
|**start_date**|**datetime**|Дата выпуска сертификата.|  
|**thumbprint**|**varbinary(32)**|Хэш сертификата SHA-1. Хэш SHA-1 является глобально уникальным.|  
|**attested_by**|**nvarchar(260)**|Только для системного использования.|  
|**pvt_key_last_backup_date**|**datetime**|Дата и время последнего экспорта закрытого ключа сертификата.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Представления каталога &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
  
  
