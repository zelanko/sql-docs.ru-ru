---
title: "Определение или изменение фильтра столбцов | Microsoft Docs"
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
  - "фильтры [репликация SQL Server], столбец"
  - "изменение фильтров, столбец"
  - "изменение фильтров"
  - "фильтры столбцов [репликация SQL Server]"
ms.assetid: d7c3186a-9a8c-45d8-ab34-05beec4c26dd
caps.latest.revision: 40
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 40
---
# Определение или изменение фильтра столбцов
  В этом разделе описывается определение и изменение фильтра столбцов [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
-   **Для определения и изменения фильтра столбцов используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Некоторые столбцы не могут быть отфильтрованы; Дополнительные сведения см. в разделе [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md). При изменении фильтра столбцов после инициализации подписок необходимо создать новый моментальный снимок и выполнить повторную инициализацию всех подписок после выполнения изменений. Дополнительные сведения о требованиях к изменениям свойств см. в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Определение фильтров столбцов выполняется на странице **Статьи** мастера создания публикации. Дополнительные сведения об использовании мастера создания публикаций см. в разделе [Создать публикацию](../../../relational-databases/replication/publish/create-a-publication.md).  
  
 Определите и измените фильтры столбцов на **статьи** Страница **Свойства публикации — \< публикация>** диалоговое окно. Дополнительные сведения о свойствах публикации и статьи см. в разделе [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Определение фильтра столбцов  
  
1.  На странице **Статьи** мастера создания публикации раскройте таблицу, которую необходимо отфильтровать, на панели **Объекты для публикации** .  
  
2.  Снимите флажки рядом со столбцами, которые необходимо отфильтровать.  
  
#### Изменение параметров фильтрации столбцов  
  
1.  На **статьи** Страница **Свойства публикации — \< публикация>** диалогового окна разверните таблицу для фильтрации в **объекты для публикации** области.  
  
2.  Снимите флажки рядом со столбцами, которые необходимо отфильтровать, и проверьте, чтобы были установлены флажки для столбцов, которые должны быть включены в статью.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 При создании статей таблицы можно определить столбцы, которые нужно включить в статью, и изменить эти столбцы после определения статьи. Можно создать и изменить фильтруемые столбцы программно с помощью хранимых процедур репликации.  
  
> [!NOTE]  
>  В следующей процедуре предполагается, что базовая таблица не изменилась. Сведения о репликации изменений языка DDL для определения данных в опубликованных таблицах см. в разделе [внесение изменений схемы в базах данных публикаций](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md).  
  
#### Определение фильтра столбца для статьи, опубликованной в публикации моментальных снимков или публикации транзакций  
  
1.  Определите статью для фильтрации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Столбцы для включения в статью или удаления из нее будут определены.  
  
    -   Если публикация только несколько столбцов из таблицы с большим числом столбцов, выполнение [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation**.  
  
    -   При публикации большинства столбцов в таблице с большим числом столбцов выполните хранимую [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), указав значение **null** для **@column** и значение **Добавьте** для **@operation** Добавление всех столбцов. Затем выполните [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md), один раз для каждого исключаемого столбца, указав значение **drop** для **@operation** и имя исключаемого столбца для **@column**.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article**. Будут созданы объекты синхронизации для отфильтрованной статьи.  
  
#### Изменение фильтра столбца с целью включения дополнительных столбцов в статью, опубликованную в публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article**. Если публикация содержит существующие подписки, укажите значение **1** для **@change_active**. Объекты синхронизации для отфильтрованной статьи при этом будут повторно созданы.  
  
3.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
4.  Повторная инициализация подписок. Дополнительные сведения см. в разделе [повторно инициализировать подписки](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Изменение фильтра столбца с целью удаления столбцов из статьи, опубликованной в публикации моментальных снимков или публикации транзакций  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) один раз для каждого удаляемого столбца. Укажите имя столбца в параметре **@column** и значение **drop** в параметре **@operation**.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md). Укажите имя публикации в параметре **@publication** , а имя отфильтрованной статьи — в параметре **@article**. Если публикация содержит существующие подписки, укажите значение **1** для **@change_active**. Объекты синхронизации для отфильтрованной статьи при этом будут повторно созданы.  
  
3.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
4.  Повторная инициализация подписок. Дополнительные сведения см. в разделе [повторно инициализировать подписки](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Определение фильтра столбца для статьи, опубликованной в публикации слиянием  
  
1.  Определите статью для фильтрации. Дополнительные сведения см. в статье [Define an Article](../../../relational-databases/replication/publish/define-an-article.md).  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md). Столбцы для включения в статью или удаления из нее будут определены.  
  
    -   Если публикация только несколько столбцов из таблицы с большим числом столбцов, выполнение [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) один раз для каждого добавляемого столбца. Укажите имя столбца в параметре **@column** и значение **add** в параметре **@operation**.  
  
    -   При публикации большинства столбцов в таблице с большим числом столбцов выполните хранимую [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), указав значение **null** для **@column** и значение **Добавьте** для **@operation** Добавление всех столбцов. Затем выполните [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md), один раз для каждого исключаемого столбца, указав значение **drop** для **@operation** и имя исключаемого столбца для **@column**.  
  
#### Изменение фильтра столбца с целью включения дополнительных столбцов в статью, опубликованную в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) один раз для каждого добавляемого столбца. Укажите имя столбца для **@column**, значение **Добавьте** для **@operation** и значение **1** для обоих **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
2.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
3.  Повторная инициализация подписок. Дополнительные сведения см. в разделе [повторно инициализировать подписки](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
#### Изменение фильтра столбца с целью удаления столбцов из статьи, опубликованной в публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) один раз для каждого удаляемого столбца. Укажите имя столбца для **@column**, значение **drop** для **@operation** и значение **1** для обоих **@force_invalidate_snapshot** и **@force_reinit_subscription**.  
  
2.  Чтобы сформировать обновленный моментальный снимок, перезапустите задание агента моментальных снимков для публикации.  
  
3.  Повторная инициализация подписок. Дополнительные сведения см. в разделе [повторно инициализировать подписки](../../../relational-databases/replication/reinitialize-subscriptions.md).  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В этом примере репликации транзакций столбец `DaysToManufacture` удаляется из статьи, основанной на таблице `Product` .  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_1.sql)]  
  
 В этом примере репликации слиянием столбец `CreditCardApprovalCode` удаляется из статьи, основанной на таблице `SalesOrderHeader` .  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-colu_2.sql)]  
  
## См. также:  
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Фильтрация опубликованных данных для репликации слиянием](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  