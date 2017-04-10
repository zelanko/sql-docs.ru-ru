---
title: "Определение связи логических записей между статьями таблиц слияния | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "логические записи репликации слиянием [репликация SQL Server]"
  - "статьи [репликация SQL Server], логические записи"
  - "логические записи [репликация SQL Server]"
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Определение связи логических записей между статьями таблиц слияния
  В данном разделе описывается процесс определения связи логических записей между статьями таблиц слияния в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 Репликация слиянием позволяет определить связь между связанными строками в различных таблицах. Эти строки затем могут быть обработаны во время синхронизации как элементы транзакции. Логическая запись может быть определена между двумя статьями независимо от наличия связи фильтров соединения между ними. Дополнительные сведения см. в разделе [изменения группы связанных строк с логическими записями](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения связи логических записей между статьями таблиц слияния используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Если добавление, изменение или удаление логической записи выполняется после инициализации подписок на публикацию, следует создать новый моментальный снимок и повторно инициализировать все подписки после внесения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Определение логических записей в **Добавить соединение** диалоговое окно доступно в мастере создания публикаций и **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения об использовании мастера и о доступе к диалоговому окну см. в разделе [Создать публикацию](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Логические записи могут определяться в диалоговом окне **Добавление соединения** , только если они применяются к фильтру соединения в публикации слиянием и если публикация соответствует требованиям для использования предварительно вычисляемых секций. Чтобы определить логические записи, которые не применяются к фильтрам соединения, и чтобы установить обнаружение и разрешение конфликтов на уровне логических записей, следует использовать хранимые процедуры.  
  
#### Определение связи логических записей  
  
1.  На **Фильтрация строк таблицы** страницы мастера публикации или **Фильтрация строк** страницы **Свойства публикации — \< публикация>** выберите фильтр строк в **Отфильтрованные таблицы** области.  
  
     Связь логических записей ассоциирована с фильтром соединения, который расширяет фильтр строк. Поэтому необходимо определить фильтр строк, прежде чем можно будет расширить фильтр с помощью фильтра соединения и применить связь логических записей. После того как определен один фильтр соединения, можно расширить этот фильтр соединения с помощью еще одного фильтра соединения. Дополнительные сведения об определении фильтров соединения см. в разделе [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Щелкните **Добавить**и выберите **Добавить соединение для расширения выбранного фильтра**.  
  
3.  Определите фильтр соединения в диалоговом окне **Добавление соединения** , а затем установите флажок **Логическая запись**.  
  
4.  При работе в **Свойства публикации — \< публикация>** диалоговом нажмите кнопку **ОК** Сохранить и закрыть диалоговое окно.  
  
#### Удаление связи логических записей  
  
-   Удалите лишь связь логических записей или удалите и связь логических записей, и ассоциированный с ней фильтр соединения.  
  
     Чтобы удалить только связь логических записей.  
  
    1.  На **Фильтрация строк** страница мастера создания публикаций или **Фильтрация строк** Страница **Свойства публикации — \< публикации>** установите флажок фильтр соединения, ассоциированный со связью логических записей в **Отфильтрованные таблицы** панели, а затем щелкните **Изменить**.  
  
    2.  В диалоговом окне **Изменить соединение** снимите флажок **Логическая запись**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Чтобы удалить связь логических записей и фильтр соединения, ассоциированный с этой связью, выполните следующие действия.  
  
    -   На **Фильтрация строк** страницы мастера публикации или **Свойства публикации — \< публикация>** диалоговое окно, выберите фильтр в **Отфильтрованные таблицы** панели, а затем щелкните **Удалить**. Если удаляемый фильтр соединения расширен за счет других фильтров, эти фильтры также будут удалены.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью хранимых процедур репликации можно программно задать связь логических записей между статьями.  
  
#### Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Если публикация содержит всех статей, которые фильтруются, выполнение [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), и обратите внимание на значение **use_partition_groups** в результирующем наборе.  
  
    -   Если значение равно **1**, то предварительно вычисляемые секции уже используются.  
  
    -   Если значение равно **0**, затем выполните [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) на издателе в базе данных публикации. Укажите значение **use_partition_groups** для **@property** и значение **true** для **@value**.  
  
        > [!NOTE]  
        >  Если публикация не поддерживает предварительно вычисляемые секции, то логические записи использовать нельзя. Дополнительные сведения см. в разделе Требования к использованию предварительно вычисляемых секций в разделе [оптимизации параметризованных фильтров производительности с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md).  
  
    -   Если это значение NULL, то необходимо запустить агент моментальных снимков для создания исходного моментального снимка для публикации.  
  
2.  Если статьи, составляющие логические записи не существуют, выполните [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) на издателе в базе данных публикации. Укажите один из приведенных ниже параметров определения и распознавания конфликтов в логической записи.  
  
    -   Для обнаружения и разрешения конфликтов, возникающих в связанных строках логической записи, укажите значение **true** для **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution**.  
  
    -   Чтобы использовать стандартные строки столбец уровня или обнаружение и разрешение конфликтов, укажите значение **false** для **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution**, который используется по умолчанию.  
  
3.  Повторите шаг 2 для каждой статьи, которая содержит логическую запись. Необходимо использовать в каждой статье логической записи одинаковые параметры определения и разрешения конфликтов. Дополнительные сведения см. в статье [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/detecting-and-resolving-conflicts-in-logical-records.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Укажите **@publication**, имя одной статьи в связи для **@article**, имя второй статьи для **@join_articlename**, имя отношения **@filtername**, предложение, которое определяет связь между двумя статьями для **@join_filterclause**, тип соединения для **@join_unique_key** и одно из следующих значений для **@filter_type**:  
  
    -   **2** -определяет логическую связь.  
  
    -   **3** -определяет логическую связь с фильтром соединения.  
  
    > [!NOTE]  
    >  Фильтр соединения не используется, направление связи между двумя статьями несущественно.  
  
5.  Повторите шаг 2 для всех оставшихся связей логических записей в публикации.  
  
#### Изменение способа определения и разрешения конфликтов логических записей  
  
1.  Для определения и разрешения конфликтов, возникающих в связанных строках логической записи, выполните следующие действия.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **logical_record_level_conflict_detection** для **@property** и значение **true** для **@value**. Укажите значение **1** для **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **logical_record_level_conflict_resolution** для **@property** и значение **true** для **@value**. Укажите значение **1** для **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
2.  Для использования стандартного метода определения и разрешения конфликтов уровня строки и столбца выполните следующие действия.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **logical_record_level_conflict_detection** для **@property** и значение **false** для **@value**. Укажите значение **1** для **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **logical_record_level_conflict_resolution** для **@property** и значение **false** для **@value**. Укажите значение **1** для **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
#### Удаление связи логических записей  
  
1.  На издателе в базе данных публикации выполните приведенный ниже запрос для получения сведений обо всех связях логических записей, определенных для указанной публикации:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     Запомните имя удаляемой связи логических записей, содержащееся в столбце **filtername** результирующего набора.  
  
    > [!NOTE]  
    >  Этот запрос возвращает те же сведения, что [sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md)однако системная хранимая процедура только возвращает сведения о связи логических записей, которые являются также фильтрами соединения.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md). Укажите параметр **@publication**, имя одной из статей в связи в качестве значения параметра **@article**, а также имя связи из шага 1 в качестве значения параметра **@filtername**.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В этом примере разрешается использование предварительно вычисляемых секций в существующей публикации и создается логическая запись, в которую входят две новые статьи для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
> [!NOTE]  
>  Репликация слиянием позволяет указывать, что конфликты должны отслеживаться и разрешаться на уровне логических записей, но эти параметры нельзя задать с помощью объектов RMO.  
  
#### Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса, задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> свойству <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, задайте для него значение <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Если статьи, которые должны составить логическую запись не существует, создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeArticle> класса и задайте следующие свойства:  
  
    -   Имя статьи для <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Имя публикации для <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   (Необязательно) Если статья отфильтрована горизонтально, укажите предложение фильтра строк для <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> свойство. Используйте это свойство для определения статического или параметризованного фильтра строк. Дополнительные сведения см. в статье [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
     Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Вызов <xref:Microsoft.SqlServer.Replication.Article.Create%2A> метод.  
  
7.  Повторите шаги 5 и 6 для каждой статьи, составляющей логическую запись.  
  
8.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> класса, чтобы определить связь логических записей между статьями. Затем установите следующие свойства.  
  
    -   Имя дочерней статьи в связи логических записей для <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> свойство.  
  
    -   Имя существующей, родительской статьи в связи логических записей для <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> свойство.  
  
    -   Имя для связи логических записей для <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> свойство.  
  
    -   Выражение, определяющее связь для <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> свойство.  
  
    -   Значение <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> для <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> свойство. Если связь логических записей является также фильтром соединения, укажите значение <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> для этого свойства. Дополнительные сведения см. в разделе [изменения группы связанных строк с логическими записями](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Вызов <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> метод в объект, представляющий дочерней статьи в связи. Передайте <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> из шага 8, чтобы определить связь.  
  
10. Повторите шаги 8 и 9 для каждой оставшейся связи логических записей в публикации.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере создается логическая запись, составленная из двух новых статей для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-csharp[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## См. также:  
 [Определение и изменение фильтра соединения между статьями публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Определение и изменение статического строкового фильтра](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [Изменения группирования связанных строк с логическими записями](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/optimize-parameterized-filter-performance-with-precomputed-partitions.md)   
 [Изменения группирования связанных строк с логическими записями](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  