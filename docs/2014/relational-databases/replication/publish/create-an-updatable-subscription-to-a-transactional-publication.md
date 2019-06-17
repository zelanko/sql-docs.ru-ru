---
title: Создание обновляемой подписки на публикацию транзакций (среда Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 07/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- updateable transactional subscriptions
- updateable transactional subscriptions, SSMS
ms.assetid: f9ef89ed-36f6-431b-8843-25d445ec137f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f9c04c03c08f118314dc96c8b491e61be317f40c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62691598"
---
# <a name="create-an-updatable-subscription-to-a-transactional-publication-management-studio"></a>Создание обновляемой подписки для публикации транзакций (среда Management Studio)

> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
 
Репликация транзакций позволяет распространять изменения, выполненные на подписчике, обратно на издатель с помощью немедленно обновляемых подписок или обновляемых посредством очередей подписок. Можно создать обновляемую подписку программно с помощью хранимых процедур репликации.

Настроить обновляемые подписки можно на странице **Обновляемые подписки** **мастера новых публикаций**. Эта страница доступна только тогда, когда включены публикации транзакций для обновляемых подписок. Дополнительные сведения о включении обновляемых подписок см. в статье [Включение обновляемых подписок для публикаций транзакций](enable-updating-subscriptions-for-transactional-publications.md).   
  
## <a name="configure-an-updatable-subscription-from-the-publisher"></a>Настройка обновляемой подписки из издателя  

1. Подключитесь к издателю в среде Microsoft SQL Server Management Studio и раскройте узел сервера.
2. Раскройте папку **Репликация** , а затем папку **Локальные публикации** .
3. Щелкните правой кнопкой мыши публикацию транзакций, настроенную для обновления подписок, а затем щелкните **Создать подписку**.
4. На страницах мастера укажите параметры подписки, например, место, где должен выполняться агент распространения.
5. На странице **Обновляемые подписки** в **мастере создания подписок** должен быть отмечен параметр **Реплицировать**.
6. Выберите параметр **Зафиксировать на стороне издателя** в раскрывающемся списке.

    *  Для немедленного обновления подписок выберите **Одновременно фиксировать изменения**. Если выбран этот параметр, а для публикации разрешено обновление подписок посредством очередей (по умолчанию для публикаций, созданных с помощью мастера создания публикаций), то свойство подписки **update_mode** будет иметь значение **failover**. Этот режим позволяет, при необходимости позднее перейти к обновлению посредством очередей.
    *  Для обновления подписок посредством очередей выберите **Ставить изменения в очередь и фиксировать при первой возможности**. Если выбран этот параметр, для публикации разрешено немедленное обновление подписок (по умолчанию для публикаций, созданных с помощью мастера создания публикаций), и на подписчике работает SQL Server 2005 или более поздняя версия, то свойство подписки **update_mode** примет значение queued failover. Этот режим позволяет, при необходимости, включить немедленное обновление позднее.

    Дополнительные сведения см. в статье [Переключение между режимами обновления для обновляемой подписки на публикацию транзакций](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

7. Страница **Имя входа для обновляемых подписок** отображается для подписок, применяющих немедленное обновление, либо имеющих параметр **update_mode** в значении **queued failover**. На странице **Имя входа для обновляемых подписок** укажите связанный сервер, через который устанавливаются соединения с издателем для обновления подписок. Соединения используются триггерами, которые запускаются на подписчике и распространяют изменения на издатель. Выберите один из следующих вариантов.

    * **Создать связанный сервер, который соединяется с использованием проверки подлинности SQL Server.** Выберите этот параметр, если вы не определили удаленный сервер или связанный сервер между подписчиком и издателем. Репликация создает связанный сервер. Указанная учетная запись уже должна существовать на издателе.
    * **Использовать уже указанный связанный или удаленный сервер** Выберите этот параметр, если вы определили удаленный сервер или связанный сервер между подписчиком и издателем с помощью процедуры [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql),[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio или другого метода.

    Дополнительные сведения о разрешениях, требуемых для учетной записи связанного сервера, см. в статье **Подписки, обновляемые посредством очередей** из [введите здесь описание ссылки](../security/secure-the-subscriber.md)

8. Завершите работу мастера.

## <a name="configure-an-updatable-subscription-from-the-subscriber"></a>Настройка обновляемой подписки из подписчика


1. Подключитесь к подписчику в среде Microsoft SQL Server Management Studio и раскройте узел сервера.
2. Раскройте папку **Репликация** .
3. Щелкните правой кнопкой мыши папку **Локальные подписки** , затем щелкните **Создать подписку**.
4. На странице **Публикация** **мастера создания подписки** выберите **Найти издатель SQL Server** из раскрывающегося списка **Издатель**.
5. Соединитесь с издателем в диалоговом окне **Соединение с сервером** .
6. Выберите публикацию транзакций, настроенную для обновляемых подписок на странице **Публикация**.
7. На страницах мастера укажите параметры подписки, например, место, где должен выполняться агент распространения.
8. На странице **Обновляемые подписки** в мастере создания подписок должен быть отмечен параметр **Реплицировать**.
9. Выберите параметр **Зафиксировать на стороне издателя** в раскрывающемся списке.

    * Для немедленного обновления подписок выберите **Одновременно фиксировать изменения**. Если выбран этот параметр, а для публикации разрешено обновление подписок посредством очередей (по умолчанию для публикаций, созданных с помощью мастера создания публикаций), то свойство подписки **update_mode** будет иметь значение **failover**. Этот режим позволяет, при необходимости позднее перейти к обновлению посредством очередей.
    * Для обновления подписок посредством очередей выберите **Ставить изменения в очередь и фиксировать при первой возможности**. Если выбран этот параметр, для публикации разрешено немедленное обновление подписок (по умолчанию для публикаций, созданных с помощью мастера создания публикаций), и на подписчике работает SQL Server 2005 или более поздняя версия, то свойство подписки **update_mode** примет значение **queued failover**. Этот режим позволяет, при необходимости, включить немедленное обновление позднее.

    Дополнительные сведения см. в статье [Переключение между режимами обновления для обновляемой подписки на публикацию транзакций](../administration/switch-between-update-modes-for-an-updatable-transactional-subscription.md).

10. Страница **Имя входа для обновляемых подписок** отображается для подписок, применяющих немедленное обновление, либо имеющих параметр **update_mode** в значении **queued failover**. На странице **Имя входа для обновляемых подписок** укажите связанный сервер, через который устанавливаются соединения с издателем для обновления подписок. Соединения используются триггерами, которые запускаются на подписчике и распространяют изменения на издатель. Выберите один из следующих вариантов.

    * **Создать связанный сервер, который соединяется с использованием проверки подлинности SQL Server.** Выберите этот параметр, если вы не определили удаленный сервер или связанный сервер между подписчиком и издателем. Репликация создает связанный сервер. Указанная учетная запись уже должна существовать на издателе.
    * **Использовать уже указанный связанный или удаленный сервер** Выберите этот параметр, если вы определили удаленный сервер или связанный сервер между подписчиком и издателем с помощью процедуры [sp_addserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql),[sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql), SQL Server Management Studio или другого метода.

    Дополнительные сведения о разрешениях, требуемых для учетной записи связанного сервера, см. в статье **Подписки, обновляемые посредством очередей** из [введите здесь описание ссылки](../security/secure-the-subscriber.md)

11. Завершите работу мастера.

## <a name="create-an-immediate-updating-pull-subscription"></a>Создание немедленно обновляемой подписки по запросу

1. Проверьте на издателе, что публикация поддерживает немедленное обновление подписок. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.
    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью немедленного обновления подписок.

2. Проверьте на издателе, что публикация поддерживает подписки по запросу. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_pull` в результирующем наборе равно `1`, то публикация поддерживает подписки по запросу.
    * Если `allow_pull` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_pull` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)на подписчике. Задайте `@publisher` и `@publication`, а также установите одно из следующих значений для `@update_mode`:

    * `sync tran` — включает подписку для немедленного обновления;
    * `failover` — включает для подписки немедленное обновление, с обновлением посредством очередей в случае отработки отказа;

    > [!NOTE]  
>  `failover` — требует, чтобы для публикации были включены обновляемые посредством очередей подписки. 
 
4. Выполните процедуру [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)на подписчике. Укажите следующее.

    * Параметры `@publisher`, `@publisher_db`и `@publication` . 
    * Учетные данные пользователя Microsoft Windows, от имени которого на подписчике запускается агент распространителя, в качестве значений параметров `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент соединяется с распространителем с использованием встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@distributor_security_mode` и данные входа Microsoft SQL Server для параметров `@distributor_login` и `@distributor_password`, если для соединения с распространителем нужно использовать проверку подлинности SQL Server. 
    * Расписание задания агента распространителя для этой подписки. 

5. В базе данных подписки на подписчике выполните процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Укажите параметр `@publisher`, параметр `@publication`, имя базы данных публикации в параметре `@publisher_db`и одно из следующих значений параметра `@security_mode`. 

    * `0` — Использовать проверку подлинности SQL Server при выполнении обновлений на издателе. При этом необходимо указать допустимое имя входа на издатель в параметрах `@login` и `@password`.
    * `1` — При соединении с издателем использовать контекст безопасности пользователя, выполняющего изменения на подписчике. Связанные с этим режимом безопасности ограничения см. в разделе [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .
    * `2` — Использовать существующее определенное пользователем имя входа на связанный сервер, созданное с помощью процедуры [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).

6. Выполните на издателе хранимую процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) , указав параметры `@publication`, `@subscriber`, `@destination_db`, значение pull в параметре `@subscription_type`и значение, указанное в шаге 3, в параметре `@update_mode`.

Подписка по запросу на издателе будет зарегистрирована. 


## <a name="create-an-immediate-updating-push-subscription"></a>Создание немедленно обновляемой принудительной подписки 

1. Проверьте на издателе, что публикация поддерживает немедленное обновление подписок. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.
    * Если значение параметра `allow_sync_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью немедленного обновления подписок.

2. Проверьте на издателе, что публикация поддерживает принудительные подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_push` в результирующем наборе равно `1`, то публикация поддерживает принудительные подписки.
    * Если `allow_push` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_push` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)на издателе. Задайте `@publication`, `@subscriber`и `@destination_db`, а также установите одно из следующих значений для `@update_mode`:

    * `sync tran` — включает поддержку немедленного обновления;
    * `failover` — включает поддержку немедленного обновления с обновлением посредством очередей при отработке отказа;

    > [!NOTE]  
>  `failover` — требует, чтобы для публикации были включены обновляемые посредством очередей подписки. 
 
4. Выполните процедуру [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)на издателе. Укажите значения следующих параметров.

    * `@subscriber`, `@subscriber_db`и `@publication`. 
    * Учетные данные Windows, с которыми будет запускаться агент распространителя на распространителе, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику через встроенную систему проверки подлинности Windows; 

    * (Необязательно) Значение `0` для параметра `@subscriber_security_mode` и данные входа SQL Server для параметров `@subscriber_login` и `@subscriber_password`, если для соединения с подписчиком нужно использовать проверку подлинности SQL Server. 
    * Расписание задания агента распространителя для этой подписки.

5. В базе данных подписки на подписчике выполните процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql). Укажите параметр `@publisher`, параметр `@publication`, имя базы данных публикации в параметре `@publisher_db`и одно из следующих значений параметра `@security_mode`. 

     * `0` — Использовать проверку подлинности SQL Server при выполнении обновлений на издателе. При этом необходимо указать допустимое имя входа на издатель в параметрах `@login` и `@password`.
     * `1` — При соединении с издателем использовать контекст безопасности пользователя, выполняющего изменения на подписчике. Связанные с этим режимом безопасности ограничения см. в разделе [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) .
     * `2` — Использовать существующее определенное пользователем имя входа на связанный сервер, созданное с помощью процедуры [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).


## <a name="create-a-queued-updating-pull-subscription"></a>Создание обновляемой посредством очередей подписки по запросу ##

1. Проверьте на издателе, что публикация поддерживает обновляемые посредством очередей подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение параметра `allow_queued_tran` в результирующем наборе равно `1`, то публикация поддерживает немедленное обновление подписок.
    * Если значение параметра `allow_queued_tran` в результирующем наборе равно `0`, публикацию необходимо создать заново с включенной возможностью обновления подписок посредством очередей.

2. Проверьте на издателе, что публикация поддерживает подписки по запросу. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_pull` в результирующем наборе равно `1`, то публикация поддерживает подписки по запросу.
    * Если `allow_pull` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение `allow_pull` для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addpullsubscription](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql)на подписчике. Задайте `@publisher` и `@publication`, а также установите одно из следующих значений для `@update_mode`:

    * `queued tran` — включает возможность обновления подписок посредством очередей;
    * `queued failover` — включает поддержку обновления посредством очередей с немедленным обновлением в качестве варианта для отработки отказа;

    > [!NOTE]  
>  `queued failover` — требует, чтобы для публикации также были включены немедленно обновляемые подписки. Чтобы переключиться на немедленное обновление, необходимо использовать процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) для определения учетных данных, с которыми изменения на подписчике реплицируются на издатель.
 
