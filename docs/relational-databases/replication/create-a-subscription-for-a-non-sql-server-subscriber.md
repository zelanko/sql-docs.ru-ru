---
title: Создание подписки для подписчика, отличного от подписчика SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers, subscriptions
ms.assetid: 5020ee68-b988-4d57-8066-67d183e61237
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d199fff8243584ee86dd97f97bcc3b8b68beb3dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063108"
---
# <a name="create-a-subscription-for-a-non-sql-server-subscriber"></a>Создание подписки для подписчика, отличного от подписчика SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  В данном разделе описывается процесс создания подписки в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] для подписчика, отличного от подписчика SQL Server, с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Репликация транзакций и репликация моментальных снимков поддерживают публикацию данных в подписчиках, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Сведения о поддерживаемых платформах подписчиков см. в разделе [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
 **В этом разделе**  
  
-   **Для создания подписки для подписчика, отличного от подписчика SQL Server, используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 Чтобы создать подписку для подписчика, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполните указанные ниже действия.  
  
1.  Установите и настройте на распространителе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствующее клиентское программное обеспечение и соответствующий поставщик OLE DB. Дополнительные сведения см. в разделах [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) и [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  Создайте публикацию с помощью мастера создания публикаций. Дополнительные сведения о создании публикаций см. в статьях [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md) и [Создание публикации из базы данных Oracle](../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md). Укажите в мастере создания публикаций следующие параметры:  
  
    -   На странице **Тип публикации** выберите **Публикация моментальных снимков** или **Публикация транзакций**.  
  
    -   На странице **Агент моментальных снимков** снимите флажок **Создать моментальный снимок немедленно**.  
  
         Моментальный снимок создается после включения публикации для подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы гарантировать, что агент моментальных снимков создаст скрипты моментального снимка и инициализации, пригодные для подписчиков, отличных от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  В диалоговом окне **Свойства публикации — \<имя_публикации>** разрешите публикацию для подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения об этом шаге см. в разделе [Publication Properties, Subscription Options](../../relational-databases/replication/publication-properties-subscription-options.md) .  
  
4.  Создайте подписку с помощью мастера создания подписок. В этом разделе содержатся дополнительные сведения об этом шаге.  
  
5.  (Необязательно) Измените свойство статьи **pre_creation_cmd** для сохранения таблиц на подписчике. В этом разделе содержатся дополнительные сведения об этом шаге.  
  
6.  Создайте моментальный снимок для публикации. В этом разделе содержатся дополнительные сведения об этом шаге.  
  
7.  Синхронизация подписки. Дополнительные сведения см. в статье [Синхронизация принудительной подписки](../../relational-databases/replication/synchronize-a-push-subscription.md).  
  
#### <a name="to-enable-a-publication-for-non-sql-server-subscribers"></a>Включение публикации для подписчиков, отличных от подписчиков SQL Server  
  
1.  Подключитесь к издателю в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], а затем раскройте узел сервера.  
  
2.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
3.  Щелкните правой кнопкой мыши публикацию, а затем щелкните **Свойства**.  
  
