---
title: Критические изменения в полнотекстовом поиске | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], breaking changes
- full-text catalogs [SQL Server], breaking changes
- breaking changes [full-text search]
- full-text indexes [SQL Server], breaking changes
ms.assetid: c55a6748-e5d9-4fdb-9a1f-714475a419c5
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 45b13c29af6a9c5e82533a4b66213d1cb1b9dd15
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62787762"
---
# <a name="breaking-changes-to-full-text-search"></a>Критические изменения в полнотекстовом поиске
  В этом разделе описываются критические изменения полнотекстового поиска. Эти изменения могут нарушать работу приложений, скриптов или механизмов, основанных на более ранних версиях [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. При обновлении могут возникнуть следующие проблемы. Дополнительные сведения см. в разделе [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
## <a name="breaking-changes-in-full-text-search-in-includesssql14includessssql14-mdmd"></a>Критические изменения полнотекстового поиска в [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Сведения будут доступны позже.  
  
## <a name="breaking-changes-in-full-text-search-in-includesssql11includessssql11-mdmd"></a>Критические изменения полнотекстового поиска в [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="collation-changed-for-name-column-in-sysfulltext_languages"></a>Изменены параметры сортировки для столбца «name» в представлении sys.fulltext_languages  
 Параметры сортировки для языка столбца **name** в представлении каталога [sys.fulltext_languages (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql) изменены с фиксированных параметров сортировки базы данных Resource на параметры сортировки по умолчанию, выбранные для экземпляра [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Это изменение позволяет сравнивать значения в столбце **name** при соединении представления [sys.syslanguages (Transact-SQL)](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) с представлением **sys.fulltext_languages**. Например, можно создать запрос, выдающий список всех баз данных, у которых язык полнотекстового поиска по умолчанию отличается от языка базы данных по умолчанию.  
  
## <a name="breaking-changes-in-full-text-search-in-sql-server-2008"></a>Критические изменения полнотекстового поиска в SQL Server 2008  
 Следующие критические изменения были внесены в компонент полнотекстового поиска (Full-Text Search) между выпуском [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] и выпуском [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] (и последующими версиями).  
  
|Компонент|Сценарий|SQL Server 2005.|SQL Server 2008 и последующие версии|  
|-------------|--------------|---------------------|----------------------------------------|  
|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) с определяемыми пользователем типами (UDT)|Полнотекстовый ключ — это определяемый пользователем тип [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], например `MyType = char(1)`.|Возвращаемый ключ имеет тип, назначенный определяемому пользователем типу.<br /><br /> В этом примере это будет **char (1)**.|Возвращаемый ключ имеет определяемый пользователем тип. В этом примере это будет **MyType**.|  
|параметр *top_n_by_rank* (операторов CONTAINSTABLE и [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) [!INCLUDE[tsql](../includes/tsql-md.md)] )|*top_n_by_rank* запросы, использующие значение 0 в качестве параметра.|Завершается с сообщением об ошибке, указывающим на то, что значение должно быть больше нуля.|Завершается успешно, возвращая 0 строк.|  
|Функции CONTAINSTABLE и **ItemCount**|Удаление строк из базовой таблицы перед передачей изменений компоненту MSSearch.|Функция CONTAINSTABLE возвращает фантомную запись. **ItemCount** не изменяется.|Функция CONTAINSTABLE не возвращает фантомных записей.|  
|**ItemCount**|Таблица содержит документы или типы столбцов, имеющие значение NULL.|В дополнение к индексированным документам в значении **ItemCount** учитываются документы, имеющие значение null или имеющие тип NULL.|Только индексированные документы учитываются в значении **ItemCount** .|  
|**ItemCount** каталога|Столбец BLOB с расширением NULL.|Он учитывается в **ItemCount** каталога|Он не учитывается в **ItemCount** каталога.|  
|**UniqueKeyCount**|Запрос к числу уникальных ключей из каталога, например две таблицы (Table1 и Table2), каждый из которых имеет три слова: word1, слово2 и word3.|**Uniquekeycount** = 9. В следующей таблице показано, как получено это значение.<br /><br /> таблица1 = 3<br /><br /> EOF для полнотекстового индекса таблицы1 = 1<br /><br /> таблица2 = 3<br /><br /> EOF для полнотекстового индекса таблицы2 = 1<br /><br /> полнотекстовый каталог = 1|Для каждой таблицы **uniquekeycount** — количество различных ключевых слов + 1 (0xFF).  Это не обрабатывает слова в > 1 doc как новый уникальный ключ.<br /><br /> Для каталога **uniquekeycount** является суммой **uniquekeycount** каждой таблицы в каталоге. Одинаковые слова, содержащиеся в различных таблицах, считаются уникальными ключами. В данном случае число уникальных ключей равно 8.|  
|параметр уровня сервера «предварительное **Вычисление ранга** »|Оптимизация производительности запросов FREETEXTTABLE.|Если параметр имеет значение 1, запросы FREETEXTTABLE, заданные с помощью *top_n_by_rank* , используют данные предварительно вычисленного ранга, хранящиеся в полнотекстовых каталогах.|Не поддерживается.|  
|[sp_fulltext_pendingchanges](/sql/relational-databases/system-stored-procedures/sp-fulltext-pendingchanges-transact-sql) при обновлении ключевого столбца|Обновляется полнотекстовый ключевой столбец на одной строке в таблице, содержащей две строки, а затем выполняется хранимая процедура sp_fulltext_pendingchanges.|Отображаются обе строки.|Отображается только одна строка.|  
|Встроенные функции|Встроенные функции с полнотекстовым оператором|Возвращает сообщение об ошибке.|Возвращает соответствующие строки.|  
|[sp_fulltext_database, хранимая процедура](/sql/relational-databases/system-stored-procedures/sp-fulltext-database-transact-sql)|Включение и отключение полнотекстового поиска при помощи хранимой процедуры using sp_fulltext_database.|Результаты для полнотекстовых запросов не возвращаются. Если полнотекстовый поиск в базе данных отключен, полнотекстовые операции запрещены.|Возвращает результаты полнотекстовых запросов. Полнотекстовые операции разрешены, даже если полнотекстовый поиск в базе данных отключен.|  
|Стоп-слова, зависящие от локали|Запрашивает специальные разновидности родительского языка, такие как бельгийская французская и Канадская французская.|Характерные для локальных запросов варианты обрабатываются компонентами (разделители слов, парадигматические модули и прекращенные слова) своего родительского языка. Например, компоненты для языка «Французский (Франция)» используются для синтаксического анализа языка «Французский (Бельгия)».|Стоп-слова для каждого идентификатора локали (LCID) должны добавляться явным образом. В частности, может потребоваться указать LCID для Бельгии, Канады и Франции.|  
|Добавление парадигм в тезаурус|Применение тезауруса и словоформы (добавление парадигм).|После добавления слова в тезаурус для него автоматически создается парадигма.|Если при расширении необходима парадигматическая форма, ее необходимо добавить явным образом.|  
|Путь и файловая группа полнотекстового каталога|Работа с полнотекстовыми каталогами.|Каждый полнотекстовый каталог имеет физический путь и входит в файловую группу. Он рассматривается как файл базы данных.|Полнотекстовый каталог является виртуальным объектом и не входит в файловую группу. Полнотекстовый каталог — это логическое понятие, обозначающее группу полнотекстовых индексов.<br /><br /> Примечание. [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] инструкции DDL, указывающие полнотекстовые каталоги, работают правильно.|  
|[sys.fulltext_catalogs](/sql/relational-databases/system-catalog-views/sys-fulltext-catalogs-transact-sql)|Использование в этом представлении каталога столбцов path, data_space_id и file_id.|Указанные столбцы возвращают конкретные значения.|Указанные столбцы возвращают значение NULL, поскольку теперь полнотекстовый каталог находится не в файловой системе.|  
|[sys.sysfulltextcatalogs](/sql/relational-databases/system-compatibility-views/sys-sysfulltextcatalogs-transact-sql)|Использование в этой устаревшей системной таблице столбца PATH.|Возвращает путь к полнотекстовому каталогу в файловой системе.|Возвращает значение NULL, поскольку полнотекстовый каталог теперь находится не в файловой системе.|  
|[sp_help_fulltext_catalogs](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-transact-sql)<br /><br /> [sp_help_fulltext_catalogs_cursor](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalogs-cursor-transact-sql)|Использование в этих устаревших хранимых процедурах столбца PATH.|Возвращает путь к полнотекстовому каталогу в файловой системе.|Возвращает значение NULL, поскольку полнотекстовый каталог теперь находится не в файловой системе.|  
|[sp_help_fulltext_catalog_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-catalog-components-transact-sql)|Использование хранимой процедуры sp_help_fulltext_catalog_components.|Возвращает список всех компонентов (фильтров, разделителей слов и обработчиков протоколов), используемых для всех полнотекстовых каталогов в текущей базе данных.|Возвращает пустые строки.|  
|[DATABASEPROPERTYEX](/sql/t-sql/functions/databasepropertyex-transact-sql)|Использование свойства **IsFullTextEnabled** .|Параметр **IsFullTextEnabled** указывает, включен ли полнотекстовый поиск в заданной базе данных.|Значение этого столбца не учитывается. Полнотекстовый поиск всегда включен для пользовательских баз данных.|  
  
## <a name="see-also"></a>См. также:  
 [Изменения в работе полнотекстового поиска](../relational-databases/search/full-text-search.md)   
 [Полнотекстовый поиск](../relational-databases/search/full-text-search.md)  
  
  
