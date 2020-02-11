---
title: sys. database_scoped_credentials (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
author: VanMSFT
ms.author: vanto
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03687ea50b04c96aa4dbafab9d02d2bbc33a14b3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079425"
---
# <a name="sysdatabase_scoped_credentials-transact-sql"></a>sys. database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  Возвращает по одной строке для каждого учетного данных области базы данных в базе данных.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|name|**имеет sysname**|Имя учетных данных области базы данных. Уникален в базе данных.|  
|credential_id|**int**|Идентификатор учетных данных области базы данных. Уникален в базе данных.|  
|principal_id|**int**|Идентификатор участника базы данных, который владеет ключом.|  
|credential_identity|**nvarchar (4000)**|Имя применяемого идентификатора. Обычно это пользователь Windows. Это имя не обязательно должно быть уникальным.|  
|create_date|**datetime**|Время создания учетных данных области базы данных.|  
|modify_date|**datetime**|Время последнего изменения учетных данных области базы данных.|  
|target_type|**nvarchar (100)**|Тип учетных данных области базы данных. Возвращает `NULL` значение для учетных данных области базы данных.|  
|target_id|**int**|Идентификатор объекта, с которым сопоставлены учетные данные области базы данных. Возвращает 0 для учетных данных области базы данных|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение `CONTROL` на базу данных.  
  
## <a name="see-also"></a>См. также:  
 [Учетные данные &#40;ядро СУБД&#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [Создание УЧЕТных данных с областью действия базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ИЗМЕНЕНИЕ УЧЕТных данных с областью действия базы данных &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [УДАЛИТЬ УЧЕТные данные области базы данных &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