4.  На странице **Параметры подписки** выберите значение **True** для параметра **Разрешать подписчики, отличные от подписчиков SQL Server**. Выбор этого параметра изменяет количество свойств так, чтобы публикация была совместимой с подписчиками, отличными от подписчика[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Если выбрано значение **True** , то свойство статьи **pre_creation_cmd** устанавливается в значение «drop». Этот параметр говорит о том, что репликация должна удалить таблицу на подписчике, если ее имя совпадает с именем таблицы в статье. Если на подписчике имеются таблицы, которые необходимо сохранить, вызовите хранимую процедуру [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) для каждой статьи, указав значение none в качестве параметра **pre_creation_cmd**: `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Будет предложено создать новый моментальный снимок для публикации. Если не нужно создавать его в данный момент, выполните позднее шаги, описанные в следующей процедуре «Инструкции».  
  
#### <a name="to-create-a-subscription-for-a-non-sql-server-subscriber"></a>Создание подписки для подписчика, отличного от подписчика SQL Server  
  
1.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
2.  Щелкните правой кнопкой мыши соответствующую публикацию, а затем щелкните **Создать подписку**.  
  
3.  Убедитесь в том, что на странице **Расположение агента распространителя** установлен флажок **Выполнять все агенты на распространителе** . Подписчики, отличные от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , не поддерживают выполнение агентов на подписчике.  
  
4.  На странице **Подписчики** щелкните **Добавить подписчик** , а затем — **Добавить подписчик, отличный от подписчика SQL Server**.  
  
5.  В диалоговом окне **Добавление подписчика, отличного от подписчика SQL Server** выберите тип подписчика.  
  
6.  Введите значение в поле **Имя источника данных**:  
  
    -   Для Oracle это будет введенное TNS-имя (transparent network substrate).  
  
    -   Для IBM это может быть любое имя. Обычно указывается сетевой адрес подписчика.  
  
     На этом этапе вводится имя источника данных, и учетные данные, указанные на шаге 9, этим мастером не проверяются. Они не используются репликацией, пока для этой подписки выполняется агент распространителя. Подключившись к подписчику с помощью клиентского средства (например, **sqlplus** для Oracle), убедитесь в том, что все значения проверены. Дополнительные сведения см. в разделах [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md) и [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)] Теперь на странице **Подписчики** мастера данный подписчик будет отображен в столбце **Подписчик** с доступным только для чтения значением **(назначение по умолчанию)** в столбце **База данных подписки** :  
  
    -   Для СУБД Oracle сервер имеет не более одной базы данных, поэтому нет необходимости указывать базу данных.  
  
    -   Для IBM DB2 база данных указывается в свойстве строки соединения DB2 **Исходный каталог** , которое может быть введено в поле **Дополнительные параметры соединения** , описанном далее в этом разделе.  
  
8.  Чтобы получить доступ к диалоговому окну **Безопасность агента распространителя** , на странице**Безопасность агента распространителя**нажмите кнопку свойств ( **…** ), расположенную рядом с подписчиком.  
  
9. В диалоговом окне **Безопасность агента распространителя** выполните следующие действия:  
  
    -   Введите в поля **Учетная запись процесса**, **Пароль**и **Подтверждение пароля** учетную запись и пароль [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которыми будет выполняться агент распространителя, и установите локальное соединение с распространителем.  
  
         Эта учетная запись должна иметь следующие минимальные разрешения: членство в предопределенной роли базы данных **db_owner** в базе данных распространителя; членство в списке доступа к публикации (PAL); разрешения на чтение хранилища моментального снимка; разрешение на чтение каталога установки поставщика OLE DB. Дополнительные сведения о списке доступа к публикации см. в статье [Организация безопасности издателя](../../relational-databases/replication/security/secure-the-publisher.md).  
  
    -   Под полем **Соединиться с подписчиком**введите в поля **Имя входа**, **Пароль**и **Подтверждение пароля** имя входа и пароль, которые следует использовать для соединения с подписчиком. Это имя входа уже должно быть сконфигурировано и иметь разрешения, достаточные для создания объектов в базе данных подписки.  
  
    -   В поле **Дополнительные параметры соединения** укажите любые параметры соединения для подписчика в форме строки соединения (Oracle не требует дополнительных параметров). Параметры разделяются точками с запятой. Ниже приводится пример строки соединения DB2 (переносы строк использованы для удобства чтения):  
  
        ```  
        Provider=DB2OLEDB;Initial Catalog=MY_SUBSCRIBER_DB;Network Transport Library=TCP;Host CCSID=1252;  
        PC Code Page=1252;Network Address=MY_SUBSCRIBER;Network Port=50000;Package Collection=MY_PKGCOL;  
        Default Schema=MY_SCHEMA;Process Binary as Character=False;Units of Work=RUW;DBMS Platform=DB2/NT;  
        Persist Security Info=False;Connection Pooling=True;  
        ```  
  
         Большая часть параметров в строке зависят от настраиваемого сервера DB2, но параметр **Обрабатывать двоичное значение как символ** всегда должен иметь значение **False**. Параметр **Исходный каталог** должен иметь значение для идентификации базы данных подписки.  
  
10. На странице **Расписание синхронизации** выберите из меню **Расписание агента** расписание для агента распространителя (обычно используется расписание **Выполнять постоянно**).  
  
11. На странице **Инициализация подписок** укажите, следует ли инициализировать подписку и, если да, когда ее необходимо инициализировать:  
  
    -   Снимите флажок **Инициализировать** , только если были созданы все объекты и были добавлены все необходимые данные в базу данных подписки.  
  
    -   Чтобы после завершения выполнения этого мастера агент распространителя передал файлы моментальных снимков подписчику, выберите в раскрывающемся списке столбца **Инициализировать, когда** значение **Немедленно** . Выберите пункт **При первой синхронизации** , чтобы агент переслал файлы при следующем запланированном запуске.  
  
12. На странице **Действия мастера** при желании можно написать скрипт для подписки. Дополнительные сведения см. в разделе [Scripting Replication](../../relational-databases/replication/scripting-replication.md).  
  
#### <a name="to-retain-tables-at-the-subscriber"></a>Сохранение таблиц на подписчике  
  
-   По умолчанию при разрешении публикации для подписчиков, не являющихся подписчиками[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , значение свойства статьи **pre_creation_cmd** устанавливается в «drop». Этот параметр говорит о том, что репликация должна удалить таблицу на подписчике, если ее имя совпадает с именем таблицы в статье. Если на подписчике уже существуют таблицы, которые необходимо сохранить, то для каждой статьи вызовите хранимую процедуру [sp_changearticle](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md) , указав в качестве параметра **pre_creation_cmd**значение «none». `sp_changearticle @publication= 'MyPublication', @article= 'MyArticle', @property='pre_creation_cmd', @value='none'`.  
  
#### <a name="to-generate-a-snapshot-for-the-publication"></a>Создание моментального снимка для публикации  
  
1.  Раскройте папку **Репликация** , а затем папку **Локальные публикации** .  
  
2.  Щелкните правой кнопкой мыши публикацию, а затем щелкните **Просмотреть состояние агента моментальных снимков**.  
  
3.  В диалоговом окне **Просмотр состояния агента моментальных снимков — \<Публикация>** щелкните **Запуск**.  
  
 Когда агент моментальных снимков завершит создание моментального снимка, на экран будет выведено примерно следующее сообщение: «[100%] Создан моментальный снимок 17 статей».  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 Можно программно создавать принудительные подписки для подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с помощью хранимых процедур репликации.  
  
> [!IMPORTANT]  
>  По возможности предлагайте пользователям вводить учетные данные системы безопасности во время выполнения приложения. В случае необходимости хранения учетных данных в файле скрипта этот файл следует защищать во избежание несанкционированного доступа.  
  
#### <a name="to-create-a-push-subscription-for-a-transactional-or-snapshot-publication-to-a-non-sql-server-subscriber"></a>Создание принудительной подписки для публикации транзакций или публикации моментальных снимков на подписчики, отличные от SQL Server  
  
1.  Установите последнюю версию поставщика OLE DB для подписчика, отличного от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , на издателе и распространителе. Требования репликации к поставщику OLE DB см. в разделах [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md), [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md), [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md).  
  
2.  В издателе в базе данных издателя проверьте, поддерживает ли публикация подписчиков, отличных от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выполнив процедуру [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md).  
  
    -   Если параметр **enabled_for_het_sub** имеет значение 1, то подписчики, отличные от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , поддерживаются.  
  
    -   Если значение **enabled_for_het_sub** равно 0, выполните процедуру [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md), указав значение **enabled_for_het_sub** для параметра **@property** и **true** для параметра **@value** .  
  
        > [!NOTE]  
        >  Перед изменением значения **enabled_for_het_sub** на **true**необходимо удалить все существующие подписки на публикацию. Нельзя присвоить параметру **enabled_for_het_sub** значение **true** , если публикация также поддерживает обновляемые подписки. Изменение параметра **enabled_for_het_sub** отразится на других свойствах публикации. Дополнительные сведения см. в статье [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
3.  В издателе в базе данных публикации выполните процедуру [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Задайте **@publication** , **@subscriber** , **(назначение по умолчанию)** @property **@destination_db** , **push** @property **@subscription_type** , а также 3 в качестве значения параметра **@subscriber_type** (задает поставщика OLE DB).  
  
4.  В издателе в базе данных публикации выполните процедуру [sp_addpushsubscription_agent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md). Укажите следующее.  
  
    -   параметры **@subscriber** и **@publication** ;  
  
    -   значение **(назначение по умолчанию)** @property **@subscriber_db** ,  
  
    -   свойства источника данных, отличного от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для параметров **@subscriber_provider** , **@subscriber_datasrc** , **@subscriber_location** , **@subscriber_provider_string** и **@subscriber_catalog** .  
  
    -   параметры [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, с которыми будет запускаться агент распространителя на распространителе в параметре **@job_login** и **@job_password** .  
  
        > [!NOTE]  
        >  Для соединений, производимых с использованием встроенной проверки подлинности Windows, в параметрах **@job_login** и **@job_password** . Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows;  
  
    -   значение **0** @property **@subscriber_security_mode** и сведения об имени входа поставщика OLE DB для параметров **@subscriber_login** и **@subscriber_password** .  
  
    -   Расписание задания агента распространителя для этой подписки. Дополнительные сведения см. в статье [Specify Synchronization Schedules](../../relational-databases/replication/specify-synchronization-schedules.md).  
  
    > [!IMPORTANT]  
    >  При создании принудительной подписки на издателе с удаленным распространителем значения, указываемые для всех параметров, включая *job_login* и *job_password*, передаются распространителю в виде обычного текста. Прежде чем выполнять эту хранимую процедуру, необходимо зашифровать соединение между издателем и его удаленным распространителем. Дополнительные сведения см. в разделе [Включение шифрования соединений в компоненте Database Engine (диспетчер конфигураций SQL Server)](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md).  
  
## <a name="see-also"></a>См. также:  
 [IBM DB2 Subscribers](../../relational-databases/replication/non-sql/ibm-db2-subscribers.md)   
 [Oracle Subscribers](../../relational-databases/replication/non-sql/oracle-subscribers.md)   
 [Другие подписчики, отличные от SQL Server](../../relational-databases/replication/non-sql/other-non-sql-server-subscribers.md)   
 [Replication System Stored Procedures Concepts](../../relational-databases/replication/concepts/replication-system-stored-procedures-concepts.md)   
 [Рекомендации по защите репликации](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
