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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ac01c2d29dbe79d0a5702e1bd42730d0b31efcf2
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827795"
---
# <a name="sp_fulltext_load_thesaurus_file-transact-sql"></a>sp_fulltext_load_thesaurus_file (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает на экземпляре сервера синтаксический анализ и загрузку данных из файла тезауруса, который соответствует языку с указанным кодом языка. Эту хранимую процедуру полезно использовать после обновления файла тезауруса. Выполнение **sp_fulltext_load_thesaurus_file** вызывает повторную компиляцию полнотекстовых запросов, использующих ТЕЗАУРУС указанного LCID.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sys.sp_fulltext_load_thesaurus_file lcid [ , @loadOnlyIfNotLoaded  = action ]   
```  
  
## <a name="arguments"></a>Аргументы  
 *lcid*  
 Целое число, сопоставляющее идентификатор локали, для которого необходимо загрузить XML-определение тезауруса. Чтобы получить ИДЕНТИФИКАТОРы языков, доступных на экземпляре сервера, используйте представление каталога [&#41;sys. fulltext_languages &#40;Transact-SQL](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md) .  
  
 ** \@ **  =  *действие* лоадонлифнотлоадед  
 Указывает, нужно ли загружать файл тезауруса во внутренние таблицы тезауруса в случае, если он уже загружен. *действие* является одним из следующих:  
  
|Значение|Определение|  
|-----------|----------------|  
|**0**;|Загружать файл тезауруса независимо от того, загружен ли он. Это поведение по умолчанию для **sp_fulltext_load_thesaurus_file**.|  
|1|Загружать файл тезауруса только в случае, если он еще не загружен.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="remarks"></a>Remarks  
 Файлы тезауруса загружаются автоматически полнотекстовыми запросами, использующими этот тезаурус. Чтобы избежать этого первого воздействия на полнотекстовые запросы, рекомендуется выполнить **sp_fulltext_load_thesaurus_file**.  
  
 Используйте [sp_fulltext_service](../../relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql.md)"**update_languages**", чтобы обновить список языков, зарегистрированных в полнотекстовом поиске.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или системного администратора могут выполнять хранимую процедуру **sp_fulltext_load_thesaurus_file** .  
  
 Только системные администраторы имеют право обновлять, изменять и удалять файлы тезауруса.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-load-a-thesaurus-file-even-if-it-is-already-loaded"></a>A. Загрузка файла тезауруса даже в случае, если он уже загружен  
 В следующем примере выполняется синтаксический анализ и загрузка файла тезауруса для английского языка.  
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1033;
```  
  
### <a name="b-load-a-thesaurus-file-only-if-it-is-not-yet-loaded"></a>Б. Загрузка файла тезауруса только в случае, если он еще не загружен  
 В следующем примере выполняется синтаксический анализ и загрузка файла тезауруса для арабского языка, если он еще не загружен.  
  
```sql
EXEC sys.sp_fulltext_load_thesaurus_file 1025, @loadOnlyIfNotLoaded = 1;
```  

## <a name="see-also"></a>См. также

[FULLTEXTSERVICEPROPERTY (Transact-SQL)](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)  
[Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
[Настройка и управление файлами тезауруса для полнотекстового поиска](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)
