---
description: Представления каталога схем — sys. schemas
title: sys. schemas (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- schemas_TSQL
- sys.schemas_TSQL
- schemas
- sys.schemas
dev_langs:
- TSQL
helpviewer_keywords:
- sys.schemas catalog view
ms.assetid: 29af5ce5-2af7-4103-8f08-3ec92603ba05
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 473dd22d2f19d29e5b778a585ad59d0d99acbaee
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479105"
---
# <a name="schemas-catalog-views---sysschemas"></a>Представления каталога схем — sys. schemas
[!INCLUDE [sql-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdbmi-asa-pdw.md)]

  Содержит по одной строке для каждой схемы базы данных.  
  
> [!NOTE]  
>  Схемы базы данных отличаются от XML-схем, которые используются для определения модели содержимого XML-документов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Имя схемы. Уникален в пределах базы данных.|  
|**schema_id**|**int**|Идентификатор схемы. Уникален в пределах базы данных.|  
|**principal_id**|**int**|Идентификатор участника, владеющего этой схемой.|  
  
## <a name="remarks"></a>Комментарии  
Схемы баз данных действуют как пространства имен или контейнеры для объектов, таких как таблицы, представления, процедуры и функции, которые можно найти в представлении каталога **sys. Objects** .  

Каждая схема имеет владельца. Владелец является [субъектом](../../relational-databases/security/authentication-access/principals-database-engine.md)безопасности.
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
[Субъекты](../../relational-databases/security/authentication-access/principals-database-engine.md)

[Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   

[Представления каталога схем &#40;Transact-SQL&#41;](./catalog-views-transact-sql.md)   

[sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