4. Выполните процедуру [sp_addpullsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)на подписчике. Укажите значения следующих параметров.

    * @publisher, `@publisher_db`и `@publication`. 
    * Учетные данные Windows, с которыми будет запускаться агент распространителя на подписчике, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальное соединение с подписчиком с использованием встроенной проверки подлинности Windows. По умолчанию агент соединяется с распространителем с использованием встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@distributor_security_mode` и данные входа SQL Server для параметров `@distributor_login` и `@distributor_password`, если для соединения с распространителем нужно использовать проверку подлинности SQL Server. 
    * Расписание задания агента распространителя для этой подписки.

5. Выполните на издателе хранимую процедуру [sp_addsubscriber](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql) для регистрации подписчика на издателе, указав параметры `@publication`, `@subscriber`, `@destination_db`, значение pull в параметре `@subscription_type`и значение, указанное в шаге 3, в параметре `@update_mode`.

Подписка по запросу на издателе будет зарегистрирована. 


## <a name="to-create-a-queued-updating-push-subscription"></a>Создание принудительной подписки, обновляемой посредством очередей ##

1. Проверьте на издателе, что публикация поддерживает обновляемые посредством очередей подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение allow_queued_tran в результирующем наборе равно 1, то публикация поддерживает немедленное обновление подписок.
    * Если значение allow_queued_tran в результирующем наборе равно 0, публикацию необходимо создать заново с включенной возможностью обновления подписок посредством очередей. Дополнительные сведения см. в разделе как: включить обновляемые подписки для публикаций транзакций (программирование репликации на языке Transact-SQL)".

2. Проверьте на издателе, что публикация поддерживает принудительные подписки. Для этого выполните процедуру [sp_helppublication](/sql/relational-databases/system-stored-procedures/sp-helppublication-transact-sql). 

    * Если значение столбца `allow_push` в результирующем наборе равно `1`, то публикация поддерживает принудительные подписки.
    * Если `allow_push` имеет значение `0`, выполните хранимую процедуру [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql), указав при этом значение allow_push для параметра `@property` и значение `true` для параметра `@value`. 

3. Выполните процедуру [sp_addsubscription](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql)на издателе. Задайте `@publication`, `@subscriber`и `@destination_db`, а также установите одно из следующих значений для `@update_mode`:

    * `queued tran` — включает возможность обновления подписок посредством очередей;
    * `queued failover` — включает поддержку обновления посредством очередей с немедленным обновлением в качестве варианта для отработки отказа;

    > [!NOTE]  
>  Параметр queued failover требует, чтобы для публикации также были включены немедленно обновляемые подписки. Чтобы переключиться на немедленное обновление, необходимо использовать процедуру [sp_link_publication](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql) для определения учетных данных, с которыми изменения на подписчике реплицируются на издатель.

4. Выполните процедуру [sp_addpushsubscription_agent](/sql/relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql)на издателе. Укажите значения следующих параметров.

    * `@subscriber`, `@subscriber_db`и `@publication`. 
    * Учетные данные Windows, с которыми будет запускаться агент распространителя на распространителе, в параметрах `@job_login` и `@job_password`. 

    > [!NOTE]  
>  Соединения, производимые с использованием встроенной проверки подлинности Windows, всегда используют учетные данные Windows, указанные в параметрах `@job_login` и `@job_password`. Агент распространителя всегда создает локальные соединения с распространителем через встроенную систему проверки подлинности Windows. По умолчанию агент подключается к подписчику с помощью встроенной проверки подлинности Windows. 
 
    * (Необязательно) Значение `0` для параметра `@subscriber_security_mode` и данные входа SQL Server для параметров `@subscriber_login` и `@subscriber_password`, если для соединения с подписчиком нужно использовать проверку подлинности SQL Server. 
    * Расписание задания агента распространителя для этой подписки.


## <a name="example"></a>Пример ##

В этом примере создается немедленно обновляемая подписка по запросу на публикацию, поддерживающую немедленно обновляемые подписки. Имя входа и пароль предоставляются во время выполнения переменными сценария sqlcmd.

> [!NOTE]  
>  Этот скрипт использует переменные скрипта sqlcmd. Они представлены в виде `$(MyVariable)`. Сведения об использовании переменных скрипта в командной строке и среде SQL Server Management Studio см. в подразделе **Выполнение скриптов репликации** раздела [Основные понятия системных хранимых процедур репликации](../concepts/replication-system-stored-procedures-concepts.md).

```sql
-- Execute this batch at the Subscriber.
DECLARE @publication AS sysname;
DECLARE @publicationDB AS sysname;
DECLARE @publisher AS sysname;
DECLARE @login AS sysname;
DECLARE @password AS nvarchar(512);
SET @publication = N'AdvWorksProductTran';
SET @publicationDB = N'AdventureWorks2008R2';
SET @publisher = $(PubServer);
SET @login = $(Login);
SET @password = $(Password);

