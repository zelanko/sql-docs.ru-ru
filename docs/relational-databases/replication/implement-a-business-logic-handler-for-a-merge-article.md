---
title: "Реализация обработчика бизнес-логики для статьи публикации слиянием | Microsoft Docs"
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
  - "разрешение конфликтов репликации слиянием [репликация SQL Server], обработчики бизнес-логики"
  - "обработчики бизнес-логики репликации слиянием [репликация SQL Server]"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
  - "обработчики бизнес-логики [репликация SQL Server]"
  - "BusinessLogicModule, класс"
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
caps.latest.revision: 44
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Реализация обработчика бизнес-логики для статьи публикации слиянием
  В данном разделе описывается процесс реализации обработчика бизнес-логики для статьи публикации слиянием в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью программирования репликации или объектов RMO.  
  
  <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> имен реализует интерфейс, который позволяет создавать сложные бизнес-логику для обработки событий, возникающих в процессе синхронизации репликации слиянием. Методы в обработчике бизнес-логики могут вызываться процессом репликации для каждой изменившейся строки, которая проходит репликацию в ходе синхронизации.  
  
 Общий порядок действий по реализации обработчика бизнес-логики следующий.  
  
1.  Создайте сборку обработчика бизнес-логики.  
  
2.  Зарегистрируйте сборку на распространителе.  
  
3.  Выполните развертывание сборки на сервере, где работает агент слияния. Для подписок по запросу агент работает на подписчике, а для принудительных подписок — на распространителе. Если используется веб-синхронизация, агент работает на веб-сервере.  
  
