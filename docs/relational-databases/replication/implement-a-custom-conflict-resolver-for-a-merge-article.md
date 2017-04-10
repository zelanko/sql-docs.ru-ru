---
title: "Implement a Custom Conflict Resolver for a Merge Article | Microsoft Docs"
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
  - "merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers"
  - "articles [SQL Server replication], conflict resolution"
  - "разрешение конфликтов [репликация SQL Server], репликация слиянием"
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 44
---
# Implement a Custom Conflict Resolver for a Merge Article
  В этом разделе описывается реализация пользовательского арбитра конфликтов для статьи публикации слиянием в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или [пользовательского арбитра конфликтов на основе COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md).  
  
 **В этом разделе**  
  
-   **Для реализации пользовательского арбитра конфликтов для статьи публикации слиянием используется:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Арбитр конфликтов на основе COM](#COM)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Собственный пользовательский арбитр конфликтов можно записать в виде хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] на каждом издателе. Во время синхронизации эта хранимая процедура вызывается при возникновении конфликтов в статье, для которой был зарегистрирован сопоставитель, и данные о строке с конфликтом передаются агентом слияния в необходимые параметры этой процедуры. Пользовательские сопоставители конфликтов на основе хранимых процедур всегда создаются на издателе.  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] арбитры хранимые процедуры вызываются только для обработки конфликтов на основе изменения строк. Их нельзя использовать для обработки других типов конфликтов, таких как ошибки вставки, возникшие из-за нарушения ограничений PRIMARY KEY или ограничений уникального индекса.  
  
#### Создание пользовательского сопоставителя конфликтов на основе хранимых процедур  
  
1.  На издателе в базе данных публикации или **msdb** создайте новую системную хранимую процедуру, реализующую следующие обязательные параметры.  
  
    |Параметр|Тип данных|Описание|  
    |---------------|---------------|-----------------|  
    |**@tableowner**|**sysname**|Имя владельца таблицы, в которой разрешается конфликт. Это владелец таблицы в базе данных публикации.|  
    |**@tablename**|**sysname**|Имя таблицы, в которой разрешается конфликт.|  
    |**@rowguid**|**uniqueidentifier**|Уникальный идентификатор строки конфликта.|  
    |**@subscriber**|**sysname**|Имя сервера, с которого распространяется вызвавшее конфликт изменение.|  
    |**@subscriber_db**|**sysname**|Имя базы данных, из которой распространяется вызвавшее конфликт изменение.|  
    |**@log_conflict OUTPUT**|**int**|Определяет, должен ли процесс слияния зарегистрировать конфликт для последующего разрешения.<br /><br /> **0** = не регистрировать конфликт.<br /><br /> **1** = подписчик — конфликта в пользу издателя.<br /><br /> **2** = издатель — конфликта в пользу издателя.|  
    |**@conflict_message OUTPUT**|**nvarchar(512)**|Сообщения, которые должны быть выданы о разрешении конфликта, если конфликт был зарегистрирован.|  
    |**@destowner**|**sysname**|Владелец опубликованной таблицы на подписчике.|  
  
     Эта хранимая процедура использует значения, переданные агентом слияния этим параметрам для применения пользовательской логики устранения конфликтов. Она должна вернуть результирующий набор, содержащий одну строку, соответствующий структуре базовой таблицы и содержащий значения данных для приоритетной версии строки.  
  
2.  Предоставьте разрешения EXECUTE на хранимую процедуру любым именам входа, используемым подписчиками для соединения с издателем.  
  
#### Использование нестандартного сопоставителя конфликтов с новой статьей таблицы  
  
1.  Выполнение [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Определение статьи, указав значение **MicrosoftSQL** **Server арбитра конфликтов хранимых процедур** для **@article_resolver** и имя хранимой процедуры, реализующей логику арбитра конфликтов для **@resolver_info** параметр. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  Выполнение [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав **@publication**, **@article**, значение **article_resolver** для **@property**, а значение **MicrosoftSQL** **ProcedureResolver хранятся сервера** для **@value**.  
  
2.  Выполнение [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав **@publication**, **@article**, значение **resolver_info** для **@property**, и имя хранимой процедуры, реализующей логику арбитра конфликтов для **@value**.  
  
##  <a name="COM"></a> При помощи пользовательского арбитра конфликтов на основе COM  
  <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> имен реализует интерфейс, который позволяет создавать сложные бизнес-логику для обработки событий и разрешения конфликтов, возникающих во время синхронизации репликации слиянием. Дополнительные сведения см. в статье [Implement a Business Logic Handler for a Merge Article](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md). Для разрешения конфликтов можно записать в машинном коде собственную бизнес-логику. Эта логика построена как COM-компонент и компилируется в динамические библиотеки (DLL) с помощью таких продуктов, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++. Сопоставитель конфликтов на основе COM — необходимо реализовать **ICustomResolver** интерфейс, который разработан специально для разрешения конфликтов.  
  
#### Создание и регистрация пользовательского сопоставителя конфликтов на основе COM  
  
1.  В COM-совместимой среде разработчика добавьте ссылки на библиотеку пользовательского сопоставителя.  
  
2.  В проекте Visual C++ используйте директиву #import для импорта этой библиотеки.  
  
3.  Создайте класс, реализующий интерфейс **ICustomResolver** .  
  
4.  Обеспечьте выполнение соответствующих методов и свойств.  
  
5.  Постройте проект, создающий файл библиотеки пользовательского сопоставителя.  
  
6.  Разверните эту библиотеку в каталоге, содержащем исполняемый файл агента слияния (обычно «\Microsoft SQL Server\100\COM»).  
  
    > [!NOTE]  
    >  Пользовательский сопоставитель конфликтов необходимо развернуть на подписчике для подписки по запросу, на распространителе для принудительной подписки или на веб-сервере, который используется для веб-синхронизации.  
  
7.  Зарегистрируйте библиотеку пользовательского сопоставителя конфликтов с помощью программы regsvr32.exe из каталога развертывания следующим образом.  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) Чтобы убедиться, что библиотека не зарегистрирована как пользовательского арбитра конфликтов.  
  
9. Чтобы зарегистрировать библиотеку в качестве пользовательского арбитра конфликтов, выполните [работу sp_registercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md), на распространителе. Укажите понятное имя COM-объект для **@article_resolver**, идентификатор библиотеки (CLSID) для **@resolver_clsid**, а значение **false** для **@is_dotnet_assembly**.  
  
    > [!NOTE]  
    >  Если больше не требуется, можно отменить его регистрацию с помощью пользовательского арбитра конфликтов [sp_unregistercustomresolver & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md).  
  
10. В кластере повторите шаги 5-8, чтобы зарегистрировать пользовательский сопоставитель на всех узлах кластера (необязательно). Это нужно для того, чтобы пользовательский сопоставитель смог правильно загрузить посредник после отработки отказа.  
  
#### Использование нестандартного сопоставителя конфликтов с новой статьей таблицы  
  
1.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) и запомните понятное имя требуемого сопоставителя.  
  
2.  На издателе в базе данных публикации выполните хранимую процедуру [sp_addmergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) Чтобы определить статью. Укажите понятное имя арбитра статей из шага 1 для **@article_resolver**. Дополнительные сведения см. в статье [Define an Article](../../relational-databases/replication/publish/define-an-article.md).  
  
#### Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  На издателе, хранимую [sp_enumcustomresolvers & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) и запомните понятное имя требуемого сопоставителя.  
  
2.  Выполнение [sp_changemergearticle & #40; Transact-SQL & #41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав **@publication**, **@article**, значение **article_resolver** для **@property**, и понятное имя арбитра статей из шага 1 для **@value**.  
  
#### Просмотр образца пользовательского сопоставителя  
  
1.  Пример доступен в образцах файлов SQL Server 2000. Загрузите файл **sql2000samples.cab** из [обновленных образцов для пакета обновления 3 (SP3) для SQL Server 2000](http://www.microsoft.com/download/details.aspx?id=8560). Будет загружено 8 файлов общим размером 6,9 МБ.  
  
2.  Извлеките файлы из загруженного сжатого CAB-файла.  
  
3.  Выполнить **setup.exe**  
  
    > [!NOTE]  
    >  При выборе параметров установки необходимо установить только образцы **Репликации** . (Путь установки по умолчанию — **C:\Program файлы (x86) \Microsoft SQL Server 2000 Samples\1033\\**)  
  
4.  Перейдите в папку установки. (По умолчанию используется папка **C:\Program файлы (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\unzip_sqlreplSP3.exe**)  
  
5.  Запустите **unzip_sqlreplSP3.exe** программы.  
  
    > [!NOTE]  
    >  Пример com-сопоставителя будет установлен (по умолчанию) для **C:\Program Files (x86) \Microsoft SQL Server 2000 Samples\1033\sqlrepl\resolver\subspres** папки.  
  
6.  В **subspres** папки, поиск всех вхождений **#include sqlres.h** во всех исходных файлов и замените их на **no_namespace #import «replrec.dll», raw_interfaces_only**  
  
## См. также:  
 [Расширенное обнаружение и разрешение конфликтов репликации слиянием](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Пользовательские сопоставители на основе технологии COM](../../relational-databases/replication/merge/com-based-custom-resolvers.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  