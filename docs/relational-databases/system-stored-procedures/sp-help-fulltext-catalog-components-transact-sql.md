---
description: sp_help_fulltext_catalog_components (Transact-SQL)
title: sp_help_fulltext_catalog_components (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_catalog_components_TSQL
- sp_help_fulltext_catalog_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_catalog_components
ms.assetid: fbd6a3d4-6a4c-42a2-bff8-2a5eb0745e47
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2884cda986a99f23c88c71c8960d25a467de0663
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89548046"
---
# <a name="sp_help_fulltext_catalog_components-transact-sql"></a>sp_help_fulltext_catalog_components (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает список всех компонентов (фильтров, разделителей слов и обработчиков протоколов), используемых для всех полнотекстовых каталогов в текущей базе данных.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_catalog_components  
```  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**имя полнотекстового каталога**|**int**|Имя полнотекстового каталога.|  
|**Идентификатор полнотекстового каталога**|**sysname**|Идентификатор полнотекстового каталога.|  
|**componenttype**|**sysname**|Тип компонента. Это может быть:<br /><br /> Filter<br /><br /> Обработчик протокола<br /><br /> Средство разбиения по словам|  
|**ComponentName**|**sysname**|Имя компонента.|  
|**этому**|**uniqueidentifier**|Идентификатор класса компонента.|  
|**FullPath**|**nvarchar(256)**|Путь к расположению компонента.<br /><br /> NULL = вызывающая сторона не является членом предопределенной роли сервера **serveradmin** .|  
|**version**|**nvarchar(30)**|Версия компонента.|  
|**производителя**|**sysname**|Имя производителя компонента.|  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры полнотекстового поиска и семантического поиска &#40;языке Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)   
 [sys.fulltext_catalogs (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql.md)   
 [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)   
 [Полнотекстовый поиск](../../relational-databases/search/full-text-search.md)  
  
  
