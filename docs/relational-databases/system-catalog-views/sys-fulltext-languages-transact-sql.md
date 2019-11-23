---
title: sys. fulltext_languages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e5af224150508f048d91345cba595517209f824d
ms.sourcegitcommit: e37636c275002200cf7b1e7f731cec5709473913
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "73981774"
---
# <a name="sysfulltext_languages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Это представление каталога содержит одну строку для каждого языка, средства разбиения по словам которого зарегистрированы с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В каждой строке отображается LCID и имя языка. При регистрации средств разбиения по словам для языка другие лингвистические ресурсы — парадигматические модули, неучитываемые слова (стоп-слова) и файлы тезауруса становятся доступными для операций полнотекстового индексирования и запросов. Значение **Name** или **LCID** можно указать в полнотекстовых запросах и инструкциях полнотекстового индекса [!INCLUDE[tsql](../../includes/tsql-md.md)].  
   
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|**lcid**|**int**|Код локали [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для языка.|  
|**name**|**sysname**|Либо значение псевдонима в [таблице sys. syslanguages](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) , соответствующее значению **LCID** , либо строковое представление числового идентификатора LCID.|  
  
## <a name="values-returned-for-default-languages"></a>Значения, возвращаемые для языков по умолчанию  
 В следующей таблице показаны значения для тех языков, средства разбиения по словам которых зарегистрированы по умолчанию.  
  
|Язык|LCID|  
|--------------|----------|  
|Arabic|1025|  
|Bengali (India)|1093|  
|British English|2057|  
|Bulgarian|1026|  
|Catalan|1027|  
|Китайский (Гонконг, КНР)|3076|  
|Chinese (Macao SAR)|5124|  
|Chinese (Singapore)|4100|  
|Croatian|1050|  
|Czech|1029|  
|Датский|1030|  
|Dutch|1043|  
|English|1033|  
|French|1036|  
|German|1031|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Greek|1032|  
|Gujarati|1095|  
|Hebrew|1037|  
|Hindi|1081|  
|Icelandic|1039|  
|Indonesian|1057|  
|Italian|1040|  
|Japanese|1041|  
|Kannada|1099|  
|Korean|1042|  
|Latvian|1062|  
|Lithuanian|1063|  
|Malay - Malaysia|1086|  
|Malayalam|1100|  
|Marathi|1102|  
|Neutral|0|  
|Norwegian (Bokmål)|1044|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Polish|1045|  
|Portuguese (Brazil)|1046|  
|Portuguese (Portugal)|2070|  
|Punjabi|1094|  
|Romanian|1048|  
|Russian|1049|  
|Serbian (Cyrillic)|3098|  
|Serbian (Latin)|2074|  
|Simplified Chinese|2052|  
|Slovak|1051|  
|Slovenian|1060|  
|Spanish|3082|  
|Swedish|1053|  
|Tamil|1097|  
|Telugu|1098|  
|Thai|1054|  
|Traditional Chinese|1028|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Turkish|1055|  
|Ukrainian|1058|  
|Urdu|1056|  
|Vietnamese|1066|  
  
## <a name="remarks"></a>Remarks  
 Чтобы обновить список языков, зарегистрированных в полнотекстовом поиске, используйте [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)"**update_languages**".  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также статью  
 [sp_fulltext_load_thesaurus_file &#40;  Transact-&#41; SQL](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)  
 [sp_fulltext_service (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка файлов тезауруса для полнотекстового поиска и управление ими](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
