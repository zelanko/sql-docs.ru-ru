---
title: "Просмотр и изменение свойств статьи | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "sp_changearticle"
  - "sp_helparticle"
  - "просмотр свойств репликации"
  - "sp_changemergearticle"
  - "sp_helpmergearticle"
  - "изменение свойств репликации, статьи"
  - "статьи [репликация SQL Server], изменение"
  - "статьи [репликация SQL Server], свойства"
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# Просмотр и изменение свойств статьи
  В данном разделе описывается процесс просмотра и изменения свойств статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
-   **Для просмотра и изменения свойств статьи используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Некоторые свойства нельзя изменять после создания публикации, другие нельзя изменять при наличии подписок на публикацию. Свойства, которые нельзя изменять, отображаются в режиме только для чтения.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   После создания публикации для некоторых изменений свойств требуется новый моментальный снимок. Если на публикацию имеются подписки, для некоторых изменений также требуется повторная инициализация всех подписок. Дополнительные сведения см. в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) и [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр и изменение свойств статьи в **Свойства публикации — \< публикация>** диалоговое окно доступно в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и мониторе репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
-   Страница **Общие** включает имя и описание публикации, имя базы данных, тип публикации и настройки срока окончания действия подписки.  
  
-   Страница **Статьи** соответствует странице **Статьи** мастера создания публикаций. Эта страница предназначена для добавления и удаления статей, изменения свойств и фильтрации столбцов для статей.  
  
-   Страница **Фильтрация строк** соответствует странице **Фильтрация строк таблицы** мастера создания публикаций. Эта страница предназначена для добавления, изменения и удаления статических фильтров строк для всех типов публикаций, для добавления, изменения и удаления параметризованных фильтров строк и фильтров соединения для публикаций слиянием.  
  
-   Страница **Моментальный снимок** позволяет задать формат и местоположение моментального снимка, необходимость его сжатия, а также скрипты для запуска до и после применения моментального снимка.  
  
-    **Моментальный снимок — FTP** страницы (для моментального снимка и публикаций транзакций и публикаций слиянием с издателей, использующих версии до SQL Server 2005) позволяет указать, могут ли подписчикам загружать файлы моментальных снимков через протокол передачи файлов (FTP).  
  
-    **Моментальный снимок — FTP и Интернет** страницы (для публикаций слиянием от издателей, использующих SQL Server 2005 или более позднюю) позволяет указать ли подписчики могут загрузить файлы моментальных снимков по протоколу FTP и ли подписчики могут синхронизировать подписки по протоколу HTTPS.  
  
-   Страница **Параметры подписки** позволяет устанавливать ряд параметров, которые применяются ко всем подпискам. Параметры отличаются в зависимости от типа публикации.  
  
-   Страница **Список доступа к публикации** позволяет указать, какие имена входа и группы имеют доступ к публикации.  
  
-   Страница **Безопасность агентов** предоставляет доступ к настройкам учетных записей, под которыми запускаются и устанавливают соединения с компьютерами в топологии репликации следующие агенты: агент моментальных снимков для всех публикаций, агент чтения журнала для всех публикаций транзакций и агент чтения очереди для публикаций транзакций, в которых допускаются подписки, обновляемые посредством очередей.  
  
-    **Секции данных** страницы (для публикаций слиянием от издателей, использующих SQL Server 2005 или более позднюю) позволяет указать ли подписчики на публикации с параметризованными фильтрами запрашивать моментальный снимок, если он не доступен. Эта страница также позволяет создавать моментальные снимки для одной или нескольких секций либо однократно, либо по расписанию.  
  
#### Просмотр и изменение свойства статьи  
  
1.  На **статьи** Страница **Свойства публикации — \< публикация>** диалоговое окно, выберите статью и нажмите кнопку **Свойства статьи**.  
  
2.  Выберите статьи, для которых необходимо внести изменения в свойства:  
  
    -   Щелкните **указать свойства выделенной \< ObjectType> статьи** для запуска **Свойства статьи — \< имя_объекта>** диалоговое окно; свойство изменения, внесенные в этом диалоговом окне, применяются только объект, который будет выделен на панели объектов на **статьи** страницы.  
  
    -   Щелкните **Установка свойств всех \< ObjectType> статьи**, чтобы открыть **Свойства всех \< ObjectType> статьи** диалоговое окно; свойство изменения, внесенные в этом диалоговом окне применяются ко всем объектам этого типа на панели объектов на **статьи** страницы, включая объекты, не выбранные для публикации.  
  
        > [!NOTE]  
        >  Изменения, произведенные в **Свойства для всех \< ObjectType> статьи** диалоговое окно отменяют изменения, сделанные ранее в **Свойства статьи — \< имя_объекта>** диалоговое окно. Например, если нужно установить некоторое количество значений по умолчанию для всех статей типа объекта, но при этом задать некоторые свойства для отдельных объектов, сначала установите значения по умолчанию для всех статей. Затем установите свойства для отдельных объектов.  
  
3.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
4.  Щелкните **ОК** на **Свойства публикации — \< публикация>** диалоговое окно.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Хранимые процедуры репликации позволяют программным путем вносить изменения в статьи и получать их свойства. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит статья.  
  
#### Просмотр свойств статьи, принадлежащей публикации транзакций или моментальных снимков  
  
1.  Выполнение [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md), указав имя публикации для **@publication** и имя статьи для **@article** параметр. Если не указан параметр **@article**, то сведения будут возвращены по всем статьям публикации.  
  
2.  Выполнение [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) для статьи таблицы, список всех столбцов в базовой таблице.  
  
#### Изменение свойств статьи, принадлежащей публикации транзакций или моментальных снимков  
  
1.  Выполнение [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md), указав свойство статьи, изменяемых в **@property** параметр и новое значение этого свойства в **@value** параметр.  
  
    > [!NOTE]  
    >  Если данное изменение требует создания нового моментального снимка, необходимо также указать значение **1** для **@force_invalidate_snapshot**, и если изменение потребует повторной инициализации подписчиков, необходимо также указать значение **1** для **@force_reinit_subscription**. Дополнительные сведения о свойствах, при изменении которых требуется новый моментальный снимок или повторной инициализации, в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Просмотр свойств статьи, принадлежащей публикации слиянием  
  
1.  Выполнение [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md), указав имя публикации для **@publication** и имя статьи для **@article** параметр. Если эти параметры не указаны, то сведения будут возвращены по всем статьям в публикации или на издателе.  
  
2.  Выполнение [sp_helpmergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql.md) для статьи таблицы, список всех столбцов в базовой таблице.  
  
#### Изменение свойств статьи, принадлежащей публикации слиянием  
  
1.  Выполнение [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав свойство статьи, изменяемых в **@property** параметр и новое значение этого свойства в **@value** параметр.  
  
    > [!NOTE]  
    >  Если данное изменение требует создания нового моментального снимка, необходимо также указать значение **1** для **@force_invalidate_snapshot**, и если изменение потребует повторной инициализации подписчиков, необходимо также указать значение **1** для **@force_reinit_subscription**. Дополнительные сведения о свойствах, при изменении которых требуется новый моментальный снимок или повторной инициализации, в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 Следующий пример репликации транзакций производит получение свойств опубликованной статьи.  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_1.sql)]  
  
 Следующий пример репликации транзакций производит изменение параметров настройки схемы опубликованной статьи.  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_2.sql)]  
  
 Следующий пример репликации слиянием производит получение свойств опубликованной статьи.  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_3.sql)]  
  
 Следующий пример репликации слиянием производит изменение параметров обнаружения конфликтов для опубликованной статьи.  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-article-_4.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Статьи можно изменять программно, кроме того, с помощью объектов RMO можно программно получить доступ к их свойствам. Конкретные классы объектов RMO, используемые для этого, зависят от типа публикации, которой принадлежит статья.  
  
#### Просмотр или изменение свойств статьи, принадлежащей публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransArticle> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.TransArticle> Свойства, которые могут быть установлены.  
  
7.  (Необязательно) Если задано значение **true** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод для внесения изменений на сервере. Если задано значение **false** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения отправляются на сервер немедленно.  
  
#### Просмотр или изменение свойств статьи, принадлежащей публикации слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeArticle> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует.  
  
6.  (Необязательно) Чтобы изменить свойства, установите новое значение для одного из <xref:Microsoft.SqlServer.Replication.MergeArticle> Свойства, которые могут быть установлены.  
  
7.  (Необязательно) Если задано значение **true** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод для внесения изменений на сервере. Если задано значение **false** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения отправляются на сервер немедленно.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере изменяется статья публикации слиянием, при этом указывается обработчик бизнес-логики, используемый этой статьей.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## См. также:  
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Расширенное обнаружение и разрешение конфликтов репликации слиянием](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  