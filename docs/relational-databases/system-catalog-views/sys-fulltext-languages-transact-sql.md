---
description: sys.fulltext_languages (Transact-SQL)
title: sys.fulltext_languages (Transact-SQL) | Документация Майкрософт
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
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9e8c29c32323c2c75e573e8e76851e4026a6e815
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464695"
---
# <a name="sysfulltext_languages-transact-sql"></a>sys.fulltext_languages (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Это представление каталога содержит одну строку для каждого языка, средства разбиения по словам которого зарегистрированы с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. В каждой строке отображаются код и имя языка. При регистрации средств разбиения по словам для языка другие лингвистические ресурсы — парадигматические модули, неучитываемые слова (стоп-слова) и файлы тезауруса становятся доступными для операций полнотекстового индексирования и запросов. В полнотекстовых запросах и инструкциях полнотекстового индекса можно указать значение **Name** или **LCID** [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
   
|Столбец|Тип данных|Описание|  
|------------|---------------|-----------------|  
|**lcid**|**int**|Код локали [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows для языка.|  
|**name**|**sysname**|Является либо значением псевдонима в [sys.sysязыках](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) , соответствующих значению **LCID** , либо строковым представлением числового кода языка.|  
  
## <a name="values-returned-for-default-languages"></a>Значения, возвращаемые для языков по умолчанию  
 В следующей таблице показаны значения для тех языков, средства разбиения по словам которых зарегистрированы по умолчанию.  
  
|Язык|LCID|  
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
|Чешский|1029|  
|Датский|1030|  
|Нидерландский|1043|  
|Английский|1033|  
|Французский|1036|  
|Немецкий|1031|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Греческий|1032|  
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
|Малаялам|1100|  
|Маратхи|1102|  
|нейтральное выражение.|0|  
|Норвежский (Букмол)|1044|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Польский|1045|  
|Португальский (Бразилия)|1046|  
|Португальский (Португалия)|2070|  
|Панджаби|1094|  
|Румынский|1048|  
|русском языке|1049|  
|Сербский (кириллица)|3098|  
|Сербский (латиница)|2074|  
|Китайский (упрощенный)|2052|  
|Словацкий|1051|  
|Словенский|1060|  
|Испанский|3082|  
|Шведский|1053|  
|Тамильский|1097|  
|Телугу|1098|  
|Тайский|1054|  
|Китайский (традиционный)|1028|  
|**Область применения**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] и более поздних версий.<br /><br /> Турецкий|1055|  
|Украинский|1058|  
|Урду|1056|  
|Вьетнамский|1066|  
  
## <a name="remarks"></a>Комментарии  
 Чтобы обновить список языков, зарегистрированных в полнотекстовом поиске, используйте [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)"**update_languages**".  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [sp_fulltext_load_thesaurus_file &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-load-thesaurus-file-transact-sql.md)   
 [sp_fulltext_service (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка файлов тезауруса для поиска Full-Text и управление ими](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md)  
  
  
