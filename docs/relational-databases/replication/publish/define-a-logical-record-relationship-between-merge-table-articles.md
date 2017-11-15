---
title: "Определение связи логических записей между статьями таблиц слияния | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merge replication logical records [SQL Server replication]
- articles [SQL Server replication], logical records
- logical records [SQL Server replication]
ms.assetid: ff847b3a-c6b0-4eaf-b225-2ffc899c5558
caps.latest.revision: "44"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b22b667a679c2dee3a87b0348170c793af0c9e1c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="define-a-logical-record-relationship-between-merge-table-articles"></a>Определение связи логических записей между статьями таблиц слияния
  В данном разделе описывается процесс определения связи логических записей между статьями таблиц слияния в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 Репликация слиянием позволяет определить связь между связанными строками в различных таблицах. Эти строки затем могут быть обработаны во время синхронизации как элементы транзакции. Логическая запись может быть определена между двумя статьями независимо от наличия связи фильтров соединения между ними. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
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
  
-   Если добавление, изменение или удаление логической записи выполняется после инициализации подписок на публикацию, следует создать новый моментальный снимок и повторно инициализировать все подписки после внесения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в статье [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Определите логические записи в диалоговом окне **Добавить соединение**, которое доступно в мастере создания публикаций и диалоговом окне **Свойства публикации — \<публикация>**. Дополнительные сведения об использовании мастера и доступе к этому диалоговому окну см. в статьях [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
 Логические записи могут определяться в диалоговом окне **Добавление соединения** , только если они применяются к фильтру соединения в публикации слиянием и если публикация соответствует требованиям для использования предварительно вычисляемых секций. Чтобы определить логические записи, которые не применяются к фильтрам соединения, и чтобы установить обнаружение и разрешение конфликтов на уровне логических записей, следует использовать хранимые процедуры.  
  
#### <a name="to-define-a-logical-record-relationship"></a>Определение связи логических записей  
  
1.  На странице **Фильтрация строк** таблицы мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<публикация>** выберите фильтр строк в области **Отфильтрованные таблицы**.  
  
     Связь логических записей ассоциирована с фильтром соединения, который расширяет фильтр строк. Поэтому необходимо определить фильтр строк, прежде чем можно будет расширить фильтр с помощью фильтра соединения и применить связь логических записей. После того как определен один фильтр соединения, можно расширить этот фильтр соединения с помощью еще одного фильтра соединения. Дополнительные сведения об определении фильтров соединения см. в разделе [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
2.  Щелкните **Добавить**и выберите **Добавить соединение для расширения выбранного фильтра**.  
  
3.  Определите фильтр соединения в диалоговом окне **Добавление соединения** , а затем установите флажок **Логическая запись**.  
  
4.  Если вы находитесь в диалоговом окне **Свойства публикации — \<публикация>**, нажмите кнопку **ОК**, чтобы сохранить изменения и закрыть диалоговое окно.  
  
#### <a name="to-delete-a-logical-record-relationship"></a>Удаление связи логических записей  
  
-   Удалите лишь связь логических записей или удалите и связь логических записей, и ассоциированный с ней фильтр соединения.  
  
     Чтобы удалить только связь логических записей.  
  
    1.  На странице **Фильтрация строк** мастера создания публикаций или странице **Фильтрация строк** диалогового окна **Свойства публикации — \<публикация>** выберите фильтр соединения, связанный с отношением логической записи, в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Изменить**.  
  
    2.  В диалоговом окне **Изменить соединение** снимите флажок **Логическая запись**.  
  
    3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
     Чтобы удалить связь логических записей и фильтр соединения, ассоциированный с этой связью, выполните следующие действия.  
  
    -   На странице **Фильтрация строк** мастера создания публикаций или в диалоговом окне **Свойства публикации — \<публикация>** выберите фильтр в области **Отфильтрованные таблицы**, а затем нажмите кнопку **Удалить**. Если удаляемый фильтр соединения расширен за счет других фильтров, эти фильтры также будут удалены.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 С помощью хранимых процедур репликации можно программно задать связь логических записей между статьями.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Если публикация содержит фильтруемые статьи, выполните хранимую процедуру [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)и проверьте значение параметра **use_partition_groups** в результирующем наборе.  
  
    -   Если значение равно **1**, то предварительно вычисляемые секции уже используются.  
  
    -   Если значение равно **0**, выполните хранимую процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md) на издателе в базе данных публикации. Задайте **use_partition_groups** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**.  
  
        > [!NOTE]  
        >  Если публикация не поддерживает предварительно вычисляемые секции, то логические записи использовать нельзя. Дополнительные сведения см. в статье [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md).  
  
    -   Если это значение NULL, то необходимо запустить агент моментальных снимков для создания исходного моментального снимка для публикации.  
  
2.  Если статьи, входящие в логическую запись, не существуют, выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) на издателе в базе данных публикации. Укажите один из приведенных ниже параметров определения и распознавания конфликтов в логической записи.  
  
    -   Для распознавания и разрешения конфликтов, возникающих в связанных строках логической записи, присвойте значение **true** в качестве значения параметра **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution**.  
  
    -   Для использования стандартного определения и разрешения конфликтов уровня строки и столбца присвойте значение **false** в качестве значения параметра **@logical_record_level_conflict_detection** и **@logical_record_level_conflict_resolution**(они имеют это значение по умолчанию).  
  
3.  Повторите шаг 2 для каждой статьи, которая содержит логическую запись. Необходимо использовать в каждой статье логической записи одинаковые параметры определения и разрешения конфликтов. Дополнительные сведения см. в статье [Detecting and Resolving Conflicts in Logical Records](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-resolving-in-logical-record.md).  
  
4.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md). Укажите **@publication**, имя одной статьи связи в качестве значения параметра **@article**, имя второй статьи в качестве значения параметра **@join_articlename**, имя связи в качестве значения параметра **@filtername**, предложение, определяющее связь между двумя статьями в качестве значения параметра **@join_filterclause**, тип соединения в качестве значения параметра **@join_unique_key** , а также одно из следующих значений параметра **@filter_type**:  
  
    -   **2** — определяет логическую связь;  
  
    -   **3** — определят логическую связь с фильтром соединения.  
  
    > [!NOTE]  
    >  Фильтр соединения не используется, направление связи между двумя статьями несущественно.  
  
