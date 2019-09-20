---
title: Реализация обработчика бизнес-логики для статьи публикации слиянием | Документация Майкрософт
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
- merge replication conflict resolution [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: ed477595-6d46-4fa2-b0d3-a5358903ec05
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 17a7c0e27dbb6cb80cb0069a2ea76036654280e3
ms.sourcegitcommit: dc8697bdd950babf419b4f1e93b26bb789d39f4a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/10/2019
ms.locfileid: "70846681"
---
# <a name="implement-a-business-logic-handler-for-a-merge-article"></a>Реализация обработчика бизнес-логики для статьи публикации слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается процесс реализации обработчика бизнес-логики для статьи публикации слиянием в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью программирования репликации или объектов RMO.  
  
 Пространство имен <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> реализует интерфейс, позволяющий создавать сложную бизнес-логику для обработки событий, возникающих в процессе синхронизации слиянием. Методы в обработчике бизнес-логики могут вызываться процессом репликации для каждой изменившейся строки, которая проходит репликацию в ходе синхронизации.  
  
 Общий порядок действий по реализации обработчика бизнес-логики следующий.  
  
1.  Создайте сборку обработчика бизнес-логики.  
  
2.  Зарегистрируйте сборку на распространителе.  
  
3.  Выполните развертывание сборки на сервере, где работает агент слияния. Для подписок по запросу агент работает на подписчике, а для принудительных подписок — на распространителе. Если используется веб-синхронизация, агент работает на веб-сервере.  
  
4.  Создание новых статей и настройка существующих статей на использование обработчика бизнес-логики.  
  
 Указанный обработчик бизнес-логики выполняется для каждой синхронизируемой строки. Сложная логика и вызовы других приложений или сетевых служб могут влиять на производительность. Дополнительные сведения об обработчиках бизнес-логики см. в статье [Выполнение бизнес логики во время синхронизации слияния](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 **В этом разделе**  
  
-   **Для реализации обработчика бизнес-логики для статьи публикации слиянием используется:**  
  
     [Программирование репликации](#ReplProg)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="ReplProg"></a> При помощи программирования репликации  
  
#### <a name="to-create-and-deploy-a-business-logic-handler"></a>Создание и развертывание обработчика бизнес-логики  
  
1.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio создайте новый проект для сборки .NET, которая содержит код, реализующий обработчик бизнес-логики.  
  
2.  Добавьте в проект ссылки на следующие пространства имен.  
  
    |Ссылка на сборку|Местоположение|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (место установки по умолчанию)|  
    |<xref:System.Data>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
    |<xref:System.Data.Common>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
  
3.  Добавьте класс, переопределяющий класс <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
4.  Реализуйте свойство <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> , чтобы показать обрабатываемые типы изменений.  
  
5.  Переопределите один или несколько следующих методов класса <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> :  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> — вызывается, когда изменение данных фиксируется в ходе синхронизации;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> — вызывается, когда возникает ошибка при загрузке или передаче инструкции DELETE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> — вызывается, когда передаются или загружаются инструкции DELETE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> — вызывается, когда возникает ошибка при загрузке или передаче инструкции INSERT;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> — вызывается, когда передаются или загружаются инструкции INSERT;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> — вызывается, когда на издателе или на подписчике возникает конфликт инструкций UPDATE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> — вызывается, когда инструкции UPDATE вызывают конфликт с инструкциями DELETE на издателе и на подписчике;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> — вызывается, когда возникает ошибка при загрузке или передаче инструкции UPDATE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> — вызывается, когда передаются или загружаются инструкции UPDATE.  
  
6.  Постройте проект, чтобы создать сборку обработчика бизнес-логики.  
  
7.  Произведите развертывание сборки в каталоге, содержащем исполняемый файл агента слияния (replmerg.exe), который по умолчанию устанавливается в каталог [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM, либо установите его в глобальный кэш сборок .NET. Если эта сборка используется не только агентом слияния, то она должна быть помещена в глобальный кэш сборок. Установка сборки в глобальный кэш производится с помощью соответствующей программы (**Gacutil.exe)** , поставляемой в пакете .NET Framework SDK.  
  
    > [!NOTE]  
    >  Обработчик бизнес-логики должен быть развернут на всех серверах, на которых работает агент слияния, включая север IIS, на котором во время веб-синхронизации находится файл replisapi.dll.  
  
#### <a name="to-register-a-business-logic-handler"></a>Регистрация обработчика бизнес-логики  
  
1.  Чтобы убедиться, что сборка не была зарегистрирована ранее как обработчик бизнес-логики, выполните на издателе процедуру [sp_enumcustomresolvers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md).  
  
2.  В распространителе выполните [sp_registercustomresolver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), указав понятное имя обработчика бизнес-логики в параметре **\@article_resolver**, значение **true** в параметре **\@is_dotnet_assembly**, имя сборки в параметре **\@dotnet_assembly_name**, а полное имя класса, переопределяющего <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule>, в параметре **\@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Если сборка не найдена ни в том же каталоге, что и исполняемый файл агента слияния, ни в папке приложения, производящего синхронный запуск агента слияния, ни в глобальном кэше сборок (GAC), то в параметре **\@dotnet_assembly_name**, помимо имени сборки, необходимо задать ее полный путь. При проведении сеанса веб-синхронизации необходимо указать местоположение сборки на веб-сервере.  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a>Использование обработчика бизнес-логики со статьей в новой таблице  
  
1.  Чтобы определить статью, выполните хранимую процедуру [sp_addmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md), указав понятное имя обработчика бизнес-логики в параметре **\@article_resolver**. Дополнительные сведения см. в статье [определить статью](../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a>Использование обработчика бизнес-логики со статьей в существующей таблице  
  
1.  Выполните хранимую процедуру [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав параметры **\@publication**, **\@article**, значение **article_resolver** в параметре **\@property** и понятное имя обработчика бизнес-логики в параметре **\@value**.  
  
###  <a name="TsqlExample"></a> Примеры (программирование репликации)  
 В следующем примере представлен обработчик бизнес-логики, осуществляющий запись в журнал аудита.  
  
 [!code-cs[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 Следующий пример осуществляет регистрацию обработчика бизнес-логики на сервере распространителя и настройку существующих статей публикации на его использование.  
  
 [!code-sql[HowTo#sp_RegisterBLH_10](../../relational-databases/replication/codesnippet/tsql/implement-a-business-log_3.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
#### <a name="to-create-a-business-logic-handler"></a>Создание обработчика бизнес-логики  
  
1.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio создайте новый проект для сборки .NET, которая содержит код, реализующий обработчик бизнес-логики.  
  
2.  Добавьте в проект ссылки на следующие пространства имен.  
  
    |Ссылка на сборку|Местоположение|  
    |------------------------|--------------|  
    |<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport>|[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]COM (место установки по умолчанию)|  
    |<xref:System.Data>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
    |<xref:System.Data.Common>|Глобальный кэш сборок (компонент платформы .NET Framework)|  
  
3.  Добавьте класс, переопределяющий класс <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
4.  Реализуйте свойство <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.HandledChangeStates%2A> , чтобы показать обрабатываемые типы изменений.  
  
5.  Переопределите один или несколько следующих методов класса <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> :  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.CommitHandler%2A> — вызывается, когда изменение данных фиксируется в ходе синхронизации;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteErrorHandler%2A> — вызывается, когда возникает ошибка при загрузке или передаче инструкции DELETE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.DeleteHandler%2A> — вызывается, когда передаются или загружаются инструкции DELETE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertErrorHandler%2A> — вызывается, когда возникает ошибка при загрузке или передаче инструкции INSERT;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.InsertHandler%2A> — вызывается, когда передаются или загружаются инструкции INSERT;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateConflictsHandler%2A> — вызывается, когда на издателе или на подписчике возникает конфликт инструкций UPDATE;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateDeleteConflictHandler%2A> — вызывается, когда инструкции UPDATE вызывают конфликт с инструкциями DELETE на издателе и на подписчике;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateErrorHandler%2A> — вызывается, когда возникает ошибка в инструкции UPDATE при передаче или загрузке;  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule.UpdateHandler%2A> — вызывается, когда передаются или загружаются инструкции UPDATE.  
  
    > [!NOTE]  
    >  Все конфликты статей, не обработанные пользовательской бизнес-логикой явным образом, обрабатываются сопоставителем конфликтов по умолчанию, назначенным для данной статьи.  
  
6.  Постройте проект, чтобы создать сборку обработчика бизнес-логики.  
  
#### <a name="to-register-a-business-logic-handler"></a>Регистрация обработчика бизнес-логики  
  
1.  Создайте соединение с распространителем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.ReplicationServer> . Передайте объект <xref:Microsoft.SqlServer.Management.Common.ServerConnection> , созданный на шаге 1.  
  
3.  Чтобы убедиться, что сборка не была ранее зарегистрирована в качестве обработчика бизнес-логики, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumBusinessLogicHandlers%2A> и просмотрите возвращенный объект <xref:System.Collections.ArrayList> .  
  
4.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler> . Задайте следующие свойства.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetAssemblyName%2A> — имя сборки .NET. Если сборка не найдена ни в том же каталоге, что и исполняемый файл агента слияния, ни в папке приложения, производящего синхронный запуск агента слияния, ни в глобальном кэше сборок (GAC), то ее имя должно включать полный путь. При использовании обработчика бизнес-логики во время сеанса веб-синхронизации необходимо перед именем сборки указывать ее полный путь.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.DotNetClassName%2A> — полное имя класса, который замещает класс <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> и реализует обработчик бизнес-логики.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> — понятное имя, используемое для доступа к обработчику бизнес-логики.  
  
    -   <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.IsDotNetAssembly%2A> — значение **true**.  
  
#### <a name="to-deploy-a-business-logic-handler"></a>Развертывание обработчика бизнес-логики  
  
1.  Произведите развертывание сборки на сервере, где запущен агент слияния, в папке, заданной при регистрации обработчика бизнес-логики на распространителе. Для подписок по запросу агент работает на подписчике, а для принудительных подписок — на распространителе. Если используется веб-синхронизация, агент работает на веб-сервере. Если в процессе регистрации обработчика бизнес-логики не был указан полный путь сборки, то ее развертывание необходимо производить в том же каталоге, что и исполняемый объект агента слияния, либо в папке приложения, осуществляющего запуск агента слияния в синхронном режиме. Если сборка используется несколькими приложениями, то ее необходимо установить в глобальный кэш сборок.  
  
#### <a name="to-use-a-business-logic-handler-with-a-new-table-article"></a>Использование обработчика бизнес-логики со статьей в новой таблице  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> . Задайте следующие свойства.  
  
    -   Имя статьи для <xref:Microsoft.SqlServer.Replication.Article.Name%2A>.  
  
    -   Имя публикации в свойстве <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>.  
  
    -   Имя базы данных публикации в свойстве <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A>.  
  
    -   Понятное имя обработчика бизнес-логики (<xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A>) в свойстве <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>.  
  
3.  Вызовите метод <xref:Microsoft.SqlServer.Replication.Article.Create%2A> . Дополнительные сведения см. в статье [определить статью](../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-use-a-business-logic-handler-with-an-existing-table-article"></a>Использование обработчика бизнес-логики со статьей в существующей таблице  
  
1.  Создайте соединение с издателем с помощью класса <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Создайте экземпляр класса <xref:Microsoft.SqlServer.Replication.MergeArticle> .  
  
3.  Установите свойства <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>и <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Установите полученное на шаге 1 соединение в качестве значения свойства <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Чтобы получить свойства объекта, вызовите метод <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> . Если этот метод возвращает **false**, то либо на шаге 3 были неверно определены свойства статьи, либо статья не существует. Дополнительные сведения см. в статье [View and Modify Article Properties](../../relational-databases/replication/publish/view-and-modify-article-properties.md).  
  
6.  Задайте понятное имя обработчика бизнес-логики в параметре <xref:Microsoft.SqlServer.Replication.MergeArticle.ArticleResolver%2A>. Это значение свойства <xref:Microsoft.SqlServer.Replication.BusinessLogicHandler.FriendlyName%2A> , указанного при регистрации обработчика бизнес-логики.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В следующем примере реализуется обработчик бизнес-логики, осуществляющий запись в журнал операций вставки, обновления и удаления на подписчике.  
  
 [!code-cs[HowTo#rmo_BusinessLogicCode](../../relational-databases/replication/codesnippet/csharp/rmohowto/businesslogic.cs#rmo_businesslogiccode)]  
  
 [!code-vb[HowTo#rmo_vb_BusinessLogicCode](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/businesslogic.vb#rmo_vb_businesslogiccode)]  
  
 В следующем примере производится регистрация обработчика бизнес-логики на распространителе.  
  
 [!code-cs[HowTo#rmo_RegisterBLH_10](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_registerblh_10)]  
  
 [!code-vb[HowTo#rmo_vb_RegisterBLH_10](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_registerblh_10)]  
  
 В следующем примере производится настройка существующей статьи на использование обработчика бизнес-логики.  
  
 [!code-cs[HowTo#rmo_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a>См. также:  
 [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [Отладка обработчика бизнес-логики (программирование репликации)](../../relational-databases/replication/debug-a-business-logic-handler-replication-programming.md)   
 [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Основные понятия объектов RMO](../../relational-databases/replication/concepts/replication-management-objects-concepts.md)  
  
  
