---
title: "Настройка стоп-слов и списков стоп-слов для полнотекстового поиска и управление ими | Документация Майкрософт"
ms.custom: 
ms.date: 02/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-search
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stoplists [full-text search]
- full-text search [SQL Server], stoplists
- full-text search [SQL Server], noise words
- noise words [full-text search]
- full-text search [SQL Server], stopwords
- stopwords [full-text search]
ms.assetid: 43b5ce7b-9f09-4443-8a5b-c3da6eb28bcc
caps.latest.revision: 81
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4a16a24b197a9fd6a2d1c89f3af8a19b2d2d308d
ms.lasthandoff: 04/11/2017

---
# <a name="configure-and-manage-stopwords-and-stoplists-for-full-text-search"></a>Настройка и управление стоп-словами и списками стоп-слов для полнотекстового поиска
  Чтобы предотвратить чрезмерное увеличение полнотекстового индекса, в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализован механизм, отбрасывающий часто встречающиеся строки, не повышающие эффективность поиска. Эти отброшенные строки называются *стоп-словами*. Во время создания индекса средство полнотекстового поиска не включает стоп-слова в полнотекстовый индекс. Это значит, что полнотекстовые запросы не будут выполнять поиск по стоп-словам.  
   
**Стоп-слова**. Стоп-слово может быть словом конкретного языка. Например, в английском языке такие слова, как «a», «and», «is» и «the», не включаются в полнотекстовый индекс, потому что при поиске они бесполезны. Стоп-слово может также быть *токеном*, не имеющим лингвистического значения.  

**Списки стоп-слов.** Управление стоп-словами в базе данных производится через объекты, называемые списками стоп-слов. *Список стоп-слов* связан с полнотекстовым индексом и применяется к полнотекстовым запросам по этому индексу.
   
## <a name="use-an-existing-stoplist"></a>Использование имеющегося списка стоп-слов  
 Имеющийся список стоп-слов можно использовать следующими способами.  
  
-   Использование поддерживаемого системой списка стоп-слов в базе данных. В составе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставляется системный список стоп-слов, который содержит наиболее часто используемые стоп-слова для каждого поддерживаемого языка, то есть для любого языка, связанного по умолчанию с предложенными конкретными средствами разбиения по словам. Вы можете скопировать системный список стоп-слов и внести необходимые изменения в созданную копию, добавляя и удаляя стоп-слова.  
  
     Системный список стоп-слов содержится в базе данных [Resource](../../relational-databases/databases/resource-database.md) .  
  
-   Использование имеющегося пользовательского списка стоп-слов из другой базы данных в текущем экземпляре сервера, а затем (при необходимости) добавление и удаление стоп-слов.  
  
## <a name="create-a-new-stoplist"></a>Создание списка стоп-слов 
### <a name="create-a-new-stoplist-with-transact-sql"></a>Создание списка стоп-слов с помощью Transact-SQL
Используйте инструкцию [CREATE FULLTEXT STOPLIST](../../t-sql/statements/create-fulltext-stoplist-transact-sql.md).

### <a name="create-a-new-stoplist-with-management-studio"></a>Создание списка стоп-слов с помощью среды Management Studio
  
1.  В обозревателе объектов разверните узел сервера.  
  
2.  Разверните узел **Базы данных**, а затем разверните базу данных, в которой нужно создать список полнотекстовых стоп-слов.  
  
3.  Разверните узел **Хранилище**, а затем щелкните правой кнопкой мыши узел **Полнотекстовые списки стоп-слов**.  
  
4.  Выберите пункт **Создание полнотекстового списка стоп-слов**.  
  
5.  Введите имя нового списка стоп-слов.  
  
6.  Дополнительно можно указать владельца списка стоп-слов.  
  
