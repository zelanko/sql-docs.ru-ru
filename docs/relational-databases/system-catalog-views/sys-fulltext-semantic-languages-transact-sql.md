---
title: sys. fulltext_semantic_languages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: aad472489192516d367185572d1c9ac67eb78154
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248782"
---
# <a name="sysfulltext_semantic_languages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает по одной строке для каждого языка, модель статистики которого зарегистрирована на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если языковая модель зарегистрирована, язык включается для семантического индексирования.  
  
 Это представление каталога аналогично представлению [sys. fulltext_languages &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md).  
    
|Имя столбца|Тип|Описание|  
|-|-|-|   
|lcid|INT|Код локали Microsoft Windows (LCID) для языка.|  
|name|sysname|Является либо значением псевдонима в [sys.sysязыках &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) соответствующим значению **LCID**, либо строковым представлением числового LCID.|  
  
## <a name="general-remarks"></a>Общие замечания  
 Дополнительные сведения см. в разделе [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md).  
  
## <a name="metadata"></a>Метаданные  
 Для получения дополнительных сведений о базе данных семантической статистики языка, установленной для поддержки семантического индексирования, запросите представление каталога [sys. fulltext_semantic_language_statistics_database &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Безопасность  
  
### <a name="permissions"></a>Разрешения  
 Видимость метаданных в представлениях каталогов ограничивается защищаемыми объектами, которыми пользователь владеет или на которые ему были предоставлены разрешения.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как выполнить запрос к представлению **sys. fulltext_semantic_languages** , чтобы получить сведения обо всех языковых моделях, зарегистрированных для семантического индексирования в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Установка и настройка семантического поиска](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