-- At the subscription database, create a pull subscription to a transactional 
-- publication using immediate updating with queued updating as a failover.
EXEC sp_addpullsubscription 
    @publisher = @publisher, 
    @publication = @publication, 
    @publisher_db = @publicationDB, 
    @update_mode = N'failover', 
    @subscription_type = N'pull';

-- Add an agent job to synchronize the pull subscription, 
-- which uses Windows Authentication when connecting to the Distributor.
EXEC sp_addpullsubscription_agent 
    @publisher = @publisher, 
    @publisher_db = @publicationDB, 
    @publication = @publication,
    @job_login = @login,
    @job_password = @password; 

-- Add a Windows Authentication-based linked server that enables the 
-- Subscriber-side triggers to make updates at the Publisher. 
EXEC sp_link_publication 
    @publisher = @publisher, 
    @publication = @publication,
    @publisher_db = @publicationDB, 
    @security_mode = 0,
    @login = @login,
    @password = @password;
GO

USE AdventureWorks2008R2;
GO

-- Execute this batch at the Publisher.
DECLARE @publication AS sysname;
DECLARE @subscriptionDB AS sysname;
DECLARE @subscriber AS sysname;
SET @publication = N'AdvWorksProductTran'; 
SET @subscriptionDB = N'AdventureWorks2008R2Replica'; 
SET @subscriber = $(SubServer);

