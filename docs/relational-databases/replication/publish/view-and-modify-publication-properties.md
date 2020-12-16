---
title: Просмотр и изменение свойств публикации | Документация Майкрософт
description: Узнайте, как просматривать и изменять свойства публикации в SQL Server с помощью SQL Server Management Studio, Transact-SQL или объектов Replication Management Objects.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- viewing replication properties
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- publications [SQL Server replication], properties
- articles [SQL Server replication], properties
- modifying replication properties, publications
- publications [SQL Server replication], modifying
ms.assetid: 27d72ea4-bcb6-48f2-b4aa-eb1410da7efc
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 83b1d20afdc123359f3b34de90875e7977d7b541
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97468895"
---
# <a name="view-and-modify-publication-properties"></a>Просмотр и изменение свойств публикации
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  В данном разделе описывается процесс просмотра и изменения свойств публикации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
-   **Для просмотра и изменения свойств публикации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Некоторые свойства нельзя изменять после создания публикации, другие нельзя изменять при наличии подписок на публикацию. Свойства, которые нельзя изменять, отображаются в режиме только для чтения.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Рекомендации  
  
-   После создания публикации для некоторых изменений свойств требуется новый моментальный снимок. Если на публикацию имеются подписки, для некоторых изменений также требуется повторная инициализация всех подписок. Дополнительные сведения см. в статьях [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) и [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотр и изменение свойств публикации осуществляется в диалоговом окне **Свойства публикации — \<Publication>** , которое доступно в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и в мониторе репликации. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
 Диалоговое окно **Свойства публикации — \<Publication>** содержит следующие страницы:  
  
-   Страница **Общие** включает имя и описание публикации, имя базы данных, тип публикации и настройки срока окончания действия подписки.  
  
-   Страница **Статьи** соответствует странице **Статьи** мастера создания публикаций. Эта страница предназначена для добавления и удаления статей, изменения свойств и фильтрации столбцов для статей.  
  
-   Страница **Фильтрация строк** соответствует странице **Фильтрация строк таблицы** мастера создания публикаций. Эта страница предназначена для добавления, изменения и удаления статических фильтров строк для всех типов публикаций, для добавления, изменения и удаления параметризованных фильтров строк и фильтров соединения для публикаций слиянием.  
  
-   Страница **Моментальный снимок** позволяет задать формат и местоположение моментального снимка, необходимость его сжатия, а также скрипты для запуска до и после применения моментального снимка.  
  
-   Страница **Моментальный снимок FTP** (для публикаций моментальных снимков и транзакций, а также для публикаций слиянием для издателей, использующих версии более ранние, чем SQL Server 2005) позволяет указать возможность загрузки файлов моментальных снимков подписчиками через протокол передачи файлов (FTP).  
  
-   Страница **Моментальный снимок FTP и Интернет** (для публикаций слиянием от издателей, использующих версию SQL Server 2005 или более позднюю) позволяет указать возможность загрузки файлов моментальных снимков подписчиками через протокол FTP и возможность синхронизации подписки подписчиками через протокол HTTPS.  
  
-   Страница **Параметры подписки** позволяет устанавливать ряд параметров, которые применяются ко всем подпискам. Параметры отличаются в зависимости от типа публикации.  
  
-   Страница **Список доступа к публикации** позволяет указать, какие имена входа и группы имеют доступ к публикации.  
  
-   Страница **Безопасность агентов** предоставляет доступ к настройкам учетных записей, под которыми запускаются и устанавливают соединения с компьютерами в топологии репликации следующие агенты: агент моментальных снимков для всех публикаций, агент чтения журнала для всех публикаций транзакций и агент чтения очереди для публикаций транзакций, в которых допускаются подписки, обновляемые посредством очередей.  
  
-   Страница **Секции данных** (для публикаций слиянием от издателей, использующих версию SQL Server 2005 или более позднюю) позволяет указать, могут ли подписчики на публикации с параметризованными фильтрами запрашивать моментальный снимок, если он не доступен. Эта страница также позволяет создавать моментальные снимки для одной или нескольких секций либо однократно, либо по расписанию.  
  
#### <a name="to-view-and-modify-publication-properties-in-management-studio"></a>Просмотр и изменение свойств публикации в среде Management Studio  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию и выберите **Свойства**.  
  
4.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  

#### <a name="to-view-and-modify-publication-properties-in-replication-monitor"></a>Просмотр и изменение свойств публикации в мониторе репликации  
  
1.  Раскройте группу издателей в левой панели монитора репликации, а затем раскройте издатель.  
  
2.  Щелкните правой кнопкой мыши публикацию и выберите **Свойства**.  
  
3.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 Публикации могут быть изменены, а их свойства могут быть возвращены программно с помощью хранимых процедур репликации. Используемые хранимые процедуры зависят от типа публикации.  
  
#### <a name="to-view-the-properties-of-a-snapshot-or-transactional-publication"></a>Просмотр свойств публикации моментальных снимков или публикации транзакций  
  
1.  Выполните хранимую процедуру [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md), указав имя публикации в параметре **\@publication**. Если не указать этот параметр, будут возвращены сведения обо всех публикациях на издателе.  
  
#### <a name="to-change-the-properties-of-a-snapshot-or-transactional-publication"></a>Изменение свойств публикации моментальных снимков или публикации транзакций  
  
1.  Выполните хранимую процедуру [sp_changepublication](../../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав изменяемое свойство публикации в параметре **\@property**, а новое значение этого свойства — в параметре **\@value**.  
  
    > [!NOTE]  
    >  Если изменение потребует создания нового моментального снимка, нужно также указать значение **1** в параметре **\@force_invalidate_snapshot**, а если изменение потребует повторной инициализации подписчиков — значение **1** в параметре **\@force_reinit_subscription**. Дополнительные сведения о свойствах публикации и статьи, при изменении которых требуется создание нового моментального снимка или повторная инициализация, см. в [этой статье](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-merge-publication"></a>Просмотр свойств публикации слиянием  
  
1.  Выполните хранимую процедуру [sp_helpmergepublication](../../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md), указав имя публикации в параметре **\@publication**. Если не указать этот параметр, будут возвращены сведения обо всех публикациях на издателе.  
  
#### <a name="to-change-the-properties-of-a-merge-publication"></a>Изменение свойств публикации слиянием  
  
1.  Выполните хранимую процедуру [sp_changemergepublication](../../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md), указав свойство публикации, которое нужно изменить, в параметре **\@property**, а новое значение этого свойства — в параметре **\@value**.  
  
    > [!NOTE]  
    >  Если изменение потребует создания нового моментального снимка, нужно также указать значение **1** в параметре **\@force_invalidate_snapshot**, а если изменение потребует повторной инициализации подписчиков — значение **1** в параметре **\@force_reinit_subscription**. Дополнительные сведения о свойствах, изменение которых требует нового мгновенного снимка или повторной инициализации, см. в статье [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-a-snapshot"></a>Просмотр свойств моментального снимка  
  
1.  Выполните хранимую процедуру [sp_helppublication_snapshot](../../../relational-databases/system-stored-procedures/sp-helppublication-snapshot-transact-sql.md), указав имя публикации в параметре **\@publication**.  
  
#### <a name="to-change-the-properties-of-a-snapshot"></a>Изменение свойств моментального снимка  
  
1.  Выполните хранимую процедуру [sp_changepublication_snapshot](../../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md), указав одно или несколько новых свойств моментальных снимков в соответствующих параметрах моментальных снимков.  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере репликации транзакций возвращаются свойства публикации.  
  
 [!code-sql[HowTo#sp_helppublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_1.sql)]  
  
 В этом примере репликации транзакций отключается репликация схемы для публикации.  
  
 [!code-sql[HowTo#sp_changepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_2.sql)]  
  
 В этом примере репликации слиянием возвращаются свойства публикации.  
  
 [!code-sql[HowTo#sp_helpmergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_3.sql)]  
  
 В этом примере репликации слиянием отключается репликация схемы для публикации.  
  
 [!code-sql[HowTo#sp_changemergepublication](../../../relational-databases/replication/codesnippet/tsql/view-and-modify-publicat_4.sql)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Публикации можно изменять и получать доступ к их свойствам программно с помощью объектов RMO. Классы RMO, которые используются для просмотра или изменения публикации, зависят от типа публикации.  
  
#### <a name="to-view-or-modify-properties-of-a-snapshot-or-transactional-publication"></a>Просмотр или изменение свойств публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransPublication> , установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Чтобы изменить свойства, задайте новые значения для устанавливаемых свойств (необязательно). Чтобы определить, присвоено ли данное значение **&** свойству **And** , используется логический оператор AND ( <xref:Microsoft.SqlServer.Replication.PublicationAttributes> в Microsoft Visual C# и <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> в Microsoft Visual Basic). С помощью операторов включающего логического ИЛИ ( **|** в Visual C# и **Or** в Visual Basic) и исключающего логического ИЛИ ( **^** в Visual C# и **Xor** в Visual Basic) измените значения <xref:Microsoft.SqlServer.Replication.PublicationAttributes> для свойства <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> в Microsoft Visual Basic).  
  
5.  Если для свойства **true** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, то для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно). Если для свойства **false** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения будут отправлены на сервер немедленно.  
  
#### <a name="to-view-or-modify-properties-of-a-merge-publication"></a>Просмотр или изменение свойств публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergePublication> , установите для публикации свойства <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> и <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> , а также установите созданное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
3.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 2 были неверно определены свойства публикации, либо публикация не существует.  
  
4.  Чтобы изменить свойства, задайте новые значения для устанавливаемых свойств (необязательно). Чтобы определить, присвоено ли данное значение **&** в Visual C# и **And** , используется логический оператор AND ( <xref:Microsoft.SqlServer.Replication.PublicationAttributes> в Microsoft Visual C# и <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> в Microsoft Visual Basic). С помощью операторов включающего логического ИЛИ ( **|** в Visual C# и **Or** в Visual Basic) и исключающего логического ИЛИ ( **^** в Visual C# и **Xor** в Visual Basic) измените значения <xref:Microsoft.SqlServer.Replication.PublicationAttributes> для свойства <xref:Microsoft.SqlServer.Replication.Publication.Attributes%2A> в Microsoft Visual Basic).  
  
5.  Если для свойства **true** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, то для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно). Если для свойства **false** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения будут отправлены на сервер немедленно.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Примеры (объекты RMO)  
 В этом примере устанавливаются атрибуты публикации для публикации транзакций. Изменения кэшируются до тех пор, пока явно не отправляются на сервер.  
  
 [!code-cs[HowTo#rmo_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changetranpub_cached)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeTranPub_cached](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changetranpub_cached)]  
  
 В этом примере отключается DDL-репликация для публикации слиянием.  
  
 [!code-cs[HowTo#rmo_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergepub_ddl)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergePub_ddl](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergepub_ddl)]  
  
## <a name="see-also"></a>См. также:  
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Внесение изменений в схемы баз данных публикации](../../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Add Articles to and Drop Articles from a Publication](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-a-publication.md)  (Добавление и удаление статей в публикации)  
 [Просмотр сведений и выполнение задач с помощью монитора репликации](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)   
 [View and Modify Article Properties (Просмотр и изменение свойств статьи)](../../../relational-databases/replication/publish/view-and-modify-article-properties.md)  
  
  
