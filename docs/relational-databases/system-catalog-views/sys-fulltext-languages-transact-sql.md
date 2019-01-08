---
title: sys.fulltext_languages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fulltext_languages
- sys.fulltext_languages_TSQL
- fulltext_languages
- fulltext_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- languages [full-text search]
- sys.fulltext_languages catalog view
ms.assetid: 2ed6b53d-1cf2-4763-9d58-36ea24a610ef
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f3fac82c2fd669bb1a7dd3f45b5a614738fdf189
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/28/2018
ms.locfileid: "52529887"
---
# <a name="sysfulltextlanguages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Это представление каталога содержит одну строку для каждого языка, средства разбиения по словам которого зарегистрированы с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждая строка отображает код и имя языка. Когда средства разбиения по словам зарегистрированы для языка, его других лингвистических ресурсов парадигматические модули, пропускаемые слова (Стоп-слова) и файлы становятся тезауруса для полнотекстового индексирования и выполнения запросов. Значение **имя** или **lcid** можно указать в запросах полнотекстового поиска и полнотекстовый индекс [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкций.  
   
|Столбец|Data type|Описание|  
|------------|---------------|-----------------|  
|**lcid**|**int**|Код локали [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для языка.|  
|**name**|**sysname**|Значение псевдонима в [sys.syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) соответствующее значение **lcid** или строковое представление числового значения кода языка.|  
  
## <a name="values-returned-for-default-languages"></a>Значения, возвращаемые для языков по умолчанию  
 В следующей таблице показаны значения для тех языков, средства разбиения по словам которых зарегистрированы по умолчанию.  
  
|Language|LCID|  
|--------------|----------|  
|Арабский|1025|  
|Bengali (India)|1093|  
|British English|2057|  
|Болгарский|1026|  
|Каталонский|1027|  
|Китайский (Гонконг, КНР)|3076|  
|Chinese (Macao SAR)|5124|  
|Chinese (Singapore)|4100|  
|Хорватский|1050|  
|Czech|1029|  
|Danish|1030|  
|Нидерландский|1043|  
|Английский|1033|  
|Французский|1036|  
|Немецкий|1031|  
|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Greek|1032|  
|Гуджарати|1095|  
|Иврит|1037|  
|Hindi|1081|  
|Исландский|1039|  
|Индонезийский|1057|  
|Итальянский|1040|  
|Японский|1041|  
|Каннада|1099|  
|Корейский|1042|  
|Латышский|1062|  
|Литовский|1063|  
|Malay - Malaysia|1086|  
|Малайялам|1100|  
|Маратхи|1102|  
|Нейтральный|0|  
|Norwegian (Bokmål)|1044|  
|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Польский|1045|  
|Portuguese (Brazil)|1046|  
|Portuguese (Portugal)|2070|  
|Панджабский|1094|  
|Румынский|1048|  
|Русский|1049|  
|Serbian (Cyrillic)|3098|  
|Serbian (Latin)|2074|  
|Китайский (упрощенный)|2052|  
|Словацкий|1051|  
|Словенский|1060|  
|Испанский|3082|  
|Шведский|1053|  
|Тамильский|1097|  
|Телугу|1098|  
|Тайский|1054|  
|Китайский (традиционный)|1028|  
|**Применимо к**: с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Турецкий|1055|  
|Украинский|1058|  
|Урду|1056|  
|Вьетнамский|1066|  
  
## <a name="remarks"></a>Примечания  
 Чтобы обновить список языков, зарегистрированных для полнотекстового поиска, используйте [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)"**update_languages**".  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также  
 [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка и управление файлами тезауруса для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
