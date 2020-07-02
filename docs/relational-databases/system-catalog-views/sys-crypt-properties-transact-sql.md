---
title: sys. crypt_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- crypt_properties
- crypt_properties_TSQL
- sys.crypt_properties_TSQL
- sys.crypt_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.crypt_properties catalog view
ms.assetid: d5684f5a-30b1-418e-ae4d-ab040db9257e
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5a4c03687f6adac3f67f3e6aa231c384a6d5e009
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85725802"
---
# <a name="syscrypt_properties-transact-sql"></a>sys.crypt_properties (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Возвращает по одной строке для каждого криптографического свойства, ассоциированного с защищаемым объектом.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**class**|**tinyint**|Задает класс, для которого существует свойство.<br /><br /> 1 = Объект или столбец<br /> 5 = Сборка|  
|**class_desc**|**nvarchar(60)**|Описание класса, для которого существует свойство.<br /><br /> OBJECT_OR_COLUMN<br /> ASSEMBLY|  
|**major_id**|**int**|Идентификатор предмета, для которого существует свойство, интерпретируемое согласно классу|  
|**отпечатк**|**varbinary(32)**|Хэш SHA-1 используемого сертификата или асимметричного ключа.|  
|**crypt_type**|**char (4)**|Тип шифрования.<br /><br /> СПВК = подписан закрытым ключом сертификата<br /><br /> SPVC = подписано асимметричным закрытым ключом<br /><br /> CPVC = Подпись закрытым ключом сертификата<br /><br /> CPVA = Подпись закрытым асимметричным ключом|  
|**crypt_type_desc**|**nvarchar(60)**|Описание типа шифрования.<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY<br /><br /> SIGNATURE BY CERTIFICATE<br /><br /> SIGNATURE BY ASYMMETRIC KEY|  
|**crypt_property**|**varbinary(max)**|Подписанные или зашифрованные биты. Для подписанного модуля это биты сигнатуры модуля.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также  
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Иерархия шифрования](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [Защищаемые объекты](../../relational-databases/security/securables.md)   
 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)   
 [Создание &#40;ов на основе СИММЕТРИЧНого ключа&#41;Transact-SQL](../../t-sql/statements/create-symmetric-key-transact-sql.md)   
 [Создание АСИММЕТРИЧного ключа &#40;&#41;Transact-SQL](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
