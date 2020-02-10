---
title: Настройка и администрирование средства разбиения на слова и парадигматические модули для поиска | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- languages [full-text search]
- full-text search [SQL Server], stemmers
- linguistic analysis [full-text search]
- full-text indexes [SQL Server], linguistic analysis
- full-text search [SQL Server], word breakers
- default full-text language option
- stemmers [full-text search]
- conjugating verbs [full-text search]
- word breakers [full-text search]
ms.assetid: d4bdd16b-a2db-4101-a946-583d1c674229
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: eaa80c71dcc58cbd780a664d2466a3bf3cec2a4c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66011543"
---
# <a name="configure-and-manage-word-breakers-and-stemmers-for-search"></a>Настройка и управление средством разбиения на слова и парадигматические модули для поиска
  Средства разбиения по словам и парадигматические модули выполняют лингвистический анализ данных, проходящих полнотекстовое индексирование. Лингвистический анализ предусматривает поиск границ слов (разделение слов) и спряжение глаголов (выделение основы). Средства разбиения по словам и парадигматические модули являются уникальными для своих языков. У разных языков правила лингвистического анализа различаются. Для данного языка *средство разбиения по словам* определяет слова по границам слов согласно лексическим правилам языка. Каждое слово (называемое также *токеном*) вставляется в полнотекстовый индекс с использованием сжатого представления для уменьшения его размера. 
  *Парадигматический модуль* создает словоформы определенного слова на основании правил этого языка (например, "выполняется", "выполнялся" и "выполняющийся" являются различными формами слова "выполняться").  
  
 Средства разбиения по словам для каждого языка позволяют получать более точные термы для этого языка. Если имеется средство разбиения по словам для группы языков, но для конкретного языка, входящего в эту группу, его нет, используется основной язык. Например, для обработки франко-канадского текста используется средство разбиения по словам для французского языка. Если для определенного языка отсутствует средство разбиения по словам, используется нейтральное средство разбиения по словам. В случае нейтрального средства разбиения по словам слова разделяются по нейтральным символам, таким как пробелы и знаки препинания.  
  
##  <a name="register"></a>Регистрация разделителей слов  
 Для использования средств разбиения по словам определенного языка необходимо выполнить их регистрацию. Для зарегистрированных средств разбиения по словам, связанных лингвистических ресурсов — парадигматические модули, пропускаемые слова (стоп-слова) и файлы тезауруса, также становятся доступными для полнотекстового индексирования и выполнения запросов. Чтобы просмотреть список языков и средств разбиения по словам, зарегистрированных в настоящее время в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], используйте следующую инструкцию [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
 SELECT * FROM sys.fulltext_languages  
  
 При добавлении, удалении или изменении средства разбиения по словам следует обновить список кодов локалей, поддерживаемых в Microsoft Windows для полнотекстового индексирования и для выполнения запросов. Дополнительные сведения см. в статье [Просмотр или изменение зарегистрированных фильтры и разделители слов](view-or-change-registered-filters-and-word-breakers.md).  
  
##  <a name="default"></a>Задание параметра языка Full-Text по умолчанию  
 Для локализованной версии программа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] устанавливает `default full-text language` параметр на язык сервера, если существует соответствующее совпадение. Для нелокализованной версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметр `default full-text language` по умолчанию имеет значение, соответствующее английскому языку.  
  
 При создании или изменении полнотекстового индекса для каждого отдельного полнотекстового индексированного столбца можно указать отдельный язык. Если для столбца не указан язык, по умолчанию используется значение параметра конфигурации `default full-text language`.  
  
> [!NOTE]  
>  Если в запросе не задан параметр LANGUAGE, то все столбцы, приведенные в предложении функции полнотекстового запроса, должны использовать один и тот же язык. Язык столбца с полнотекстовым индексированием, к которому выполняется запрос, определяет правила лингвистического анализа для аргументов предикатов полнотекстового запроса ([CONTAINS](/sql/t-sql/queries/contains-transact-sql) и [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)) и функций ([CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) и [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql)).  
  
##  <a name="lang"></a>Выбор языка для индексированного столбца  
 При создании полнотекстового индекса рекомендуется указывать язык для каждого индексируемого столбца. Если для столбца язык не задан, то используется язык системы по умолчанию. Язык столбца определяет, какое средство разбиения по словам и какой парадигматический модуль используется для индексирования этого столбца. Кроме того, файл тезауруса этого языка будет использоваться полнотекстовыми запросами к столбцу.  
  
 При выборе языка столбца в процессе создания полнотекстового индекса следует учитывать несколько факторов. Они связаны со способом, которым текст размечается на лексемы и затем индексируется средством полнотекстового поиска. Дополнительные сведения см. в разделе [Выбор языка при создании полнотекстового индекса](choose-a-language-when-creating-a-full-text-index.md).  
  
 **Просмотр языка средства разбиения по словам для столбца**  
  
-   [Управление полнотекстовыми индексами](../indexes/indexes.md)  
  
-   [sys. fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
    ```  
    SELECT 'language_id' AS "LCID" FROM sys.fulltext_index_columns;  
    ```  
  
##  <a name="info"></a>Получение сведений о разделителях слов  
 **Просмотр результатов разметки для сочетания "средство разбиения по словам", тезауруса и списка стоп-слов**  
  
-   [sys. dm_fts_parser &#40;&#41;Transact-SQL ](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql).  
  
 **Возвращение сведения о зарегистрированных средствах разбиения по словам**  
  
-   [sp_help_fulltext_system_components &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql)  
  
##  <a name="tshoot"></a>Устранение ошибок превышения времени ожидания при разбиении по словам  
 Ошибка, связанная с превышением времени ожидания при разбиении по словам, может возникать в разных ситуациях. Дополнительные сведения о таких ситуациях и соответствующих действиях см. в разделе [MSSQLSERVER_30053](../errors-events/mssqlserver-30053-database-engine-error.md).  
  
##  <a name="impact"></a>Основные сведения о влиянии новых разделителей слов  
 Обычно каждая версия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] включает новые средства разбиения по словам, которые имеют лучшие лингвистические правила и более точны, чем прежние. Новые средства разбиения по словам могут вести себя немного не так, как средства разбиения по словам в полнотекстовых индексах, импортированных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это важно, если полнотекстовый каталог был импортирован при обновлении базы данных до текущей версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Один или несколько языков, используемых полнотекстовыми индексами в полнотекстовом каталоге, могут быть связаны с новыми средствами разбиения по словам. Дополнительные сведения см. в разделе [Обновление полнотекстового поиска](upgrade-full-text-search.md).  
  
 Полный список всех средств разбиения по словам см. в статье [sys.fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql).  
  
## <a name="see-also"></a>См. также:  
 [ALTER FULLTEXT INDEX &#40;&#41;Transact-SQL](/sql/t-sql/statements/alter-fulltext-index-transact-sql)   
 [Создание ПОЛНОТЕКСТОВОГО индекса &#40;&#41;Transact-SQL](/sql/t-sql/statements/create-fulltext-index-transact-sql)   
 [sp_fulltext_service &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-service-transact-sql)   
 [sys. fulltext_languages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql)   
 [Настройка стоп-слова и списков для полнотекстового поиска и управление ими](configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [Обновление полнотекстового поиска](upgrade-full-text-search.md)  
  
  
