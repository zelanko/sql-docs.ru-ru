---
title: sp_fulltext_load_thesaurus_file (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_load_thesaurus_file
- sp_fulltext_load_thesaurus_file_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_load_thesaurus_file
- full-text indexes [SQL Server], thesaurus files
- thesaurus [full-text search], editing
ms.assetid: 73a309c3-6d22-42dc-a6fe-8a63747aa2e4
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d076bfde2e4dc4a71af558a08f197d20144ce9db
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840978"
---
# <a name="spfulltextloadthesaurusfile-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает на экземпляре сервера синтаксический анализ и загрузку данных из файла тезауруса, который соответствует языку с указанным кодом языка. Эту хранимую процедуру полезно использовать после обновления файла тезауруса. Выполнение **sp_fulltext_load_thesaurus_file** запускает повторную компиляцию полнотекстовых запросов, использующих тезаурус указанного кода языка.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *lcid*  
 Целое число, сопоставляющее идентификатор локали, для которого необходимо загрузить XML-определение тезауруса. Чтобы получить коды языков, доступных на экземпляре сервера, используйте [sys.fulltext_languages &#40;Transact-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) представления каталога.  
  
 **@loadOnlyIfNotLoaded** = *Действие*  
 Указывает, нужно ли загружать файл тезауруса во внутренние таблицы тезауруса в случае, если он уже загружен. *Действие* является одним из:  
  
|Значение|Определение|  
|-----------|----------------|  
|**0**|Загружать файл тезауруса независимо от того, загружен ли он. Это поведение по умолчанию **sp_fulltext_load_thesaurus_file**.|  
|1|Загружать файл тезауруса только в случае, если он еще не загружен.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Примечания  
 Файлы тезауруса загружаются автоматически полнотекстовыми запросами, использующими этот тезаурус. Чтобы избежать снижения производительности в первый раз на полнотекстовые запросы, мы рекомендуем выполнить **sp_fulltext_load_thesaurus_file**.  
  
 Используйте [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)"**update_languages**" для обновления списка языков, зарегистрированных для полнотекстового поиска.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или системный администратор могут выполнять процедуру **sp_fulltext_load_thesaurus_file** хранимой процедуры.  
  
 Только системные администраторы имеют право обновлять, изменять и удалять файлы тезауруса.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-load-a-thesaurus-file-even-if-it-is-already-loaded"></a>A. Загрузка файла тезауруса даже в случае, если он уже загружен  
 В следующем примере выполняется синтаксический анализ и загрузка файла тезауруса для английского языка.  
  
```  
EXEC sys.sp_fulltext_load_thesaurus_file 1033;  
GO  
```  
  
### <a name="b-load-a-thesaurus-file-only-if-it-is-not-yet-loaded"></a>Б. Загрузка файла тезауруса только в случае, если он еще не загружен  
 В следующем примере выполняется синтаксический анализ и загрузка файла тезауруса для арабского языка, если он еще не загружен.  
  
```  
EXEC sys.sp_fulltext_load_thesaurus_file 1025, @loadOnlyIfNotLoaded = 1;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [FULLTEXTSERVICEPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Настройка и управление файлами тезауруса для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [Настройка файлов тезауруса и управление ими для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)  
  
  
