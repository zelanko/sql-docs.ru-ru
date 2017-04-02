---
title: "Определение статьи | Microsoft Docs"
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
  - "статьи [репликация SQL Server], определение"
  - "sp_addmergearticle"
  - "добавление статей"
  - "sp_addarticle"
  - "статьи [репликация SQL Server], добавление"
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 45
---
# Определение статьи
  В данном разделе описывается определение статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы выполните следующие действия.**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для определения статьи используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Названия статей не могут содержать следующие символы: % , * , [ , ] , | , : , " , ? , ' , \ , / , \< , >. Если объекты в базе данных, содержащие любые из этих символов, нужно реплицировать, необходимо задать для статьи имя, отличное от имени объекта.  
  
##  <a name="Security"></a> Безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](http://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание публикаций и определение статей осуществляется с помощью мастера создания публикаций. После создания публикации, просмотр и изменение свойств публикации в **Свойства публикации — \< публикация>** диалоговое окно. Сведения о создании публикации из базы данных Oracle см. в разделе [Создание публикации из базы данных Oracle](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Разверните **репликации** папки затем щелкните правой кнопкой **Локальные публикации** папки.  
  
3.  Щелкните **Создать публикацию**.  
  
4.  Следуйте указаниям на страницах мастера создания публикаций, чтобы:  
  
    -   задать распространитель, если распространение не было настроено на сервере. Дополнительные сведения о настройке распространения см. в разделе [настройки публикации и распространения](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         При указании на **распространитель** страницы, что сервер издателя буде функционировать как свой собственный распространитель (локальный распространитель), а сервер не настроен как распространитель, мастера создания публикаций произведет настройку сервера. Нужно будет задать для распространителя папку моментальных снимков по умолчанию на странице **Папка моментальных снимков** . Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о соответствующей защите папок см. в разделе [Безопасность папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Если задано, что в качестве распространителя будет функционировать другой сервер, необходимо ввести пароль на странице **Административный пароль** для соединений, устанавливаемых между издателем и распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
         Дополнительные сведения см. в разделе [Настройка распространения](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Выберите базу данных публикации.  
  
    -   Выберите тип публикации. Дополнительные сведения см. в разделе [типы репликации](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Задайте данные и объекты базы данных для публикации. При необходимости отфильтруйте столбцы из статей таблиц и установите свойства статей.  
  
    -   Если требуется, отфильтруйте строки из статей таблиц. Дополнительные сведения см. в разделе [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Настройте расписание для агента моментальных снимков.  
  
    -   Задайте учетные данные, под которыми следующие агенты репликации будут запускаться и устанавливать соединения:  
  
         \- Агент моментальных снимков для всех публикаций.  
  
         \- Агент чтения журнала для всех публикаций транзакций.  
  
         \- Агент чтения очереди для публикаций транзакций, допускающих обновляемые подписки.  
  
         Дополнительные сведения см. в разделах [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) и [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   При необходимости создайте скрипт для публикации. Дополнительные сведения см. в разделе [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Задайте имя для публикации.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 После создания публикации статьи можно создавать программно с помощью хранимых процедур репликации. Конкретные хранимые процедуры, применяемые для создания статей, будут зависеть от типа публикации, для которого определена статья. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### Определение статьи для публикации транзакций или моментальных снимков  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md). Укажите имя публикации, к которой принадлежит статья, для **@publication**, имя статьи для **@article**, объект базы данных, публикуемые для **@source_object**, и необязательные параметры. Используйте **@source_owner** Указание владельца схемы объекта, если не **dbo**. Если статья не статьи таблицы на основе журнала, укажите тип статьи для **@type**; Дополнительные сведения см. в разделе [задать типы статей & #40; Программирование репликации Transact-SQL & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  Для горизонтальной фильтрации строк в таблице или просмотреть статью, используйте [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) определения предложения фильтра. Дополнительные сведения см. в статье [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Для вертикальной фильтрации столбцов в таблице или просмотреть статью, используйте [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Дополнительные сведения см. в статье [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
4.  Выполнение [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) Если статья отфильтрована.  
  
5.  Если публикация содержит существующие подписки и [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) возвращает значение **0** в **immediate_sync** столбец, необходимо вызвать метод [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) Добавить статью в каждую существующую подписку.  
  
6.  Если в публикации есть подписки по запросу, выполните [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) на стороне издателя, чтобы создать новый моментальный снимок для существующих подписок по запросу, который содержит только новую статью.  
  
    > [!NOTE]  
    >  Для подписок, которые не были инициализированы с помощью моментального снимка, не нужно выполнять [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) как эта процедура выполняется по [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
#### Определение статьи для публикации слиянием  
  
1.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите имя публикации, для **@publication**, имя статьи для **@article**, и выполняется публикация для объекта **@source_object**. Для горизонтальной фильтрации строк таблицы, укажите значение для **@subset_filterclause**. Дополнительные сведения см. в разделах [Define and Modify a Parameterized Row Filter for a Merge Article](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) и [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md). Если статья не является статьей таблицы, укажите ее тип в качестве значения параметра **@type**. Дополнительные сведения см. в разделе [задать типы статей & #40; Программирование репликации Transact-SQL & #41;](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  (Необязательно) На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) Определение фильтра соединения между двумя статьями. Дополнительные сведения см. в статье [Define and Modify a Join Filter Between Merge Articles](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  (Необязательно) На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) для фильтрации столбцов таблицы. Дополнительные сведения см. в статье [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере определяется статья на основе таблицы `Product` для публикации транзакций, причем статья фильтруется как по горизонтали, так и по вертикали.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 В этом примере определяются статьи для публикации слиянием, причем статья `SalesOrderHeader` фильтруется статически на основе идентификатора **SalesPersonID**, а к статье `SalesOrderDetail` применяется фильтр соединения на основе `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Статьи можно определять программно с помощью объектов RMO. Классы RMO, с помощью которых создается статья, зависят от типа публикации, для которого эта статья определяется.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В приведенном ниже примере в публикацию транзакций добавляется статья с фильтрами строк и столбцов.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 В приведенном ниже примере в публикацию слиянием добавляется три статьи. Статьи содержат фильтры столбцов, а два фильтра соединения используются для заполнения параметризованных фильтров строк в других статьях.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## См. также:  
 [Создание публикации](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Основные понятия системных хранимых процедур репликации](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  