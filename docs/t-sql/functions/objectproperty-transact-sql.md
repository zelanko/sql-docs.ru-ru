---
title: "OBJECTPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OBJECTPROPERTY
- OBJECTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- displaying schema-scoped object information
- viewing schema-scoped object information
- OBJECTPROPERTY function
- schema-scoped objects [SQL Server]
- objects [SQL Server], schema-scoped
ms.assetid: 27569888-f8b5-4cec-a79f-6ea6d692b4ae
caps.latest.revision: 81
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0ee3350b200f0f42203a89d06ddb587b0792ee18
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="objectproperty-transact-sql"></a>OBJECTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает данные об объектах области схемы в текущей базе данных. Список объектов области схемы см. в разделе [sys.objects &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md). Эта функция не может использоваться для объектов вне области схемы, таких как триггеры языка определения данных (DDL) и уведомления о событиях.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
OBJECTPROPERTY ( id , property )   
```  
  
## <a name="arguments"></a>Аргументы  
 *идентификатор*  
 Выражение, которое представляет идентификатор объекта в текущей базе данных. *Идентификатор* — **int** и предполагается, что объект схемы в текущем контексте базы данных.  
  
 *Свойство*  
 Выражение, которое представляет сведения, которые необходимо вернуть для объекта, указанного параметром *идентификатор*. *свойство* может принимать одно из следующих значений.  
  
> [!NOTE]  
>  Если не указано иное, значение NULL возвращается, когда *свойство* не является допустимым именем свойства, *идентификатор* не является допустимым Идентификатором объекта, *идентификатор* является неподдерживаемым типом объекта для указанного *свойство*, или вызывающий объект не имеет разрешения на просмотр метаданных объекта.  
  
|Имя свойства|Тип объекта|Описание и возвращаемые значения|  
|-------------------|-----------------|-------------------------------------|  
|CnstIsClustKey|Ограничение|Ограничение PRIMARY KEY с кластеризованным индексом.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsColumn|Ограничение|Ограничение CHECK, DEFAULT или FOREIGN KEY на одиночный столбец.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsDeleteCascade|Ограничение|Ограничение FOREIGN KEY с параметром ON DELETE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsDisabled|Ограничение|Отключенное ограничение.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsNonclustKey|Ограничение|Ограничение PRIMARY KEY или UNIQUE с некластеризованным индексом.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsNotRepl|Ограничение|Ограничение определено с помощью ключевых слов NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsNotTrusted|Ограничение|Ограничение включено без проверки существующих строк, поэтому может быть действительным не для всех строк.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|CnstIsUpdateCascade|Ограничение|Ограничение FOREIGN KEY с параметром ON UPDATE CASCADE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsAfterTrigger|Триггер|Триггер AFTER.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsAnsiNullsOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Установка ANSI_NULLS во время создания.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsDeleteTrigger|Триггер|Триггер DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsFirstDeleteTrigger|Триггер|Первый триггер, который срабатывает при применении к таблице инструкции DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsFirstInsertTrigger|Триггер|Первый триггер, который срабатывает при применении к таблице инструкции INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsFirstUpdateTrigger|Триггер|Первый триггер, который срабатывает при применении к таблице инструкции UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsInsertTrigger|Триггер|Триггер INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsInsteadOfTrigger|Триггер|Триггер INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsLastDeleteTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции DELETE для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsLastInsertTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции INSERT для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsLastUpdateTrigger|Триггер|Последний триггер, сработавший при выполнении инструкции UPDATE для таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsQuotedIdentOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Значение параметра QUOTED_IDENTIFIER на момент создания.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsStartup|Процедура|Процедура запуска.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsTriggerDisabled|Триггер|Триггер отключен.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsTriggerNotForRepl|Триггер|Триггер определен как NOT FOR REPLICATION.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsUpdateTrigger|Триггер|Триггер UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|ExecIsWithNativeCompilation|Процедура [!INCLUDE[tsql](../../includes/tsql-md.md)]|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Процедура компилируется в собственном коде.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**|  
|HasAfterTrigger|Таблица, представление|Таблица или представление с триггером AFTER.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|HasDeleteTrigger|Таблица, представление|Таблица или представление с триггером DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|HasInsertTrigger|Таблица, представление|Таблица или представление с триггером INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|HasInsteadOfTrigger|Таблица, представление|Таблица или представление с триггером INSTEAD OF.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|HasUpdateTrigger|Таблица, представление|Таблица или представление с триггером UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsAnsiNullsOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Указывается, что для параметра ANSI NULLS таблицы задано ON. Это означает, что результатом всех сравнений со значением NULL является UNKNOWN. Эта настройка относится ко всем выражениям в определении таблицы, включая вычисляемые столбцы и ограничения, в течение всего времени существования таблицы.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsCheckCnst|Любой объект области схемы|Ограничение CHECK.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsConstraint|Любой объект области схемы|Ограничение CHECK, DEFAULT или FOREIGN KEY единственного столбца на столбце или таблице.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsDefault|Любой объект области схемы|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Привязанное значение по умолчанию:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsDefaultCnst|Любой объект области схемы|Ограничение DEFAULT:<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsDeterministic|Функция, представление|Свойство детерминизма функции или представления.<br /><br /> 1 = детерминированная<br /><br /> 0 = недетерминированная|  
|IsEncrypted|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление|Указывает, что исходный текст инструкции модуля был преобразован в запутанный формат. Результат запутывания не виден непосредственно ни в одном представлении каталога [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Пользователи, не имеющие доступа к системным таблицам или файлам баз данных, не могут получить текст, подвергнутый запутыванию. Однако этот текст будет доступен пользователям, которые либо смогут обращаться к системным таблицам через [порт выделенного административного Соединения](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md) или непосредственный доступ к файлам базы данных. Кроме того, пользователь, имеющий возможность подключить отладчик к серверному процессу, сможет получить исходный текст процедуры из памяти во время выполнения.<br /><br /> 1 = зашифрована<br /><br /> 0 = не зашифрована<br /><br /> Базовый тип данных: **int**|  
|IsExecuted|Любой объект области схемы|Объект (представление, процедура, функция или триггер) может быть выполнен.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsExtendedProc|Любой объект области схемы|Расширенная процедура.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsForeignKey|Любой объект области схемы|Ограничение FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsIndexed|Таблица, представление|Таблица или представление, имеющие индекс.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsIndexable|Таблица, представление|Таблица или представление, на которых может быть создан индекс.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsInlineFunction|Функция|Встроенная функция.<br /><br /> 1 = встроенная функция<br /><br /> 0 = невстроенная функция|  
|IsMSShipped|Любой объект области схемы|Объект, созданный во время установки сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsPrimaryKey|Любой объект области схемы|Ограничение PRIMARY KEY.<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> NULL = не функция или идентификатор объекта недействителен.|  
|IsProcedure|Любой объект области схемы|Процедура.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsQuotedIdentOn|Функция [!INCLUDE[tsql](../../includes/tsql-md.md)], процедура [!INCLUDE[tsql](../../includes/tsql-md.md)], таблица, триггер [!INCLUDE[tsql](../../includes/tsql-md.md)], представление, ограничение CHECK, определение DEFAULT|Указывается, что параметр quoted identifier для объекта имеет значение ON. Это означает, что двойные кавычки разделяют идентификаторы во всех выражениях, участвующих в определении объекта.<br /><br /> 1 = включен;<br /><br /> 0 = выключен.|  
|IsQueue|Любой объект области схемы|Очередь компонента Service Broker<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsReplProc|Любой объект области схемы|Процедура репликации.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsRule|Любой объект области схемы|Привязанное правило.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsScalarFunction|Функция|Скалярная функция.<br /><br /> 1 = скалярная функция<br /><br /> 0 = нескалярная функция|  
|IsSchemaBound|Функция, представление|Привязанная к схеме функция или представление, созданные с помощью SCHEMABINDING.<br /><br /> 1 = привязана к схеме<br /><br /> 0 = не привязана к схеме.|  
|IsSystemTable|Таблица|Системная таблица.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsTable|Таблица|Таблица.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsTableFunction|Функция|Функция с табличным значением.<br /><br /> 1 = функция с табличным значением<br /><br /> 0 = функция не с табличным значением|  
|IsTrigger|Любой объект области схемы|Триггер.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsUniqueCnst|Любой объект области схемы|Ограничение UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsUserTable|Таблица|Пользовательская таблица.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|IsView|Просмотр|Представление.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|OwnerId|Любой объект области схемы|Владелец объекта.<br /><br /> **Примечание:** владелец схемы не обязательно является владельцем объекта. Например, дочерние объекты (такие, у которых *parent_object_id* является не нулевым) всегда будет возвращать тот же идентификатор владельца, что и родительский объект.<br /><br /> Nonnull = идентификатор пользователя базы данных владельца объекта.|  
|TableDeleteTrigger|Таблица|У таблицы есть триггер DELETE.<br /><br /> > 1 = идентификатор первого триггера указанного типа.|  
|TableDeleteTriggerCount|Таблица|В таблице имеется указанное число триггеров DELETE.<br /><br /> >0 = количество триггеров DELETE.|  
|TableFullTextMergeStatus|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Определяет, участвует ли в настоящий момент полнотекстовый индекс для таблицы в процессе слияния.<br /><br /> 0 = для таблицы отсутствует полнотекстовый индекс, либо индекс не находится в процессе слияния.<br /><br /> 1 = полнотекстовый индекс находится в процессе слияния.|  
|TableFullTextBackgroundUpdateIndexOn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> В таблице имеется включенный полнотекстовый индекс фонового обновления (отслеживание автозамен).<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE|  
|TableFulltextCatalogId|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор полнотекстового каталога, в котором находятся данные полнотекстового индекса для таблицы.<br /><br /> Не 0 = идентификатор полнотекстового каталога, связанный с уникальным индексом, идентифицирующим строки в полнотекстовой индексированной таблице.<br /><br /> 0 = таблица не имеет полнотекстового индекса.|  
|TableFulltextChangeTrackingOn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Для таблицы включено полнотекстовое отслеживание изменений.<br /><br /> 1 = TRUE<br /><br /> 0 = FALSE|  
|TableFulltextDocsProcessed|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество строк, обработанных с начала полнотекстового индексирования. В таблице, которая индексируется для полнотекстового поиска, все столбцы одной строки рассматриваются как часть единого индексируемого документа.<br /><br /> 0 = отсутствие активного сканирования или полнотекстовое индексирование закончено.<br /><br /> > 0 = один из следующих (A или B): A) число документов, обработанных операциями вставки или обновления операций с начала полного, добавочного или ручного заполнения с отслеживанием изменений. (Б) число строк, обрабатываемых insert или операции обновления с момента включения отслеживания изменений при фоновом заполнении индекса, изменения схемы полнотекстового индекса, полнотекстовый каталог перестроен или экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] перезапуск и т. д.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.<br /><br /> Это свойство не обеспечивает наблюдение за удаленными строками или их подсчет.|  
|TableFulltextFailCount|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество строк, для которых полнотекстовый поиск не выявил индекса.<br /><br /> 0 = Заполнение завершено.<br /><br /> > 0 = один из следующих (A или B): A) число документов, не индексированных с начала заполнения отслеживания изменений полного, постепенного или ручного обновления. (Б) для отслеживания изменений при фоновом режиме обновления индекса, количество строк, не индексированных с начала заполнения или перезапуска заполнения. Это может быть вызвано изменением схемы, перестроением каталога, перезапуском сервера и т. д.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.|  
|TableFulltextItemCount|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество строк, для которых было успешно выполнено полнотекстовое индексирование.|  
|TableFulltextKeyColumn|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Идентификатор столбца, связанного с уникальным индексом одного столбца, который участвует в определении полнотекстового индекса:<br /><br /> 0 = таблица не имеет полнотекстового индекса.|  
|TableFulltextPendingChanges|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Количество ожидающих отслеженных изменений к обработке.<br /><br /> 0 = Отслеживание изменений не включено.<br /><br /> NULL = Таблица не содержит полнотекстового индекса.|  
|TableFulltextPopulateStatus|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> 0 = Бездействует.<br /><br /> 1 = Производится полное заполнение.<br /><br /> 2 = Производится добавочное заполнение.<br /><br /> 3 = Выполняется распространение отслеженных изменений.<br /><br /> 4 = выполняется индексирование фонового обновления (например автоматическое отслеживание изменений).<br /><br /> 5 = Полнотекстовое индексирование приостановлено, или не хватает ресурсов на его выполнение.|  
|TableHasActiveFulltextIndex|Таблица|**Область применения**: начиная с [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица имеет активный полнотекстовый индекс.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasCheckCnst|Таблица|Таблица имеет ограничение CHECK.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasClustIndex|Таблица|Таблица имеет кластеризованный индекс.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasDefaultCnst|Таблица|Таблица имеет ограничение DEFAULT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasDeleteTrigger|Таблица|У таблицы есть триггер DELETE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasForeignKey|Таблица|Таблица имеет ограничение FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasForeignRef|Таблица|На таблицу есть ссылки по ограничению FOREIGN KEY.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasIdentity|Таблица|Таблица содержит столбец идентификаторов.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasIndex|Таблица|Таблица имеет индекс какого-либо типа.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasInsertTrigger|Таблица|Объект имеет триггер INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasNonclustIndex|Таблица|Таблица содержит некластеризованный индекс.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasPrimaryKey|Таблица|Таблица содержит первичный ключ.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasRowGuidCol|Таблица|Таблица содержит свойство ROWGUIDCOL для **uniqueidentifier** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasTextImage|Таблица|Таблица имеет **текст**, **ntext**, или **изображения** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasTimestamp|Таблица|Таблица имеет **timestamp** столбца.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasUniqueCnst|Таблица|Таблица имеет ограничение UNIQUE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasUpdateTrigger|Таблица|Объект содержит триггер UPDATE.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableHasVarDecimalStorageFormat|Таблица|Таблица включается для **vardecimal** формат хранения.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableInsertTrigger|Таблица|Таблица содержит триггер INSERT.<br /><br /> > 1 = идентификатор первого триггера указанного типа.|  
|TableInsertTriggerCount|Таблица|В таблице имеется указанное число триггеров INSERT.<br /><br /> >0 = количество триггеров INSERT.|  
|TableIsFake|Таблица|Таблица реально не существует. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] материализует ее внутренним образом по запросу.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableIsLockedOnBulkLoad|Таблица|Таблица заблокирована из-за **bcp** или заданием BULK INSERT.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|TableIsMemoryOptimized|Таблица|**Область применения**: начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Таблица, оптимизированная для памяти<br /><br /> 1 = True<br /><br /> 0 = False.<br /><br /> Базовый тип данных: **int**<br /><br /> Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).|  
|TableIsPinned|Таблица|Таблица закреплена для хранения в кэше данных.<br /><br /> 0 = False.<br /><br /> Эта функция не поддерживается в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и в более поздних версиях.|  
|TableTextInRowLimit|Таблица|Максимальное количество байтов, допустимое для текста в строке.<br /><br /> 0, если не установлен параметр текст в строке.|  
|TableUpdateTrigger|Таблица|Таблица содержит триггер UPDATE.<br /><br /> > 1 = идентификатор первого триггера указанного типа.|  
|TableUpdateTriggerCount|Таблица|В таблице имеется указанное число триггеров UPDATE.<br /><br /> >0 = количество триггеров UPDATE.|  
|TableHasColumnSet|Таблица|Таблица содержит набор столбцов.<br /><br /> 0 = False.<br /><br /> 1 = True<br /><br /> Дополнительные сведения см. в статье [Использование наборов столбцов](../../relational-databases/tables/use-column-sets.md).|  
|TableTemporalType|Таблица|**Область применения**: начиная с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Указывает тип таблицы.<br /><br /> 0 = нетемпоральные таблицы<br /><br /> 1 = Таблица журнала для таблицы с системным управлением версиями<br /><br /> 2 = временная таблица с системным управлением версиями|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **int**  
  
## <a name="exceptions"></a>Исключения  
 Возвращает значение NULL в случае ошибки или если участник не имеет разрешений для просмотра объекта.  
  
 Пользователь может просматривать только метаданные защищаемых объектов, которыми он владеет или на которые пользователю были предоставлены разрешения. Это значит, что встроенные функции, создающие метаданные (например, OBJECTPROPERTY), могут возвращать значение NULL, если у пользователя нет разрешения на доступ к объекту. Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="remarks"></a>Замечания  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Предполагается, что *object_id* находится в контексте текущей базы данных. Запрос, который ссылается на *object_id* в другой базе данных будут возвращать значение NULL или неправильные результаты. Например в следующем запросе текущий контекст базы данных является база данных master. [!INCLUDE[ssDE](../../includes/ssde-md.md)] Попытается вернуть значение свойства для указанного *object_id* в этой базе данных вместо базы данных, указанной в запросе. Запрос возвращает неверные результаты, так как представление `vEmployee` не находится в базе данных master.  
  
```  
USE master;  
GO  
SELECT OBJECTPROPERTY(OBJECT_ID(N'AdventureWorks2012.HumanResources.vEmployee'), 'IsView');  
GO  
```  
  
 OBJECTPROPERTY (*view_id*, 'IsIndexable') может потреблять значительные ресурсы компьютера, так как для вычисления свойства IsIndexable необходимы синтаксический анализ определения представления, нормализация и частичная оптимизация. Даже если свойство IsIndexable определяет, что таблицы или представления могут быть проиндексированы, фактическое создание индекса может завершиться ошибкой, если не выполняются требования к ключу индекса. Дополнительные сведения см. в разделе [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md).  
  
 OBJECTPROPERTY (*table_id*, 'TableHasActiveFulltextIndex') вернет значение 1 (true), если хотя бы один столбец таблицы был добавлен для индексирования. Заполнение полнотекстового индекса становится активным, как только для индексирования добавлен хотя бы один столбец.  
  
 После создания таблицы параметр QUOTED IDENTIFIER всегда сохраняется в метаданных таблицы со значением ON, даже если при создании таблицы для него было задано OFF. Поэтому OBJECTPROPERTY (*table_id*, 'IsQuotedIdentOn') всегда возвращает значение 1 (true).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-verifying-that-an-object-is-a-table"></a>A. Проверка того, что объект является таблицей  
 В следующем примере производится проверка, является ли `UnitMeasure` таблицей в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') = 1  
   PRINT 'UnitMeasure is a table.'  
ELSE IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') = 0  
   PRINT 'UnitMeasure is not a table.'  
ELSE IF OBJECTPROPERTY (OBJECT_ID(N'Production.UnitMeasure'),'ISTABLE') IS NULL  
   PRINT 'ERROR: UnitMeasure is not a valid object.';  
GO  
  
```  
  
