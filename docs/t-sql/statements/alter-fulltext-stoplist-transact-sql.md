---
title: "ALTER FULLTEXT STOPLIST (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER FULLTEXT STOPLIST
- ALTER_FULLTEXT_STOPLIST_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- ALTER FULLTEXT STOPLIST statement
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: f6ad87d5-6a34-435a-8456-8244947c5c83
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 314e41c5b885ee5441dbc4c88db14c22fc50e7b7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-fulltext-stoplist-transact-sql"></a>ALTER FULLTEXT STOPLIST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Вставляет или удаляет стоп-слово в используемый по умолчанию полнотекстовый список стоп-слов текущей базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER FULLTEXT STOPLIST stoplist_name  
{   
        ADD [N] 'stopword' LANGUAGE language_term    
  | DROP   
    {  
        'stopword' LANGUAGE language_term   
      | ALL LANGUAGE language_term   
      | ALL  
     }  
;  
```  
  
## <a name="arguments"></a>Аргументы  
 *stoplist_name*  
 Имя изменяемого списка стоп-слов. *stoplist_name* не может превышать 128 символов.  
  
 **"** *стоп-слово* **"**  
 Строка, которая может быть словом с лингвистическим значением в определенном языке или токеном, не имеющим лингвистического значения. *Стоп-слово* ограничено до максимальной длины токена (64 символов). Стоп-слово можно указать в виде строки в Юникоде.  
  
 Язык *language_term*  
 Указывает язык, связанный с *стоп-слово* добавляемым или удаляемым.  
  
 *language_term* может быть указан как строковое, целочисленное или шестнадцатеричное значение, соответствующее коду локали (LCID) языка, как показано ниже:  
  
|Формат|Description|  
|------------|-----------------|  
|Строковые значения|*language_term* соответствует **псевдоним** значение столбца в [sys.syslanguages (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) Просмотр в режиме совместимости. Строка должна быть заключена в одинарные кавычки, как и в **"***language_term***"**.|  
|Целочисленный|*language_term* является код языка.|  
|Шестнадцатеричный|*language_term* 0 x следуют шестнадцатеричное значение кода языка. Шестнадцатеричное значение не может иметь более восьми знаков, включая начальные нули. Если значение указано в формате двухбайтовой кодировки (DBCS), SQL Server преобразует его в Юникод.|  
  
 Добавить **"***стоп-слово***"** языка *language_term*  
 Добавляет стоп-слово в список стоп-слов для языка, указанного в аргументе LANGUAGE *language_term*.  
  
 Если указанное сочетание ключевого слова и значения кода языка в рамках данного списка стоп-слов не уникальны, возвращается ошибка.  Если значение кода языка не соответствует зарегистрированному языку, формируется ошибка.  
  
 DROP { **"***стоп-слово***"** язык *language_term* | ВСЕ ЯЗЫКОВЫЕ *language_term* | ALL}  
 Удаляет стоп-слово из списка стоп-слов.  
  
 **"** *стоп-слово* **"** языка *language_term*  
 Удаляет указанное стоп-слово для языка, указанного аргументом *language_term*.  
  
 ВСЕ ЯЗЫКОВЫЕ *language_term*  
 Удаляет все Стоп-слова для языка, указанного аргументом *language_term*.  
  
 ALL  
 Удаляет все стоп-слова из списка стоп-слов.  
  
## <a name="remarks"></a>Замечания  
 Инструкция CREATE FULLTEXT STOPLIST поддерживается только для уровня совместимости 100 и выше. Для уровней совместимости 80 и 90 системный список стоп-слов всегда назначается базе данных.  
  
## <a name="permissions"></a>Permissions  
 Чтобы назначить список стоп-слов в качестве используемого по умолчанию списка стоп-слов базы данных, необходимо разрешение ALTER DATABASE. Чтобы изменить список стоп-слов, необходимо быть владельцем или членом **db_owner** или **db_ddladmin** предопределенных ролей базы данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере демонстрируется изменение списка стоп-слов `CombinedFunctionWordList` путем добавления слова «en» для испанского и затем французского языков.  
  
```  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'Spanish';  
ALTER FULLTEXT STOPLIST CombinedFunctionWordList ADD 'en' LANGUAGE 'French';  
```  
  
## <a name="see-also"></a>См. также:  
 [СОЗДАТЬ ПОЛНОТЕКСТОВЫЙ список стоп-СЛОВ &#40; Transact-SQL &#41;](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md)   
 [DROP FULLTEXT STOPLIST &#40; Transact-SQL &#41;](../../t-sql/statements/drop-fulltext-stoplist-transact-sql.md)   
 [Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [sys.fulltext_stoplists &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md)   
 [sys.fulltext_stopwords &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md)   
 [Настройка стоп-слов, списков стоп-слов и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)  
  
  

