---
title: "Просмотр и изменение свойств публикации | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "просмотр свойств репликации"
  - "изменение свойств репликации, статьи"
  - "статьи [репликация SQL Server], изменение"
  - "публикации [репликация SQL Server], свойства"
  - "статьи [репликация SQL Server], свойства"
  - "изменение свойств репликации, публикации"
  - "публикации [репликация SQL Server], изменение"
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Просмотр и изменение свойств публикации
  В данном разделе описывается процесс просмотра и изменения свойств публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
-   **Для просмотра и изменения свойств публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Некоторые свойства нельзя изменять после создания публикации, другие нельзя изменять при наличии подписок на публикацию. Свойства, которые нельзя изменять, отображаются в режиме только для чтения.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   После создания публикации для некоторых изменений свойств требуется новый моментальный снимок. Если на публикацию имеются подписки, для некоторых изменений также требуется повторная инициализация всех подписок. Дополнительные сведения см. в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) и [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр и изменение свойств публикации в **Свойства публикации — \< публикация>** диалоговое окно доступно в [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и мониторе репликации. Сведения о запуске монитора репликации см. в разделе [запустить монитор репликации](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
  **Свойства публикации — \< публикация>** диалоговое окно содержит следующие страницы:  
  
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
  
#### Просмотр и изменение свойств публикации в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию и выберите **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
#### Просмотр и изменение свойств публикации в мониторе репликации  
  
1.  Раскройте группу издателей в левой панели монитора репликации, а затем раскройте издатель.  
  
2.  Щелкните правой кнопкой мыши публикацию и выберите **Свойства**.  
  
3.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикации могут быть изменены, а их свойства могут быть возвращены программно с помощью хранимых процедур репликации. Используемые хранимые процедуры зависят от типа публикации.  
  
#### Просмотр свойств публикации моментальных снимков или публикации транзакций  
  
1.  Выполнение [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), указав имя публикации для **@publication** параметр. Если не указать этот параметр, будут возвращены сведения обо всех публикациях на издателе.  
  
#### Изменение свойств публикации моментальных снимков или публикации транзакций  
  
1.  Выполнение [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав изменяемое свойство публикации в **@property** параметр и новое значение этого свойства в **@value** параметр.  
  
    > [!NOTE]  
    >  Если изменение потребует создания нового моментального снимка, необходимо также указать значение **1** для **@force_invalidate_snapshot**, и если изменение потребует повторной инициализации подписчиков, необходимо указать значение **1** для **@force_reinit_subscription**. Дополнительные сведения о свойствах, при изменении которых требуется новый моментальный снимок или повторной инициализации, в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Просмотр свойств публикации слиянием  
  
1.  Выполнение [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав имя публикации для **@publication** параметр. Если не указать этот параметр, будут возвращены сведения обо всех публикациях на издателе.  
  
#### Изменение свойств публикации слиянием  
  
1.  Выполнение [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав свойство публикации, изменяемых в **@property** параметр и новое значение этого свойства в **@value** параметр.  
  
    > [!NOTE]  
    >  Если изменение потребует создания нового моментального снимка, необходимо также указать значение **1** для **@force_invalidate_snapshot**, и если изменение потребует повторной инициализации подписчиков, необходимо указать значение **1** для **@force_reinit_subscription** Дополнительные сведения о свойствах, при изменении которых требуется новый моментальный снимок или повторной инициализации, в разделе [Изменение публикации и свойства статей](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### Просмотр свойств моментального снимка  
  
1.  Выполнение [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), указав имя публикации для **@publication** параметр.  
  
#### Изменение свойств моментального снимка  
  
1.  Выполнение [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), указав один или несколько новых свойств моментальных снимков для соответствующих параметрах моментальных снимков.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере репликации транзакций возвращаются свойства публикации.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 В этом примере репликации транзакций отключается репликация схемы для публикации.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 В этом примере репликации слиянием возвращаются свойства публикации.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 В этом примере репликации слиянием отключается репликация схемы для публикации.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно изменять и получать доступ к их свойствам программно с помощью объектов RMO. Классы RMO, которые используются для просмотра или изменения публикации, зависят от типа публикации.  
  
#### Просмотр или изменение свойств публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.TransPublication> класса, задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Чтобы изменить свойства, задайте новые значения для устанавливаемых свойств (необязательно). Использовать логический оператор AND (**&** в Microsoft Visual C# и **и** в Visual Basic) для определения данной <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значение для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство. Используйте исключающего логического оператора OR (**|** в Visual C# и **или** в Visual Basic) и исключающего логического или (**^** в Visual C# и **Xor** в Visual Basic) для изменения <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значения для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство.  
  
5.  (Необязательно) Если задано значение **true** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод для внесения изменений на сервере. Если задано значение **false** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения отправляются на сервер немедленно.  
  
#### Просмотр или изменение свойств публикации слиянием  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergePublication> класса, задайте <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> Свойства для публикации, а также набор <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> Свойства подключения, созданной на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Чтобы изменить свойства, задайте новые значения для устанавливаемых свойств (необязательно). Использовать логический оператор AND (**&** в Visual C# и **и** в Visual Basic) для определения данной <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значение для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство. Используйте исключающего логического оператора OR (**|** в Visual C# и **или** в Visual Basic) и исключающего логического или (**^** в Visual C# и **Xor** в Visual Basic) для изменения <xref:Microsoft.SqlServer.Replication.PublicationAttributes> значения для <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> свойство.  
  
5.  (Необязательно) Если задано значение **true** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, вызовите <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> метод для внесения изменений на сервере. Если задано значение **false** для <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения отправляются на сервер немедленно.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере устанавливаются атрибуты публикации для публикации транзакций. Изменения кэшируются до тех пор, пока явно не отправляются на сервер.  
  
 [!code-csharp[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 В этом примере отключается DDL-репликация для публикации слиянием.  
  
 [!code-csharp[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Внесение изменений схем в базы данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Добавление и удаление статей в публикации и #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)   
 [Просмотр сведений и выполнение задач для публикации & #40; Монитор репликации & #41;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-publication-replication-monitor.md)   
 [Просмотр и изменение свойств статьи](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  