### <a name="b-verifying-that-a-scalar-valued-user-defined-function-is-deterministic"></a>Б. Проверка того, что скалярная функция, определяемая пользователем, является детерминированной  
 В следующем примере проверяется ли определяемой пользователем скалярной функции `ufnGetProductDealerPrice`, который возвращает **money** , детерминированной.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT OBJECTPROPERTY(OBJECT_ID('dbo.ufnGetProductDealerPrice'), 'IsDeterministic');  
GO  
```  
  
 Результирующий набор показывает, что функция `ufnGetProductDealerPrice` не является детерминированной.  
  
 `-----`  
  
 `0`  
  
### <a name="c-finding-the-objects-that-belong-to-a-specific-schema"></a>В. Поиск объектов, принадлежащих определенной схеме  
 В следующем примере свойство `SchemaId` возвращает все объекты, которые принадлежат схеме `Production`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT name, object_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTY(object_id, N'SchemaId') = SCHEMA_ID(N'Production')  
ORDER BY type_desc, name;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-verifying-that-an-object-is-a-table"></a>Проверка того, что объект является таблицей D:  
 В следующем примере производится проверка, является ли `dbo.DimReseller` таблицей в базе данных [!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)].  
  
```  
-- Uses AdventureWorks  
  
IF OBJECTPROPERTY (OBJECT_ID(N'dbo.DimReseller'),'ISTABLE') = 1  
   SELECT 'DimReseller is a table.'  
ELSE   
   SELECT 'DimReseller is not a table.';  
GO  
```  
  
### <a name="e-finding-the-tables-that-belong-to-a-specific-schema"></a>Д. Поиск таблиц, принадлежащих определенной схеме  
 Следующий пример возвращает все таблицы в схеме dbo.  
  
```  
-- Uses AdventureWorks  
  
SELECT name, object_id, type_desc  
FROM sys.objects   
WHERE OBJECTPROPERTY(object_id, N'SchemaId') = SCHEMA_ID(N'dbo')  
ORDER BY type_desc, name;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [COLUMNPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/columnproperty-transact-sql.md)   
 [Функции метаданных &#40; Transact-SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECTPROPERTYEX &#40; Transact-SQL &#41;](../../t-sql/functions/objectpropertyex-transact-sql.md)   
 [ALTER AUTHORIZATION &#40; Transact-SQL &#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [TYPEPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/typeproperty-transact-sql.md)   
 [sys.Objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)  
  
  


