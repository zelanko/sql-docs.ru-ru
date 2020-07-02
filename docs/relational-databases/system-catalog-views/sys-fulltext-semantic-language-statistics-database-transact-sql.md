---
title: sys. fulltext_semantic_language_statistics_database (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database
- sys.fulltext_semantic_language_statistics_database
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_language_statistics_database catalog view
ms.assetid: 32e95614-ed88-4068-8c37-1e21544717bc
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 993715676a6abd5d6687b7b1adbbeb3ab121d39f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764685"
---
# <a name="sysfulltext_semantic_language_statistics_database-transact-sql"></a>sys.fulltext_semantic_language_statistics_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Возвращает строку о базе данных статистики семантики языка, установленной на текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Можно выполнить запрос к этому представлению для сбора сведений о компоненте статистической семантики языка, необходимых для семантической обработки.  
   
  
||||  
|-|-|-|  
|**Имя столбца**|**Type**|**Описание**|  
|**database_id**|**int**|Идентификатор базы данных, уникальный внутри экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**register_date**|**datetime**|Дата регистрации базы данных для семантической обработки.|  
|**registered_by**|**int**|Идентификатор участника на уровне сервера, зарегистрировавшего базу данных для семантической обработки.|  
|**version**|**nvarchar(128)**|Сведения о последней версии, характерные для базы данных статистики семантики языка.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Для получения сведений о языках, поддерживаемых для семантического индексирования, запросите представление каталога [sys. fulltext_semantic_languages &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как выполнить запрос к представлению **sys. fulltext_semantic_language_statistics_database** , чтобы получить сведения о базе данных семантической статистики языка, зарегистрированной в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
