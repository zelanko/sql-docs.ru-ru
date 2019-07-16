---
title: sys.fulltext_document_types (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_document_types_TSQL
- fulltext_document_types
- fulltext_document_types_TSQL
- sys.fulltext_document_types
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_document_types catalog view
ms.assetid: 156fcfa4-7304-4a5c-b96f-1c3e061e5df0
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e60f977c220d14680499ca12a4884e912587b7b6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68133853"
---
# <a name="sysfulltextdocumenttypes-transact-sql"></a>sys.fulltext_document_types (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого типа документа, который является доступным для операций полнотекстового индексирования. Каждая строка представляет интерфейс IFilter, который зарегистрирован в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**document_type**|**sysname**|Расширение файла поддерживаемого типа документа.<br /><br /> Это значение может использоваться для определения фильтра, который будет использоваться во время полнотекстового индексирования столбцов типа **varbinary(max)** или **изображение**.|  
|**class_id**|**uniqueidentifier**|Идентификатор GUID класса IFilter, который поддерживает расширение файла.|  
|**путь**|**nvarchar(260)**|Путь к IFilter DLL. Путь является видимым только для элементов предопределенной роли сервера **serveradmin** .|  
|**version**|**sysname**|Версия IFilter DLL.|  
|**Изготовитель**|**sysname**|Название производителя IFilter.<br /><br /> Примечание. Только документы с производителем как [!INCLUDE[msCoName](../../includes/msconame-md.md)] поддерживаются [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
