---
title: Реализация пользовательского арбитра конфликтов для статьи слиянием | Документация Майкрософт
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
- merge replication conflict resolution [SQL Server replication], stored procedure-based resolvers
- articles [SQL Server replication], conflict resolution
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 76bd8524-ebc1-4d80-b5a2-4169944d6ac0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b36d610912f518f0586739e0380e300efefbed40
ms.sourcegitcommit: 3d189b68c0965909d167de61546b574af1ef7a96
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69561135"
---
# <a name="implement-a-custom-conflict-resolver-for-a-merge-article"></a>Реализация пользовательского арбитра конфликтов для статьи слиянием
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В этом разделе описано, как реализовать пользовательский арбитр конфликтов для статьи слияния в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или [пользовательского арбитра конфликтов на основе COM](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md).  
  
 **В этом разделе**  
  
-   **Реализация пользовательского арбитра конфликтов для статьи слияния с помощью следующих средств:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Арбитр конфликтов на основе COM](#COM)  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Собственный пользовательский арбитр конфликтов можно записать в виде хранимой процедуры [!INCLUDE[tsql](../../includes/tsql-md.md)] на каждом издателе. При синхронизации эта хранимая процедура вызывается, когда обнаруживаются конфликты в статье, в которой был зарегистрирован арбитр. Агент слияния передает сведения о конфликтной строке в необходимые параметры процедуры. Пользовательские сопоставители конфликтов на основе хранимых процедур всегда создаются на издателе.  
  
> [!NOTE]  
>  Арбитры конфликтов хранимых процедур [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызываются только для обработки конфликтов, связанных с изменением строк. Их нельзя использовать для обработки других типов конфликтов, таких как ошибки вставки, возникшие из-за нарушения ограничений PRIMARY KEY или ограничений уникального индекса.
  
#### <a name="to-create-a-stored-procedure-based-custom-conflict-resolver"></a>Создание пользовательского сопоставителя конфликтов на основе хранимых процедур  
  
1.  На издателе в базе данных публикации или **msdb** создайте новую системную хранимую процедуру, реализующую следующие обязательные параметры.  
  
    |Параметр|Тип данных|Описание|  
    |---------------|---------------|-----------------|  
    |**\@tableowner**|**sysname**|Имя владельца таблицы, в которой разрешается конфликт. Это владелец таблицы в базе данных публикации.|  
    |**\@tablename**|**sysname**|Имя таблицы, в которой разрешается конфликт.|  
    |**\@rowguid**|**uniqueidentifier**|Уникальный идентификатор для конфликтной строки.|  
    |**\@subscriber**|**sysname**|Имя сервера, с которого распространяется вызвавшее конфликт изменение.|  
    |**\@subscriber_db**|**sysname**|Имя базы данных, с которой распространяется вызвавшее конфликт изменение.|  
    |**\@log_conflict OUTPUT**|**int**|Указывает, нужно ли в процессе слияния регистрировать конфликт для последующего разрешения.<br /><br /> **0** = не регистрировать конфликт.<br /><br /> **1** = разрешение конфликта в пользу издателя.<br /><br /> **2** = разрешение конфликта в пользу подписчика.|  
    |**\@conflict_message OUTPUT**|**nvarchar(512)**|Сообщения, которые должны быть выданы о разрешении конфликта, если конфликт был зарегистрирован.|  
    |**\@destowner**|**sysname**|Владелец опубликованной таблицы на подписчике.|  
  
     Эта хранимая процедура использует значения, которые агент слияния передает в эти параметры для реализации пользовательской логики разрешения конфликтов. Процедура должна вернуть результирующий набор для одной строки, который имеет такую же структуру, как и базовая таблица, и содержит значения данных для приоритетной версии строки.  
  
2.  Предоставьте разрешения EXECUTE на хранимую процедуру любым именам входа, используемым подписчиками для соединения с издателем.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

#### <a name="use-a-custom-conflict-resolver-with-a-new-table-article"></a>Применение пользовательского арбитра конфликтов с новой статьей таблицы  
  
1. Выполните [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) для определения статьи. 
1. Для параметра **\@article_resolver** укажите значение **MicrosoftSQL** **Server Stored Procedure Resolver**. 
1. Для параметра **\@resolver_info** укажите имя хранимой процедуры, реализующей логику разрешения конфликтов. 

   Дополнительные сведения см. в статье [Определение статьи](../../relational-databases/replication/publish/define-an-article.md).
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  Выполните процедуру [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md). При этом укажите параметры **\@publication**, **\@article**, значение **article_resolver** в параметре **\@property** и значение **MicrosoftSQL** **Server Stored ProcedureResolver** в параметре **\@value**.  
  
2.  Выполните хранимую процедуру [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав параметры **\@publication**, **\@article**, значение **resolver_info** в параметре **\@property** и имя хранимой процедуры, реализующей логику арбитра конфликтов, в параметре **\@value**.  
  
##  <a name="COM"></a> Использование пользовательского арбитра конфликтов на основе COM  
 Пространство имен <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport> реализует интерфейс, позволяющий создавать сложную бизнес-логику для обработки событий и разрешения конфликтов, возникающих при синхронизации репликации слиянием. Дополнительные сведения см. в руководстве по [реализации обработчика бизнес-логики для статьи слияния](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md). Для разрешения конфликтов можно записать в машинном коде собственную бизнес-логику. Эта логика построена как COM-компонент. Она компилируется в динамические библиотеки (DLL) с помощью таких продуктов, как [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C++. Такой арбитр конфликтов на основе COM должен реализовывать интерфейс **ICustomResolver**, спроектированный специально для разрешения конфликтов.  
  
#### <a name="to-create-and-register-a-com-based-custom-conflict-resolver"></a>Создание и регистрация пользовательского сопоставителя конфликтов на основе COM  
  
1.  В COM-совместимой среде разработчика добавьте ссылки на библиотеку пользовательского сопоставителя.  
  
2.  В проекте Visual C++ используйте директиву #import для импорта этой библиотеки.  
  
3.  Создайте класс, реализующий интерфейс **ICustomResolver** .  
  
4.  Обеспечьте выполнение соответствующих методов и свойств.  
  
5.  Постройте проект, создающий файл библиотеки пользовательского сопоставителя.  
  
6.  Разверните эту библиотеку в каталоге, содержащем исполняемый файл агента слияния (обычно \Microsoft SQL Server\100\COM).  
  
    > [!NOTE]  
    >  Пользовательский сопоставитель конфликтов необходимо развернуть на подписчике для подписки по запросу, на распространителе для принудительной подписки или на веб-сервере, который используется для веб-синхронизации.  
  
7.  Зарегистрируйте библиотеку пользовательского арбитра конфликтов с помощью программы regsvr32.exe из каталога развертывания следующим образом:  
  
    ```  
    regsvr32.exe mycustomresolver.dll  
    ```  
  
8.  В издателе выполните хранимую процедуру [sp_enumcustomresolvers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md), чтобы проверить, не зарегистрирована ли уже эта библиотека в качестве пользовательского арбитра конфликтов.  
  
9. Чтобы зарегистрировать библиотеку в качестве пользовательского арбитра конфликтов, выполните хранимую процедуру [sp_registercustomresolver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md) в распространителе. Укажите понятное имя COM-объекта в параметре **\@article_resolver**, идентификатор библиотеки (CLSID) в параметре **\@resolver_clsid** и значение **false** в параметре **\@is_dotnet_assembly**.  
  
    > [!NOTE]  
    >  Если пользовательский арбитр конфликтов больше не нужен, вы можете отменить его регистрацию с помощью хранимой процедуры [sp_unregistercustomresolver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md).  
  
10. (Необязательно) В кластере повторите шаги 6–9, чтобы зарегистрировать пользовательский арбитр на всех узлах кластера. Эти шаги нужны для того, чтобы пользовательский арбитр смог правильно загрузить посредник после отработки отказа.
  
#### <a name="to-use-a-custom-conflict-resolver-with-a-new-table-article"></a>Использование нестандартного сопоставителя конфликтов с новой статьей таблицы  
  
1.  Выполните процедуру [sp_enumcustomresolvers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) в издателе и запомните понятное имя требуемого арбитра.  
  
2.  Чтобы определить статью, в базе данных публикации издателя выполните процедуру [sp_addmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md). Укажите понятное имя сопоставителя статей из шага 1 в параметре **\@article_resolver**. Дополнительные сведения см. в статье [Определение статьи](../../relational-databases/replication/publish/define-an-article.md).  
  
#### <a name="to-use-a-custom-conflict-resolver-with-an-existing-table-article"></a>Использование нестандартного сопоставителя конфликтов с существующей статьей таблицы  
  
1.  Выполните процедуру [sp_enumcustomresolvers (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-enumcustomresolvers-transact-sql.md) в издателе и запомните понятное имя требуемого арбитра.  
  
2.  Выполните хранимую процедуру [sp_changemergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md), указав параметры **\@publication**, **\@article**, значение **article_resolver** в параметре **\@property** и понятное имя сопоставителя статей из шага 1 в параметре **\@value**.  
  

## <a name="see-also"></a>См. также раздел  
 [Подробнее о репликации слиянием — обнаружение и разрешение конфликтов](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Пользовательские арбитры на основе технологии COM](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-custom-resolvers.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