7.  Выберите один из следующих вариантов создания списка стоп-слов.  
  
    -   **Создать пустой список стоп-слов**  
  
    -   **Создать из системного списка стоп-слов**  
  
    -   **Создать из существующего полнотекстового списка стоп-слов**  
  
     Дополнительные сведения см. в разделе [Создание списка полнотекстовых стоп-слов (страница "Общие")](http://msdn.microsoft.com/library/97f8e82d-82ab-4525-91c9-1ee3ae217309).  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="use-a-stoplist-in-full-text-queries"></a>Использование списка стоп-слов в полнотекстовых запросах  
 Чтобы использовать список стоп-слов в запросах, нужно связать его с полнотекстовым индексом. Можно добавить список стоп-слов к полнотекстовому индексу при создании индекса или изменить индекс позже, добавив список стоп-слов.  
  
### <a name="create-a-full-text-index-and-associate-a-stoplist-with-it"></a>Создание полнотекстового индекса и его связь со списком стоп-слов
Используйте инструкцию [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md).
  
### <a name="associate-or-disassociate-a-stoplist-with-an-existing-full-text-index"></a>Связывание или разъединение списка стоп-слов с имеющимся полнотекстовым индексом
Используйте инструкцию [ALTER FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/alter-fulltext-index-transact-sql.md). 
  
## <a name="change-the-stopwords-in-a-stoplist"></a>Изменение стоп-слов в списке стоп-слов  
### <a name="add-or-drop-stopwords-from-a-stoplist-with-transact-sql"></a>Добавление или удаление стоп-слов из списка стоп-слов с помощью Transact-SQL
Используйте инструкцию [ALTER FULLTEXT STOPLIST (Transact-SQL)](../../t-sql/statements/alter-fulltext-stoplist-transact-sql.md).
  
### <a name="add-or-drop-stopwords-from-a-stoplist-with-management-studio"></a>Добавление или удаление стоп-слов из списка стоп-слов с помощью среды Management Studio  
  
1.  В обозревателе объектов разверните узел сервера.  
  
2.  Раскройте узел **Базы данных**, а затем — соответствующую базу данных.  
  
3.  Разверните узел **Хранилище**и выберите **Полнотекстовые списки стоп-слов**.  
  
4.  Щелкните правой кнопкой мыши список стоп-слов, свойства которого необходимо изменить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне [Свойства полнотекстового списка стоп-слов](http://msdn.microsoft.com/library/2e907f5b-0cf9-484a-afcf-a4e7f1e2f87f) выполните указанные ниже действия.  
  
    1.  В списке **Действия** выберите одно из следующих действий: **Добавить стоп-слово**, **Удалить стоп-слово**, **Удалить все стоп-слова**или **Очистить список стоп-слов**.  
  
    2.  Если для выбранного действия доступно текстовое поле **Стоп-слово** , введите одно стоп-слово. Это стоп-слово должно быть уникальным; иными словами, оно еще не должно присутствовать в списке стоп-слов для выбранного языка.  
  
    3.  Если для выбранного действия доступен список **Язык полнотекстового поиска** , выберите язык.  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="manage-stoplists-and-their-usage"></a>Управление списками стоп-слов и их использование
  
### <a name="view-all-the-stopwords-in-a-stoplist"></a>Просмотр всех стоп-слов в списке стоп-слов
Используйте представление [sys.fulltext_stopwords (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md). 
  
### <a name="get-info-about-all-the-stoplists-in-the-current-database"></a>Получение сведений обо всех списках стоп-слов в текущей базе данных
Используйте представления [sys.fulltext_stoplists (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql.md) и [sys.fulltext_stopwords (Transact-SQL)](../../relational-databases/system-catalog-views/sys-fulltext-stopwords-transact-sql.md).
  
### <a name="view-the-tokenization-result-of-a-word-breaker-thesaurus-and-stoplist-combination"></a>Просмотр разметки, полученной в результате применения средства разбиения по словам, тезауруса и списка стоп-слов
Используйте представление [sys.dm_fts_parser (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql.md).

### <a name="suppress-an-error-message-if-stopwords-cause-a-boolean-operation-on-a-full-text-query-to-fail"></a>Подавление сообщения об ошибке при неуспешном завершении логической операции, применяемой к полнотекстовому запросу, из-за стоп-слов
Используйте [параметр конфигурации сервера transform noise words](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md). 
   
## <a name="more-info-about-stopword-position"></a>Дополнительные сведения о позиции стоп-слов
 Хотя стоп-слова при поиске не учитываются, полнотекстовый индекс принимает во внимание расположение таких слов. Рассмотрим для примера фразу «Instructions are applicable to these Adventure Works Cycles models». Позиции слов в этой фразе приведены в следующей таблице.  
  
|Word|Положение|  
|----------|--------------|  
|Instructions|1|  
|are|2|  
|applicable|3|  
|в|4|  
|these|5|  
|Adventure|6|  
|Works|7|  
|Cycles|8|  
|модели|9|  
  
 Стоп-слова «are», «to» и «these», занимающие позиции 2, 4 и 5, в полнотекстовый индекс не включаются. Однако данные об их позициях сохраняются, благодаря чему позиции других слов в фразе остаются неизменными.   
  
## <a name="upgrade-noise-words-from-sql-server-2005"></a>Обновление пропускаемых слов из SQL Server 2005  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] пропускаемые слова были заменены стоп-словами. При обновлении базы данных с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]файлы пропускаемых слов более не используются. Однако файлы пропускаемых слов хранятся в папке FTDATA\FTNoiseThresaurusBak, и их можно использовать в дальнейшем при обновлении или построении соответствующих списков стоп-слов. Сведения об обновлении файлов пропускаемых слов с переходом к спискам стоп-слов см. в разделе [Обновление полнотекстового поиска](../../relational-databases/search/upgrade-full-text-search.md).  
  
  
  

