---
title: Определение статьи | Документация Майкрософт
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 5d7ff1f5f516d438ed07a203223acf32970a7961
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065767"
---
# <a name="define-an-article"></a>Определение статьи
  В данном разделе описывается определение статьи в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)]или объектов RMO.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для определения статьи используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [объекты RMO;](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Названия статей не могут содержать следующие символы: % , * , [ , ] , | , : , " , ? , ' , \ , / , \< , >. Если объекты в базе данных, содержащие любые из этих символов, нужно реплицировать, необходимо задать для статьи имя, отличное от имени объекта.  
  
##  <a name="security"></a><a name="Security"></a> безопасность  
 По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. Если необходимо хранить учетные данные, используйте [службы шифрования](https://go.microsoft.com/fwlink/?LinkId=34733) , предоставляемые платформой [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows .NET Framework.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Создание публикаций и определение статей осуществляется с помощью мастера создания публикаций. После создания публикации просмотрите и измените свойства публикации в диалоговом окне **Свойства публикации — \<Publication> ** . Дополнительные сведения о создании публикаций из базы данных Oracle вы найдете в [этой статье](create-a-publication-from-an-oracle-database.md).  
  
#### <a name="to-create-a-publication-and-define-articles"></a>Создание публикации и определение статей  
  
1.  Подключитесь к издателю в среде [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем щелкните правой кнопкой мыши папку **Локальные публикации** .  
  
3.  Щелкните **Создать публикацию**.  
  
4.  Следуйте указаниям на страницах мастера создания публикаций, чтобы:  
  
    -   задать распространитель, если распространение не было настроено на сервере. Дополнительные сведения о настройке распространения см. в статье [Настройка публикации и распространения](../configure-publishing-and-distribution.md).  
  
         Если на странице **Распространитель** вы задаете, что сервер издателя буде функционировать как свой собственный распространитель (локальный распространитель), а сервер не настроен в качестве распространителя, то мастер создания публикаций произведет настройку сервера. Нужно будет задать для распространителя папку моментальных снимков по умолчанию на странице **Папка моментальных снимков** . Папка моментальных снимков — это просто каталог, назначенный для совместного использования; агенты, считывающие и записывающие данные в эту папку, должны иметь достаточные разрешения для доступа к ней. Дополнительные сведения о надлежащей защите папок см. в статье [Организация безопасности папки моментальных снимков](../security/secure-the-snapshot-folder.md).  
  
         Если задано, что в качестве распространителя будет функционировать другой сервер, необходимо ввести пароль на странице **Административный пароль** для соединений, устанавливаемых между издателем и распространителем. Пароль должен совпадать с паролем, указанным при включении издателя на удаленном распространителе.  
  
         Дополнительные сведения см. в разделе [Configure Distribution](../configure-distribution.md).  
  
    -   Выберите базу данных публикации.  
  
    -   Выберите тип публикации. Дополнительные сведения см. в статье [Типы репликации](../types-of-replication.md).  
  
    -   Задайте данные и объекты базы данных для публикации. При необходимости отфильтруйте столбцы из статей таблиц и установите свойства статей.  
  
    -   Если требуется, отфильтруйте строки из статей таблиц. Дополнительные сведения см. в статье [Фильтрация опубликованных данных](filter-published-data.md).  
  
    -   Настройте расписание для агента моментальных снимков.  
  
    -   Задайте учетные данные, под которыми следующие агенты репликации будут запускаться и устанавливать соединения:  
  
         — агент моментальных снимков для всех публикаций;  
  
         — агент чтения журнала для всех публикаций транзакций;  
  
         — агент чтения очереди для публикаций транзакций, допускающих обновление подписок.  
  
         Дополнительные сведения см. в разделах [Replication Agent Security Model](../security/replication-agent-security-model.md) и [Replication Security Best Practices](../security/replication-security-best-practices.md).  
  
    -   При необходимости создайте скрипт для публикации. Дополнительные сведения см. в разделе [Scripting Replication](../scripting-replication.md).  
  
    -   Задайте имя для публикации.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
 После создания публикации статьи можно создавать программно с помощью хранимых процедур репликации. Конкретные хранимые процедуры, применяемые для создания статей, будут зависеть от типа публикации, для которого определена статья. Дополнительные сведения см. в разделе [Create a Publication](create-a-publication.md).  
  
#### <a name="to-define-an-article-for-a-snapshot-or-transactional-publication"></a>Определение статьи для публикации транзакций или моментальных снимков  
  
1.  Выполните процедуру [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql)на издателе в базе данных публикации. Укажите имя публикации, которой принадлежит статья для ** \@ публикации**, имя статьи для ** \@ статьи**, публикуемый объект базы данных для ** \@ source_object**и любые другие необязательные параметры. Используйте ** \@ source_owner** , чтобы указать владение схемой объекта, если нет — **dbo**. Если статья не является статьей таблицы, основанной на журнале, укажите тип статьи для ** \@ типа**. Дополнительные сведения см. в разделе [Указание типов статей &#40;программирование репликации на языке Transact-SQL&#41;](specify-article-types-replication-transact-sql-programming.md).  
  
2.  Для горизонтальной фильтрации строк в таблице или для просмотра статьи используйте хранимую процедуру [sp_articlefilter](/sql/relational-databases/system-stored-procedures/sp-articlefilter-transact-sql) , определяющую предложение фильтра. Дополнительные сведения см. в разделе [Define and Modify a Static Row Filter](define-and-modify-a-static-row-filter.md).  
  
3.  Для вертикальной фильтрации столбцов в таблице или просмотра статьи используйте хранимую процедуру [sp_articlecolumn](/sql/relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql). Дополнительные сведения см. в разделе [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
4.  Если статья является фильтруемой, выполните хранимую процедуру [sp_articleview](/sql/relational-databases/system-stored-procedures/sp-articleview-transact-sql) .  
  
5.  Если публикация содержит существующие подписки и хранимая процедура [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql) возвращает значение **0** в столбце **immediate_sync** , то необходимо с помощью хранимой процедуры [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) добавить статью в каждую существующую подписку.  
  
6.  Если в публикации есть подписки по запросу, выполните хранимую процедуру [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) на издателе для создания нового моментального снимка для существующих подписок по запросу, содержащего только новую статью.  
  
    > [!NOTE]  
    >  Для подписок, которые не были инициализированы с помощью моментального снимка, нет необходимости выполнять хранимую процедуру [sp_refreshsubscriptions](/sql/relational-databases/system-stored-procedures/sp-refreshsubscriptions-transact-sql) , поскольку она выполняется процедурой [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql).  
  
#### <a name="to-define-an-article-for-a-merge-publication"></a>Определение статьи для публикации слиянием  
  
1.  В базе данных публикации на издателе выполните процедуру [sp_addmergearticle](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql). Укажите имя публикации для ** \@ публикации**, имя статьи для ** \@ статьи**и публикуемый объект для ** \@ source_object**. Чтобы горизонтально фильтровать строки таблицы, укажите значение для ** \@ subset_filterclause**. Дополнительные сведения см. в разделах [Определение и изменение параметризованного фильтра строк для статьи публикации слиянием](define-and-modify-a-parameterized-row-filter-for-a-merge-article.md) и [Определение и изменение статического строкового фильтра](define-and-modify-a-static-row-filter.md). Если статья не является статьей таблицы, укажите тип статьи для ** \@ типа**. Дополнительные сведения см. в статье [Определение типов статей (программирование репликации на языке Transact-SQL)](specify-article-types-replication-transact-sql-programming.md).  
  
2.  Чтобы определить фильтр соединения между двумя статьями, на издателе в базе данных публикации выполните процедуру [sp_addmergefilter](/sql/relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql) (необязательно). Дополнительные сведения см. в статье [Определение и изменение фильтра соединения между статьями публикации слиянием](define-and-modify-a-join-filter-between-merge-articles.md).  
  
3.  На издателе в базе данных публикации выполните хранимую процедуру [sp_mergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-mergearticlecolumn-transact-sql) для фильтрации столбцов таблицы (необязательно). Дополнительные сведения см. в разделе [Define and Modify a Column Filter](define-and-modify-a-column-filter.md).  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> Примеры (Transact-SQL)  
 В этом примере определяется статья на основе таблицы `Product` для публикации транзакций, причем статья фильтруется как по горизонтали, так и по вертикали.  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createtranpub.sql#sp_addtranarticle)]  
  
 В этом примере определяются статьи для публикации слиянием, причем статья `SalesOrderHeader` фильтруется статически на основе идентификатора **SalesPersonID**, а к статье `SalesOrderDetail` применяется фильтр соединения на основе `SalesOrderHeader`.  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../snippets/tsql/SQL15/replication/howto/tsql/createmergepub.sql#sp_addmergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> При помощи объектов RMO  
 Статьи можно определять программно с помощью объектов RMO. Классы RMO, с помощью которых создается статья, зависят от типа публикации, для которого эта статья определяется.  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> Примеры (объекты RMO)  
 В приведенном ниже примере в публикацию транзакций добавляется статья с фильтрами строк и столбцов.  
  
 [!code-csharp[HowTo#rmo_CreateTranArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createtranarticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateTranArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createtranarticles)]  
  
 В приведенном ниже примере в публикацию слиянием добавляется три статьи. Статьи содержат фильтры столбцов, а два фильтра соединения используются для заполнения параметризованных фильтров строк в других статьях.  
  
 [!code-csharp[HowTo#rmo_CreateMergeArticles](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_createmergearticles)]  
  
 [!code-vb[HowTo#rmo_vb_CreateMergeArticles](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_createmergearticles)]  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](create-a-publication.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)   
 [Добавление и удаление статей в существующих публикациях](add-articles-to-and-drop-articles-from-existing-publications.md)   
 [Фильтрация опубликованных данных](filter-published-data.md)   
 [Публикация данных и объектов базы данных](publish-data-and-database-objects.md)   
 [Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
