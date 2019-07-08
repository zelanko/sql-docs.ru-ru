---
title: Определение статьи | Документация Майкрософт
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
- articles [SQL Server replication], defining
- sp_addmergearticle
- adding articles
- sp_addarticle
- articles [SQL Server replication], adding
ms.assetid: 220584d8-b291-43ae-b036-fbba3cc07a2e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e5ee2fcc90061bbd003081f747fb7f4a50b6755f
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2019
ms.locfileid: "67585825"
---
# <a name="define-an-article"></a>Определение статьи
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается определение статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Для определения статьи используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Названия статей не могут содержать следующие символы: % , * , [ , ] , | , : , " , ? , ' , \ , / , < , >. Если объекты в базе данных, содержащие любые из этих символов, нужно реплицировать, необходимо задать для статьи имя, отличное от имени объекта.  
  
##  <a name="Security"></a> безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание публикаций и определение статей осуществляется с помощью мастера создания публикаций. После создания публикации вы можете просмотреть и изменить ее свойства в диалоговом окне **Свойства публикации — \<публикация>** . Дополнительные сведения о создании публикаций из базы данных Oracle вы найдете в [этой статье](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
#### <a name="to-create-a-publication-and-define-articles"></a>Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]и раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем щелкните правой кнопкой мыши папку **Локальные публикации** .  
  
3.  Щелкните **Создать публикацию**.  
  
4.  Следуйте указаниям на страницах мастера создания публикаций, чтобы:  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

    -   задать распространитель, если распространение не было настроено на сервере. Дополнительные сведения о настройке распространения см. в статье [Настройка публикации и распространения](../../../relational-databases/replication/configure-publishing-and-distribution.md).  
  
         Если на странице **Распространитель** вы задаете, что сервер издателя буде функционировать как свой собственный распространитель (локальный распространитель), а сервер не настроен в качестве распространителя, то мастер создания публикаций произведет настройку сервера. Нужно будет задать для распространителя папку моментальных снимков по умолчанию на странице **Папка моментальных снимков** . Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
         Если задано, что в качестве распространителя будет функционировать другой сервер, необходимо ввести пароль на странице **Административный пароль** для соединений, устанавливаемых между издателем и распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
         Дополнительные сведения см. в разделе [Configure Distribution](../../../relational-databases/replication/configure-distribution.md).  
  
    -   Выберите базу данных публикации.  
  
    -   Выберите тип публикации. Дополнительные сведения см. в статье [Типы репликации](../../../relational-databases/replication/types-of-replication.md).  
  
    -   Задайте данные и объекты базы данных для публикации. При необходимости отфильтруйте столбцы из статей таблиц и установите свойства статей.  
  
    -   Если требуется, отфильтруйте строки из статей таблиц. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md).  
  
    -   Настройте расписание для агента моментальных снимков.  
  
    -   Задайте учетные данные, под которыми следующие агенты репликации будут запускаться и устанавливать соединения:  
  
         — агент моментальных снимков для всех публикаций;  
  
         — агент чтения журнала для всех публикаций транзакций;  
  
         — агент чтения очереди для публикаций транзакций, допускающих обновление подписок.  
  
         Дополнительные сведения см. в разделах [Replication Agent Security Model](../../../relational-databases/replication/security/replication-agent-security-model.md) и [Replication Security Best Practices](../../../relational-databases/replication/security/replication-security-best-practices.md).  
  
    -   При необходимости создайте скрипт для публикации. Дополнительные сведения см. в разделе [Scripting Replication](../../../relational-databases/replication/scripting-replication.md).  
  
    -   Задайте имя для публикации.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 После создания публикации статьи можно создавать программно с помощью хранимых процедур репликации. Конкретные хранимые процедуры, применяемые для создания статей, будут зависеть от типа публикации, для которого определена статья. Дополнительные сведения см. в разделе [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md).  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>Определение статьи для публикации транзакций или моментальных снимков  
  
