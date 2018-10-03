---
title: Просмотр и изменение свойств статьи | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9ccee2c8fd7fe02ff038105bd4bc934201ed861c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47710412"
---
# <a name="view-and-modify-article-properties"></a>Просмотр и изменение свойств статьи
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается процесс просмотра и изменения свойств статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] при помощи среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
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
  
-   После создания публикации для некоторых изменений свойств требуется новый моментальный снимок. Если на публикацию имеются подписки, для некоторых изменений также требуется повторная инициализация всех подписок. Дополнительные сведения см. в статьях [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md) и [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Просмотрите и измените свойства статьи в диалоговом окне **Свойства публикации — \<публикация>**, доступном в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] и мониторе репликации. Сведения о запуске монитора репликации см. в [этой статье](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
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
  
#### <a name="to-view-and-modify-article-properties"></a>Просмотр и изменение свойства статьи  
  
1.  На странице **Статьи** диалогового окна **Свойства публикации — \<публикация>** выберите статью и щелкните **Свойства статьи**.  
  
2.  Выберите статьи, для которых необходимо внести изменения в свойства:  
  
    -   Щелкните **Указать свойства выделенной статьи \<тип_объекта>**, чтобы открыть диалоговое окно **Свойства статьи — \<имя_объекта>**. Изменения, внесенные в этом диалоговом окне, применяются только к объекту, который будет выделен на панели объектов на странице **Статьи**.  
  
    -   Щелкните **Указать свойства всех статей \<тип_объекта>**, чтобы открыть диалоговое окно **Свойства всех статей \<тип_объекта>**. Изменения свойств, внесенные в этом диалоговом окне, применяются ко всем объектам этого типа на панели объектов на странице **Статьи**, включая объекты, не выбранные для публикации.  
  
        > [!NOTE]  
        >  Изменения свойств, внесенные в диалоговом окне **Свойства всех статей \<тип_объекта>** переопределяют изменения, сделанные ранее в диалоговом окне **Свойства статьи — \<имя_объекта>**. Например, если нужно установить некоторое количество значений по умолчанию для всех статей типа объекта, но при этом задать некоторые свойства для отдельных объектов, сначала установите значения по умолчанию для всех статей. Затем установите свойства для отдельных объектов.  
  
3.  Измените свойства, если необходимо, и нажмите кнопку **ОК**.  
  
4.  Щелкните **ОК**, чтобы вернуться в диалоговое окно **Свойства публикации — \<публикация>**.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Хранимые процедуры репликации позволяют программным путем вносить изменения в статьи и получать их свойства. Хранимые процедуры, используемые для этого, зависят от типа публикации, к которой принадлежит статья.  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a>Просмотр свойств статьи, принадлежащей публикации транзакций или моментальных снимков  
  
1.  Выполните хранимую процедуру [sp_helparticle](../../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md), задав в качестве параметров **@publication** и **@article** имя публикации и имя статьи соответственно. Если не указан параметр **@article**, то сведения будут возвращены по всем статьям публикации.  
  
2.  Чтобы получить список всех столбцов базовой таблицы, выполните хранимую процедуру [sp_helparticlecolumns](../../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md) для статей таблиц.  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a>Изменение свойств статьи, принадлежащей публикации транзакций или моментальных снимков  
  
1.  Выполните хранимую процедуру [sp_changearticle](../../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md), указав изменяемое свойство статьи в параметре **@property** , а его новое значение — в параметре **@value** имя публикации и имя статьи соответственно.  
  
    > [!NOTE]  
    >  Если в результате изменения необходимо создать новый моментальный снимок, необходимо также задать значение **1** в параметре **@force_invalidate_snapshot**, а если в результате изменения необходима повторная инициализация подписчиков, также необходимо указать значение **1** в параметре **@force_reinit_subscription**. Дополнительные сведения о свойствах публикации и статьи, при изменении которых требуется создание нового моментального снимка или повторная инициализация, см. в [этой статье](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a>Просмотр свойств статьи, принадлежащей публикации слиянием  
  
1.  Выполните хранимую процедуру [sp_helpmergearticle](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md), задав в качестве параметров **@publication** и **@article** имя публикации и имя статьи соответственно. Если эти параметры не указаны, то сведения будут возвращены по всем статьям в публикации или на издателе.  
  
2.  Чтобы получить список всех столбцов базовой таблицы, выполните хранимую процедуру [sp_helpmergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql.md) для статей таблиц.  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a>Изменение свойств статьи, принадлежащей публикации слиянием  
  
1.  Выполните хранимую процедуру [sp_changemergearticle](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав изменяемое свойство статьи в параметре **@property** , а его новое значение — в параметре **@value** имя публикации и имя статьи соответственно.  
  
    > [!NOTE]  
    >  Если в результате изменения необходимо создать новый моментальный снимок, необходимо также задать значение **1** в параметре **@force_invalidate_snapshot**, а если в результате изменения необходима повторная инициализация подписчиков, также необходимо указать значение **1** в параметре **@force_reinit_subscription**. Дополнительные сведения о свойствах, при изменении которых требуется создание нового моментального снимка или повторная инициализация, см. в [этой статье](../../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
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
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Просмотр или изменение свойств статьи, принадлежащей публикации моментальных снимков или публикации транзакций  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.TransArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.TransArticle> , которое можно установить (необязательно).  
  
7.  Если для свойства **P:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, то для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно). Если для свойства **false** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения будут отправлены на сервер немедленно.  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a>Просмотр или изменение свойств статьи, принадлежащей публикации слиянием  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует.  
  
6.  Чтобы изменить свойства, установите новое значение для одного из свойств <xref:Microsoft.SqlServer.Replication.MergeArticle> , которое можно установить (необязательно).  
  
7.  Если для свойства **P:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, то для фиксирования изменений на сервере необходимо вызвать метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> (необязательно). Если для свойства **false** в параметре <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (по умолчанию), изменения будут отправлены на сервер немедленно.  
  
###  <a name="PShellExample"></a> Пример (объекты RMO)  
 В этом примере изменяется статья публикации слиянием, при этом указывается обработчик бизнес-логики, используемый этой статьей.  
  
 [!code-cs[HowTo#rmo_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a>См. также:  
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Изменение свойств публикации и статьи](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