-- At the Publisher, register the subscription, using the defaults.
USE [AdventureWorks2008R2]
EXEC sp_addsubscription 
    @publication = @publication, 
    @subscriber = @subscriber, 
    @destination_db = @subscriptionDB, 
    @subscription_type = N'pull', 
    @update_mode = N'failover';
GO
```

## <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>настроить параметры разрешения конфликтов обновления посредством очередей (среда SQL Server Management Studio)
  Установить параметры разрешения конфликтов для публикаций, которые поддерживают подписки, обновляемые посредством очередей, можно на странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Просмотр и изменение свойств публикации](view-and-modify-publication-properties.md).  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>Установка параметров разрешения конфликтов обновления посредством очередей  
  
1.  На странице **Параметры подписки** диалогового окна **Свойства публикации — \<публикация>** выберите одно из следующих значений для параметра **Политика разрешения конфликтов**:    
    -   **Сохранить изменение издателя**    
    -   **Сохранить изменение подписчика**    
    -   **Повторно инициализировать подписку**    
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="see-also"></a>См. также ##
 [Create a Publication](create-a-publication.md)   
 [Updatable Subscriptions for Transactional Replication](../transactional/updatable-subscriptions-for-transactional-replication.md)   
 [Использование программы sqlcmd с переменными скрипта](../../scripting/sqlcmd-use-with-scripting-variables.md)   

  