5.  Повторите шаг 2 для всех оставшихся связей логических записей в публикации.  
  
#### <a name="to-change-conflict-detection-and-resolution-for-logical-records"></a>Изменение способа определения и разрешения конфликтов логических записей  
  
1.  Для определения и разрешения конфликтов, возникающих в связанных строках логической записи, выполните следующие действия.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Задайте **@property** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Задайте **@property** в качестве значения параметра **@property** и **true** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
2.  Для использования стандартного метода определения и разрешения конфликтов уровня строки и столбца выполните следующие действия.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Задайте **@property** в качестве значения параметра **@property** и **false** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
    -   В базе данных публикации на издателе выполните процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Задайте **@property** в качестве значения параметра **@property** и **false** в качестве значения параметра **@value**. Задайте **1** в качестве значения параметра **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
#### <a name="to-remove-a-logical-record-relationship"></a>Удаление связи логических записей  
  
1.  На издателе в базе данных публикации выполните приведенный ниже запрос для получения сведений обо всех связях логических записей, определенных для указанной публикации:  
  
     [!code-sql[HowTo#sp_ReturnMergeLogicalRecords](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_1.sql)]  
  
     Запомните имя удаляемой связи логических записей, содержащееся в столбце **filtername** результирующего набора.  
  
    > [!NOTE]  
    >  Этот запрос возвращает те же сведения, что и системная хранимая процедура [sp_helpmergefilter](../../../relational-databases/system-stored-procedures/sp-helpmergefilter-transact-sql.md), однако системная хранимая процедура возвращает только сведения по тем связям логических записей, которые являются также фильтрами соединения.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_dropmergefilter](../../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md). Укажите **@publication**, имя одной из статей в связи в качестве значения параметра **@article**, а также имя связи из шага 1 в качестве значения параметра **@filtername**.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В этом примере разрешается использование предварительно вычисляемых секций в существующей публикации и создается логическая запись, в которую входят две новые статьи для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-sql[HowTo#sp_AddMergeLogicalRecord](../../../relational-databases/replication/codesnippet/tsql/define-a-logical-record-_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
> [!NOTE]  
>  Репликация слиянием позволяет указывать, что конфликты должны отслеживаться и разрешаться на уровне логических записей, но эти параметры нельзя задать с помощью объектов RMO.  
  
#### <a name="to-define-a-logical-record-relationship-without-an-associated-join-filter"></a>Определение связи логических записей без сопутствующего фильтра соединения  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> , установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Если свойство <xref:Microsoft.SqlServer.Replication.MergePublication.PartitionGroupsOption%2A> имеет значение <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.False>, укажите значение <xref:Microsoft.SqlServer.Replication.PartitionGroupsOption.True>.  
  
5.  Если статьи, которые должны составить логическую запись, не существуют, создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> и задайте следующие свойства.  
  
    -   Имя статьи для <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Если статья отфильтрована горизонтально, задайте условие фильтра строк для свойства <xref:Microsoft.SqlServer.Replication.MergeArticle.FilterClause%2A> (необязательно). Используйте это свойство для определения статического или параметризованного фильтра строк. Дополнительные сведения см. в статье [Parameterized Row Filters](../../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
     Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
6.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Create%2A> .  
  
7.  Повторите шаги 5 и 6 для каждой статьи, составляющей логическую запись.  
  
8.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> , чтобы определить связь логических записей между статьями. Затем установите следующие свойства.  
  
    -   Имя дочерней статьи в связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.ArticleName%2A> .  
  
    -   Имя существующей, родительской статьи в связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinArticleName%2A> .  
  
    -   Имя связи логических записей для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterName%2A> .  
  
    -   Выражение, определяющее связь для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.JoinFilterClause%2A> .  
  
    -   Значение <xref:Microsoft.SqlServer.Replication.FilterTypes.LogicalRecordLink> для свойства <xref:Microsoft.SqlServer.Replication.MergeJoinFilter.FilterTypes%2A> . Если связь логических записей является также фильтром соединения, укажите значение <xref:Microsoft.SqlServer.Replication.FilterTypes.JoinFilterAndLogicalRecordLink> для этого свойства. Дополнительные сведения см. в статье [Группирование изменений в связанных строках с помощью логических записей](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
9. Вызовите метод <xref:Microsoft.SqlServer.Replication.MergeArticle.AddMergeJoinFilter%2A> для объекта, представляющего дочернюю статью в этой связи. Передайте объект <xref:Microsoft.SqlServer.Replication.MergeJoinFilter> из шага 8, чтобы определить связь.  
  
10. Повторите шаги 8 и 9 для каждой оставшейся связи логических записей в публикации.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере создается логическая запись, составленная из двух новых статей для таблиц `SalesOrderHeader` и `SalesOrderDetail` .  
  
 [!code-cs[HowTo#rmo_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createlogicalrecord)]  
  
 [!code-vb[HowTo#rmo_vb_CreateLogicalRecord](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createlogicalrecord)]  
  
## <a name="see-also"></a>См. также:  
 [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)   
 [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [Определение и изменение статического строкового фильтра](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [Группирование изменений в связанных строках с помощью логических записей](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [Оптимизация производительности параметризованного фильтра с помощью предварительно вычисляемых секций](../../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)   
 [Группирование изменений в связанных строках с помощью логических записей](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)  
  
  
