---
title: "Определение сопоставителя статей публикации слиянием | Microsoft Docs"
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
  - "статьи [репликация SQL Server], разрешение конфликтов"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
  - "разрешение конфликтов репликации слиянием [репликация SQL Server], сопоставители конфликтов статей слияния"
ms.assetid: a40083b3-4f7b-4a25-a5a3-6ef67bdff440
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# Определение сопоставителя статей публикации слиянием
  В этом разделе описывается определение арбитра статей публикации слиянием в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Рекомендации](#Recommendations)  
  
-   **Для определения арбитра статей публикации слиянием используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Репликация слиянием допускает следующие типы сопоставителей статей:  
  
    -   Сопоставитель по умолчанию. Поведение сопоставителя по умолчанию зависит от того, является подписка клиентской или серверной. Дополнительные сведения об указании типа подписки см. в разделе [Укажите тип подписки слиянием и приоритета разрешения конфликтов & #40; SQL Server Management Studio & #41;](../../../relational-databases/replication/specify a merge subscription type and conflict resolution priority.md).  
  
    -   Пользовательский сопоставитель, который может быть обработчиком бизнес-логики (написанным на управляемом коде), или пользовательским, основанным на технологии COM. Дополнительные сведения см. в статье [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md). Если необходимо реализовать настраиваемую логику, которая выполняется для каждой реплицируемой строки, а не только для конфликтующих строк в разделе [реализовать обработчик бизнес-логики для статьи слияния](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Стандартная на основе COM арбитр конфликтов, который входит в состав [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Чтобы использовать сопоставитель, отличный от сопоставителя по умолчанию, необходимо скопировать сопоставитель на компьютер, на котором выполняется агент слияния, и зарегистрировать его (если используется обработчик бизнес-логики, он также должен быть зарегистрирован на издателе). Агент слияния выполняется на:  
  
    -   распространителе для принудительной подписки;  
  
    -   подписчике для подписки по запросу;  
  
    -   IIS-сервер [!INCLUDE[msCoName](../../../includes/msconame-md.md)] для подписки по запросу, которая использует веб-синхронизацию  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 После регистрации арбитра укажите, что статья должна использовать распознаватель на **распознавателя** вкладке **Свойства статьи — \< статья>** диалоговое окно доступно в мастере создания публикаций и **Свойства публикации — \< публикации>** диалоговое окно. Дополнительные сведения об использовании мастера и о доступе к диалоговому окну см. в разделе [Создать публикацию](../../../relational-databases/replication/publish/create-a-publication.md) и [Просмотр и изменение свойств публикации](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
#### Указание сопоставителя  
  
1.  На **статьи** страница мастера создания публикаций или **Свойства публикации — \< публикация>** диалоговое окно, выберите таблицу.  
  
2.  Щелкните **Свойства статьи**, затем щелкните **Указать свойства выделенной статьи таблицы**.  
  
3.  На **Свойства статьи — \< статья>** щелкните **распознавателя** вкладки.  
  
4.  Выберите **использовать пользовательский арбитр (зарегистрированный на распространителе)**, и выберите в списке распознаватель.  
  
5.  Если Сопоставитель запрашивает входные данные (такие как имя столбца), укажите его в **Введите данные, необходимые арбитру** текстовое поле.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
7.  Повторите этот процесс для каждой статьи, которая запрашивает сопоставитель.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### Регистрация пользовательского сопоставителя конфликтов  
  
1.  Если планируется зарегистрировать собственный пользовательский сопоставитель конфликтов, создайте один из следующих типов.  
  
    -   Сопоставитель на основе управляемого кода в качестве обработчика бизнес-логики. Дополнительные сведения см. в статье [Implement a Business Logic Handler for a Merge Article](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
    -   Арбитр на основе хранимых процедур и арбитр на основе COM. Дополнительные сведения см. в разделе [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md).  
  
2.  Чтобы определить, если нужный Сопоставитель уже зарегистрирован, выполните [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) на издателе в любой базе данных. Будет выведено описание пользовательского сопоставителя, а также идентификатор класса (CLSID) для каждого сопоставителя на основе COM, зарегистрированного на распространителе, или сведения об управляемой сборке для каждого обработчика бизнес-логики, зарегистрированного на распространителе.  
  
3.  Если нужного пользовательского сопоставителя еще не зарегистрировано, выполните [работу sp_registercustomresolver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) на распространителе. Укажите имя арбитра для **@article_resolver**; для обработчика бизнес-логики это понятное имя сборки. Арбитры конфликтов на основе COM укажите идентификатор CLSID DLL для **@resolver_clsid**, и для обработчика бизнес-логики, укажите значение **true** для **@is_dotnet_assembly**, имя сборки для **@dotnet_assembly_name**, и полное имя класса, который переопределяет <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> для **@dotnet_class_name**.  
  
    > [!NOTE]  
    >  Если сборку обработчика бизнес-логики не развертывается в том же каталоге, что и исполняемый файл агента слияния, в том же каталоге приложения, синхронно запускающего агент слияния или в глобальном кэше сборок (GAC), необходимо указать полное имя сборки для **@dotnet_assembly_name**.  
  
4.  Если сопоставитель является сопоставителем на основе COM, сделайте следующее.  
  
    -   Скопируйте DLL-библиотеку пользовательского сопоставителя на распространитель для принудительных подписок либо на подписчик для подписок по запросу.  
  
        > [!NOTE]  
        >  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Пользовательские арбитры конфликтов можно найти в [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]каталога COM.  
  
    -   Используйте файл regsvr32.exe, чтобы зарегистрировать DLL-библиотеку пользовательского сопоставителя в операционной системе. Например, чтобы зарегистрировать аддитивный сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , введите в командной строке следующее.  
  
        ```  
        regsvr32 ssradd.dll  
        ```  
  
5.  Если Сопоставитель является обработчиком бизнес-логики, разверните сборку в той же папке, что и исполняемый файл агента слияния (replmerg.exe), в папке приложения, которое вызывает агент слияния, или в папке, указанной для **@dotnet_assembly_name** параметр в шаге 3.  
  
    > [!NOTE]  
    >  Местом установки по умолчанию исполняемого файла агента слияния является [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM.  
  
#### Указание пользовательского сопоставителя при определении статьи публикации слиянием  
  
1.  Если планируется использовать собственный пользовательский сопоставитель конфликтов, создайте и зарегистрируйте сопоставитель с помощью описанной выше процедуры.  
  
2.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) и запомните имя нужного пользовательского сопоставителя в **значение** результирующего набора.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите имя арбитра из шага 2 для **@article_resolver** и любые нужные входные данные с помощью пользовательского распознавателя **@resolver_info** параметр. Для хранимой процедуры выполнения определенных пользовательских распознавателей **@resolver_info** имя хранимой процедуры. Дополнительные сведения о необходимых входных данных для арбитры, предоставляемые [!INCLUDE[msCoName](../../../includes/msconame-md.md)], в разделе [Microsoft арбитров конфликтов на базе COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Указание или изменение пользовательского сопоставителя для существующей статьи публикации слиянием  
  
1.  Чтобы определить, определен ли пользовательский арбитр конфликтов для статьи или получить имя арбитра конфликтов, выполните [sp_helpmergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md). Если имеется пользовательский арбитр конфликтов для статьи был определен, его имя будет отображено в **article_resolver** поле. Любые входные данные, переданные распознаватель будет отображаться в **resolver_info** поля результирующего набора.  
  
2.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) и запомните имя нужного пользовательского сопоставителя в **значение** поля результирующего набора.  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). Укажите значение **article_resolver**, включая полный путь для обработчиков бизнес-логики для **@property**, и имя нужного пользовательского сопоставителя из шага 2 для **@value**.  
  
4.  Чтобы изменить необходимые входные данные для пользовательского арбитра конфликтов, выполните [sp_changemergearticle & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) еще раз. Укажите значение **resolver_info** для **@property** и любые необходимые входные данные для пользовательского арбитра конфликтов **@value**. Для хранимой процедуры выполнения определенных пользовательских распознавателей **@resolver_info** имя хранимой процедуры. Дополнительные сведения о необходимых входных данных см. в разделе [Microsoft арбитров конфликтов на базе COM](../../../relational-databases/replication/merge/microsoft-com-based-resolvers.md).  
  
#### Отмена регистрации пользовательского сопоставителя конфликтов  
  
1.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) и запомните имя пользовательского арбитра конфликтов для удаления в **значение** поля результирующего набора.  
  
2.  Выполнение [sp_unregistercustomresolver & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md) на распространителе. Укажите полное имя пользовательского арбитра из шага 1 для **@article_resolver**.  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере создается новая статья и указывается, что усредняющий сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при возникновении конфликта должен использоваться для вычисления среднего значения в столбце **UnitPrice** .  
  
 [!code-sql[HowTo#sp_addmerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_1.sql)]  
  
 В этом примере изменяется статья и указывается, что аддитивный сопоставитель конфликтов [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] при возникновении конфликта должен использоваться для вычисления суммы значений в столбце **UnitsOnOrder** .  
  
 [!code-sql[HowTo#sp_changemerge_resolver](../../../relational-databases/replication/codesnippet/tsql/specify-a-merge-article-_2.sql)]  
  
## См. также:  
 [Расширенное обнаружение и разрешение конфликтов репликации слиянием](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  