1.  Выполните процедуру [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)на издателе в базе данных публикации. Укажите имя публикации, которой принадлежит статья, в качестве значения параметра **@publication** , имя статьи в качестве значения параметра **@article** , публикуемый объект базы данных в качестве значения параметра **@source_object** , а также, при необходимости, другие параметры. С помощью параметра **@source_owner** задайте принадлежность схемы объекта. Если она отсутствует, то **dbo**. Если статья не является статьей таблицы, основанной на журнале, укажите тип статьи в качестве значения параметра **@type** . Дополнительные сведения см. в статье [Определение типов статей (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  Для горизонтальной фильтрации строк в таблице или для просмотра статьи используйте хранимую процедуру [sp_articlefilter](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md) , определяющую предложение фильтра. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md).  
  
3.  Для вертикальной фильтрации столбцов в таблице или просмотра статьи используйте хранимую процедуру [sp_articlecolumn](../../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md). Дополнительные сведения см. в разделе [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
4.  Если статья является фильтруемой, выполните хранимую процедуру [sp_articleview](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md) .  
  
5.  Если публикация содержит существующие подписки и хранимая процедура [sp_helppublication](../../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md) возвращает значение **0** в столбце **immediate_sync** , то необходимо с помощью хранимой процедуры [sp_addsubscription](../../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) добавить статью в каждую существующую подписку.  
  
6.  Если в публикации есть подписки по запросу, выполните хранимую процедуру [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) на издателе для создания нового моментального снимка для существующих подписок по запросу, содержащего только новую статью.  
  
    > [!NOTE]  
    >  Для подписок, которые не были инициализированы с помощью моментального снимка, нет необходимости выполнять хранимую процедуру [sp_refreshsubscriptions](../../../relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql.md) , поскольку она выполняется процедурой [sp_addarticle](../../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md).  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>Определение статьи для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите имя публикации в качестве значения параметра **@publication** , имя статьи в качестве значения параметра **@article** , а также публикуемый объект в качестве значения параметра **@source_object** . Для горизонтальной фильтрации строк таблицы укажите значение параметра **@subset_filterclause** . Дополнительные сведения см. в разделах [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) и [Определение и изменение статического строкового фильтра](../../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md). Если статья не является статьей таблицы, укажите ее тип в качестве значения параметра **@type** . Дополнительные сведения см. в статье [Определение типов статей (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/publish/specify-article-types-replication-transact-sql-programming.md).  
  
2.  Чтобы определить фильтр соединения между двумя статьями, на издателе в базе данных публикации выполните процедуру [sp_addmergefilter](../../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md) (необязательно). Дополнительные сведения см. в разделе [Определение и изменение фильтра соединения между статьями публикации слиянием](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](../../../relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql.md) для фильтрации столбцов таблицы (необязательно). Дополнительные сведения см. в разделе [Define and Modify a Column Filter](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md).  
  
###  <a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере определяется статья на основе таблицы `Product` для публикации транзакций, причем статья фильтруется как по горизонтали, так и по вертикали.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_1.sql)]  
  
 В этом примере определяются статьи для публикации слиянием, причем статья `SalesOrderHeader` фильтруется статически на основе идентификатора **SalesPersonID**, а к статье `SalesOrderDetail` применяется фильтр соединения на основе `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-an-article_2.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
 Статьи можно определять программно с помощью объектов RMO. Классы RMO, с помощью которых создается статья, зависят от типа публикации, для которого эта статья определяется.  
  
###  <a name="PShellExample"></a> Примеры (объекты RMO)  
 В приведенном ниже примере в публикацию транзакций добавляется статья с фильтрами строк и столбцов.  
  
 [!code-cs[HowTo#rmo_CreateTranArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 В приведенном ниже примере в публикацию слиянием добавляется три статьи. Статьи содержат фильтры столбцов, а два фильтра соединения используются для заполнения параметризованных фильтров строк в других статьях.  
  
 [!code-cs[HowTo#rmo_CreateMergeArticles](../../../relational-databases/replication/codesnippet/csharp/rmohowto/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../relational-databases/replication/codesnippet/visualbasic/rmohowtovb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../../relational-databases/replication/publish/create-a-publication.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Добавление и удаление статей в существующих публикациях](../../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Фильтрация опубликованных данных](../../../relational-databases/replication/publish/filter-published-data.md)   
 [Публикация данных и объектов базы данных](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)  
  
  