4.  Создание новых статей и настройка существующих статей на использование обработчика бизнес-логики.  
  
 Указанный обработчик бизнес-логики выполняется для каждой синхронизируемой строки. Сложная логика и вызовы других приложений или сетевых служб могут влиять на производительность. Дополнительные сведения об обработчиках бизнес-логики см. в разделе [выполнение бизнес логики во время слияния синхронизации](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 **В этом разделе**  
  
-   **Для реализации обработчика бизнес-логики для статьи публикации слиянием используется:**  
  
     [Программирование репликации](#ReplProg)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="ReplProg"></a> При помощи программирования репликации  
  
#### Создание и развертывание обработчика бизнес-логики  
  
1.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio создайте новый проект для сборки .NET, которая содержит код, реализующий обработчик бизнес-логики.  
  
2.  Добавьте в проект ссылки на следующие пространства имен.  
  
    |Ссылка на сборку|Местоположение|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (установка по умолчанию)|  
    |<xref:System.Data>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
    |<xref:System.Data.Common>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
  
3.  Добавьте класс, который переопределяет <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> класса.  
  
4.  Реализуйте <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> свойство для указания типов изменений, которые были обработаны.  
  
5.  Переопределите один или несколько следующих методов <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> класса:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -вызывается при фиксации изменения данных во время синхронизации.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> — вызывается, когда происходит ошибка, когда инструкция DELETE — загрузке или передаче.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> — вызывается, когда инструкции DELETE загрузки или передачи.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> — вызывается, когда возникает ошибка при выполнении инструкции INSERT является загрузке или передаче.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> — вызывается, когда инструкции INSERT загрузки или передачи.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> — вызывается, когда возникает конфликт инструкций UPDATE на издателе и подписчике.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> — вызывается, когда возникает конфликт инструкций UPDATE с инструкциями DELETE на издателе и подписчике.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> — вызывается, когда происходит ошибка, если инструкция UPDATE — загрузке или передаче.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> — вызывается, когда инструкции UPDATE загрузки или передачи.  
  
6.  Постройте проект, чтобы создать сборку обработчика бизнес-логики.  
  
7.  Произведите развертывание сборки в каталоге, содержащем исполняемый файл агента слияния (replmerg.exe), который по умолчанию устанавливается в каталог [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, либо установите его в глобальный кэш сборок .NET. Если эта сборка используется не только агентом слияния, то она должна быть помещена в глобальный кэш сборок. Сборки могут быть установлены в глобальный кэш СБОРОК с помощью средства глобального кэша сборок (**Gacutil.exe)** в .NET Framework SDK.  
  
    > [!NOTE]  
    >  Обработчик бизнес-логики должен быть развернут на всех серверах, на которых работает агент слияния, включая север IIS, на котором во время веб-синхронизации находится файл replisapi.dll.  
  
#### Регистрация обработчика бизнес-логики  
  
1.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Чтобы убедиться, что сборка не уже был зарегистрирован как обработчик бизнес-логики.  
  
2.  На распространителе выполните хранимую процедуру [работу sp_registercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), указав понятное имя обработчика бизнес-логики для **@article_resolver**, значение **true** для **@is_dotnet_assembly**, имя сборки для **@dotnet_assembly_name**, и полное имя класса, который переопределяет <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Если сборка не развертывается в том же каталоге, что и исполняемый файл агента слияния, в том же каталоге приложения, синхронно запускающего агент слияния или в глобальном кэше сборок (GAC), необходимо указать полное имя сборки для **@dotnet_assembly_name**. При проведении сеанса веб-синхронизации необходимо указать местоположение сборки на веб-сервере.  
  
#### Использование обработчика бизнес-логики со статьей в новой таблице  
  
1.  Выполнение [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Чтобы определить статью, указав понятное имя обработчика бизнес-логики для **@article_resolver**. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Использование обработчика бизнес-логики со статьей в существующей таблице  
  
1.  Выполнение [sp_changemergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав **@publication**, **@article**, значение **article_resolver** для **@property**, и понятное имя обработчика бизнес-логики для **@value**.  
  
###  <a name="TsqlExample"></a> Примеры (программирование репликации)  
 В следующем примере представлен обработчик бизнес-логики, осуществляющий запись в журнал аудита.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 Следующий пример осуществляет регистрацию обработчика бизнес-логики на сервере распространителя и настройку существующих статей публикации на его использование.  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../relational-databases/replication/codesnippet/tsql/implement-a-business-log_3.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### Создание обработчика бизнес-логики  
  
1.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio создайте новый проект для сборки .NET, которая содержит код, реализующий обработчик бизнес-логики.  
  
2.  Добавьте в проект ссылки на следующие пространства имен.  
  
    |Ссылка на сборку|Местоположение|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (установка по умолчанию)|  
    |<xref:System.Data>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
    |<xref:System.Data.Common>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
  
3.  Добавьте класс, который переопределяет <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> класса.  
  
4.  Реализуйте <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> свойство для указания типов изменений, которые были обработаны.  
  
5.  Переопределите один или несколько следующих методов <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> класса:  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> -вызывается при фиксации изменения данных во время синхронизации.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> — вызывается, когда возникает ошибка, пока выполняется инструкция DELETE загрузки или передачи.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> — вызывается, когда инструкции DELETE загрузки или передачи.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> -Если при выполнении инструкции INSERT возникает ошибка вызывается загрузке или передаче.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> — вызывается, когда инструкции INSERT загрузки или передачи.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> — вызывается, когда возникает конфликт инструкций UPDATE на издателе и подписчике.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> — вызывается, когда возникает конфликт инструкций UPDATE с инструкциями DELETE на издателе и подписчике.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> — Если ошибка возникает, когда инструкция UPDATE вызывается загрузке или передаче.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> — вызывается, когда инструкции UPDATE загрузки или передачи.  
  
    > [!NOTE]  
    >  Все конфликты статей, не обработанные пользовательской бизнес-логикой явным образом, обрабатываются сопоставителем конфликтов по умолчанию, назначенным для данной статьи.  
  
6.  Постройте проект, чтобы создать сборку обработчика бизнес-логики.  
  
#### Регистрация обработчика бизнес-логики  
  
1.  Создайте соединение с распространителем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса. Передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> и просмотрите возвращенный <xref:System.Collections.ArrayList> объекта, чтобы убедиться, что сборка не уже был зарегистрирован как обработчик бизнес-логики.  
  
4.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> класса. Задайте следующие свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> -имя сборки .NET. Если сборка не найдена ни в том же каталоге, что и исполняемый файл агента слияния, ни в папке приложения, производящего синхронный запуск агента слияния, ни в глобальном кэше сборок (GAC), то ее имя должно включать полный путь. При использовании обработчика бизнес-логики во время сеанса веб-синхронизации необходимо перед именем сборки указывать ее полный путь.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> -полное имя класса, который переопределяет <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> и реализует обработчик бизнес-логики.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> -Понятное имя, используемое при доступе к обработчик бизнес-логики.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> -значение **true**.  
  
#### Развертывание обработчика бизнес-логики  
  
1.  Произведите развертывание сборки на сервере, где запущен агент слияния, в папке, заданной при регистрации обработчика бизнес-логики на распространителе. Для подписок по запросу агент работает на подписчике, а для принудительных подписок — на распространителе. Если используется веб-синхронизация, агент работает на веб-сервере. Если в процессе регистрации обработчика бизнес-логики не был указан полный путь сборки, то ее развертывание необходимо производить в том же каталоге, что и исполняемый объект агента слияния, либо в папке приложения, осуществляющего запуск агента слияния в синхронном режиме. Если сборка используется несколькими приложениями, то ее необходимо установить в глобальный кэш сборок.  
  
#### Использование обработчика бизнес-логики со статьей в новой таблице  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeArticle> класса. Задайте следующие свойства.  
  
    -   Имя статьи для <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Имя публикации для <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Имя базы данных публикации <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.  
  
    -   Понятное имя обработчика бизнес-логики (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) для <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.Article.Create%2A> метод. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Использование обработчика бизнес-логики со статьей в существующей таблице  
  
1.  Создайте соединение с издателем с помощью <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.MergeArticle> класса.  
  
3.  Задайте <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>, и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> Свойства.  
  
4.  Задайте соединение из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> свойство.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод, чтобы получить свойства объекта. Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует. Дополнительные сведения см. в статье [View and Modify Article Properties](../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
6.  Задайте понятное имя обработчика бизнес-логики для <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>. Это значение <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> свойство, указанное при регистрации обработчика бизнес-логики.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере реализуется обработчик бизнес-логики, осуществляющий запись в журнал операций вставки, обновления и удаления на подписчике.  
  
 [!code-csharp[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 В следующем примере производится регистрация обработчика бизнес-логики на распространителе.  
  
 [!code-csharp[HowTo#rmo_RegisterBLH_10](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 В следующем примере производится настройка существующей статьи на использование обработчика бизнес-логики.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## См. также:  
 [Implement a Custom Conflict Resolver for a Merge Article](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [Отладка обработчика бизнес-логики & #40; Программирование репликации на & #41;](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
  
  