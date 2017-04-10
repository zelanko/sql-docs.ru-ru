---
title: "Работа с профилями агента репликации | Microsoft Docs"
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
  - "репликация [SQL Server], агенты и профили"
  - "профили агентов репликации [SQL Server]"
  - "агенты [репликация SQL Server], профили"
  - "профили [SQL Server], агенты репликации"
ms.assetid: 9c290a88-4e9f-4a7e-aab5-4442137a9918
caps.latest.revision: 49
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 49
---
# Работа с профилями агента репликации
  В данном разделе описывается работа с профилями агента репликации в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] или объектов RMO. Поведение каждого агента репликации контролируется набором параметров, который может устанавливаться через профили агента. У каждого агента имеются профили по умолчанию, а некоторые агенты имеют дополнительные предопределенные профили. В каждый момент времени активен только один профиль.  
  
 **В этом разделе**  
  
-   **Для работы с профилями агента репликации используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    -   Доступ к диалоговому окну «Профили агентов»  
  
    -   Указание профиля для агента  
  
    -   Создание профиля  
  
    -   Изменение профиля  
  
    -   Удаление профиля  
  
     [Transact-SQL](#TsqlProcedure)  
  
    -   Создание профиля  
  
    -   Изменение профиля  
  
    -   Удаление профиля  
  
    -   Использование профилей агента при синхронизации  
  
    -   Пример (Transact-SQL)  
  
     [Объекты RMO](#RMOProcedure)  
  
    -   Создание профиля  
  
    -   Изменение профиля  
  
    -   Удаление профиля  
  
-   **Дальнейшие действия:**  [после изменения параметров агента](#FollowUp)  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
###  <a name="Access_SSMS"></a> Доступ к диалоговому окну «Профили агентов» из среды SQL Server Management Studio  
  
1.  На **Общие** Страница **Свойства распространителя — \< распространитель>** диалоговом нажмите кнопку **профиля по умолчанию**.  
  
#### Доступ к диалоговому окну «Профили агентов» из монитора репликации  
  
-   Чтобы открыть диалоговое окно для всех агентов, щелкните издатель правой кнопкой мыши и нажмите кнопку **Профили агента**.  
  
-   Чтобы открыть диалоговое окно для одного агента:  
  
    1.  На левой панели монитора репликации раскройте группу издателей, раскройте нужный издатель, а затем выберите публикацию.  
  
    2.  Для профилей агента распространителя и агента слияния, щелкните правой кнопкой мыши подписку на **все подписки** а затем щелкните **профиль агента**. Для других агентов щелкните правой кнопкой мыши агент на **Агенты** а затем щелкните **профиль агента**.  
  
###  <a name="Specify_SSMS"></a> Указание профиля для агента  
  
1.  Если в окне **Профили агентов** отображаются профили нескольких агентов, следует выбрать агент.  
  
2.  Выберите профиль в столбце **По умолчанию для новых** сетки **Профили агентов** . По умолчанию профиль применяется к агентам только для новых публикаций и подписок.  
  
3.  Чтобы указать, что всем агентам выбранного типа следует использовать для существующих публикаций или подписок данный профиль, щелкните **Изменить существующие агенты**.  
  
###  <a name="Modify_SSMS"></a> Просмотр и редактирование параметров, связанных с профилем  
  
1.  Если в окне **Профили агентов** отображаются профили нескольких агентов, следует выбрать агент.  
  
2.  Нажмите кнопку свойств (**...**) рядом с профилем.  
  
3.  Просмотрите параметры и значения в **\< Имя_профиля> Свойства профиля** диалоговое окно.  
  
    -   Параметры в пользовательских профилях могут редактироваться, параметры же в предопределенных системных профилях недоступны для изменения.  
  
    -   Для просмотра всех параметров агента снимите флажок **Показывать только параметры, используемые в этом профиле** . К дополнительным сведениям о параметрах агента можно перейти по ссылкам в конце этого раздела.  
  
4.  Щелкните **Закрыть**.  
  
###  <a name="Create_SSMS"></a> Создание пользовательского профиля  
  
1.  Если в окне **Профили агентов** отображаются профили нескольких агентов, следует выбрать агент.  
  
2.  Нажмите кнопку **Создать**.  
  
3.  В диалоговом окне инициализации **Создать профиль агента** выберите существующий профиль, который будет служить основой нового профиля.  
  
4.  В диалоговом окне **Создать профиль агента** введите значения в текстовые поля **Имя** и **Описание** .  
  
5.  Чтобы настроить профиль, измените параметры. Для просмотра всех параметров агента снимите флажок **Показывать только параметры, используемые в этом профиле** . К дополнительным сведениям о параметрах агента можно перейти по ссылкам в конце этого раздела.  
  
6.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
###  <a name="Delete_SSMS"></a> Удаление пользовательского профиля  
  
1.  Если в окне **Профили агентов** отображаются профили нескольких агентов, следует выбрать агент.  
  
2.  Если профиль связан с одним или более агентом, измените профиль для этих агентов:  
  
    1.  Выберите другой профиль в сетке **Профили агентов** .  
  
    2.  Щелкните **Изменить существующие агенты**.  
  
        > [!NOTE]  
        >  В результате изменится профиль всех агентов выбранного типа для существующих публикаций или подписок, а не только тех из них, которые вы намереваетесь удалить.  
  
3.  Выберите профиль, подлежащий удалению, затем нажмите кнопку **Удалить**.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
###  <a name="Create_tsql"></a> Создание нового профиля агента  
  
1.  На распространителе выполните хранимую процедуру [sp_add_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md). Укажите **@name**, значение **1** для **@profile_type**, и одно из следующих значений для **@agent_type**:  
  
    -   **1** - [агент моментальных снимков репликации](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [агента распространителя репликации](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [агент слияния репликации](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [агент чтения очереди репликации](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Если этот профиль станет профилем по умолчанию для агента репликации данного типа, укажите значение **1** для **@default**. Идентификатор нового профиля возвращается с помощью **@profile_id** выходной параметр. Таким образом создается новый профиль с набором параметров профиля на основе профиля по умолчанию для данного типа агента.  
  
2.  Когда новый профиль создан, для его настройки можно добавить, удалить или изменить параметры по умолчанию.  
  
###  <a name="Modify_tsql"></a> Изменение существующего профиля агента  
  
1.  На распространителе выполните хранимую процедуру [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Укажите одно из следующих значений для **@agent_type**:  
  
    -   **1** - [агент моментальных снимков репликации](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [агента распространителя репликации](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [агент слияния репликации](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [агент чтения очереди репликации](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Будут получены все профили для указанного типа агента. Обратите внимание на значение **profile_id** в результирующем наборе для профиля для изменения.  
  
2.  На распространителе выполните хранимую процедуру [sp_help_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md). Укажите идентификатор профиля из шага 1 для **@profile_id**. В результате будут возвращены все параметры для профиля. Запомните имена параметров профиля, которые требуется изменить или удалить.  
  
3.  Чтобы изменить значение параметра в профиле, выполните [sp_change_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md). Укажите идентификатор профиля из шага 1 для **@profile_id**, имя параметра для изменения **@property**, и новое значение для параметра **@value**.  
  
    > [!NOTE]  
    >  Существующий профиль агента невозможно сделать профилем по умолчанию для агента. Профиль по умолчанию должен быть создан заново, как показано в предыдущей процедуре.  
  
4.  Чтобы удалить параметр из профиля, выполните [sp_drop_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md). Укажите идентификатор профиля из шага 1 для **@profile_id** и имя параметра для удаления **@parameter_name**.  
  
5.  Чтобы добавить новый параметр в профиль, сделайте следующее.  
  
    -   Запрос [MSagentparameterlist & #40; Transact-SQL & #41;](../../../relational-databases/system-tables/msagentparameterlist-transact-sql.md) Таблица на распространителе, чтобы определить, какие параметры профиля можно задать для каждого типа агента.  
  
    -   На распространителе выполните хранимую процедуру [sp_add_agent_parameter & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md). Укажите идентификатор профиля из шага 1 для **@profile_id**, имя является допустимым параметром для добавления для **@parameter_name**, и значение параметра для **@parameter_value**.  
  
###  <a name="Delete_tsql"></a> Удаление профиля агента  
  
1.  На распространителе выполните хранимую процедуру [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Укажите одно из следующих значений для **@agent_type**:  
  
    -   **1** - [агент моментальных снимков репликации](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [агента распространителя репликации](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [агент слияния репликации](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [агент чтения очереди репликации](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Будут получены все профили для указанного типа агента. Обратите внимание на значение **profile_id** в результирующем наборе для удаляемого профиля.  
  
2.  На распространителе выполните хранимую процедуру [sp_drop_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md). Укажите идентификатор профиля из шага 1 для **@profile_id**.  
  
###  <a name="Synch_tsql"></a> Использование профилей агента при синхронизации  
  
1.  На распространителе выполните хранимую процедуру [sp_help_agent_profile & #40; Transact-SQL & #41;](../../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md). Укажите одно из следующих значений для **@agent_type**:  
  
    -   **1** - [агент моментальных снимков репликации](../../../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
    -   **2** - [агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)  
  
    -   **3** - [агента распространителя репликации](../../../relational-databases/replication/agents/replication-distribution-agent.md)  
  
    -   **4** - [агент слияния репликации](../../../relational-databases/replication/agents/replication-merge-agent.md)  
  
    -   **9** - [агент чтения очереди репликации](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
     Будут получены все профили для указанного типа агента. Обратите внимание на значение **Имя_профиля** в результирующем наборе для профиля для использования.  
  
2.  Если агент запускается из задания агента, измените шаг задания, который запускает агент, чтобы задать значение **Имя_профиля** полученным на шаге 1 после **- ProfileName** параметр командной строки. Дополнительные сведения см. в разделе [& #40; Просмотр и изменение параметров командной строки агента репликации SQL Server Management Studio & #41;](../../../relational-databases/replication/agents/view and modify replication agent command prompt parameters.md).  
  
3.  Если агент запускается из командной строки, укажите значение **Имя_профиля** полученным на шаге 1 после **- ProfileName** параметр командной строки.  
  
###  <a name="TsqlExample"></a> Пример (Transact-SQL)  
 В этом примере создается пользовательский профиль для агента слияния с именем **custom_merge**, изменяет значение **- UploadReadChangesPerBatch** добавляет новый параметр, **- ExchangeType** параметр и возвращает сведения о созданном профиле.  
  
 [!code-sql[HowTo#sp_addagentprofileparam](../../../relational-databases/replication/codesnippet/tsql/work-with-replication-ag_1.sql)]  
  
##  <a name="RMOProcedure"></a> При помощи объектов RMO  
  
###  <a name="Create_RMO"></a> Создание нового профиля агента  
  
1.  Создайте соединение с распространителем с помощью экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.AgentProfile> класса.  
  
3.  Установите следующие свойства объекта.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> -имя для профиля.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AgentType%2A> - <xref:Microsoft.SqlServer.Replication.AgentType> значение, указывающее тип агента репликации, для которой создается профиль.  
  
    -   <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> - <xref:Microsoft.SqlServer.Management.Common.ServerConnection> созданной на шаге 1.  
  
    -   (Необязательно) <xref:Microsoft.SqlServer.Replication.AgentProfile.Description%2A> -Описание профиля.  
  
    -   (Необязательно) <xref:Microsoft.SqlServer.Replication.AgentProfile.Default%2A> -присвоить этому свойству значение **true** при всех заданиях агентов для данного <xref:Microsoft.SqlServer.Replication.AgentType> будут использовать этот профиль по умолчанию.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.AgentProfile.Create%2A> метод для создания профиля на сервере.  
  
5.  После создания профиля на сервере можно производить его настройку, добавляя, удаляя или изменяя значения параметров агента репликации.  
  
6.  Назначение профиля для существующего задания агента репликации, вызовите <xref:Microsoft.SqlServer.Replication.AgentProfile.AssignToAgent%2A> метод. В качестве параметра *distributionDBName* передайте имя базы данных распространителя, а в параметре *agentID*— идентификатор задания.  
  
###  <a name="Modify_RMO"></a> Изменение существующего профиля агента  
  
1.  Создайте соединение с распространителем с помощью экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.ReplicationServer> класса. Передайте <xref:Microsoft.SqlServer.Management.Common.ServerConnection> объекта, созданного на шаге 1.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если этот метод возвратил значение **false**, проверьте, существует ли распространитель.  
  
4.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationServer.EnumAgentProfiles%2A> метод. Передайте <xref:Microsoft.SqlServer.Replication.AgentType> значение сузить возвращаемый профили для конкретного агента репликации.  
  
5.  Извлеките <xref:Microsoft.SqlServer.Replication.AgentProfile> объекта из возвращенного <xref:System.Collections.ArrayList>, где <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> Свойства объекта соответствует имени профиля.  
  
6.  Вызовите один из следующих методов <xref:Microsoft.SqlServer.Replication.AgentProfile> чтобы изменить профиль:  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.AddParameter%2A> -добавляется к профилю поддерживаемый параметр где *имя* имя параметра агента репликации и *значение* равен указанному значению. Для перечисления всех поддерживаемых параметров агента для данного типа агента, вызовите <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> метод. Этот метод возвращает <xref:System.Collections.ArrayList> из <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> объектов, которые представляют все поддерживаемые параметры.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.RemoveParameter%2A> -удаляет существующий параметр из профиля, где *имя* имя параметра агента репликации. Чтобы перечислить все текущие параметры агента, определенные для профиля, вызовите <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> метод. Этот метод возвращает <xref:System.Collections.ArrayList> из <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> объектов, которые представляют существующие параметры для этого профиля.  
  
    -   <xref:Microsoft.SqlServer.Replication.AgentProfile.ChangeParameter%2A> -изменяет значение существующего параметра в профиле, где *имя* имя параметра агента и *newValue* значение, на котором изменяется параметр. Чтобы перечислить все текущие параметры агента, определенные для профиля, вызовите <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameters%2A> метод. Этот метод возвращает <xref:System.Collections.ArrayList> из <xref:Microsoft.SqlServer.Replication.AgentProfileParameter> объектов, которые представляют существующие параметры для этого профиля. Для перечисления всех поддерживаемых параметров агента, вызовите <xref:Microsoft.SqlServer.Replication.AgentProfile.EnumParameterInfo%2A> метод. Этот метод возвращает <xref:System.Collections.ArrayList> из <xref:Microsoft.SqlServer.Replication.AgentProfileParameterInfo> объектов, представляющих поддерживаемые значения для всех параметров.  
  
###  <a name="Delete_RMO"></a> Удаление профиля агента  
  
1.  Создайте соединение с распространителем с помощью экземпляра <xref:Microsoft.SqlServer.Management.Common.ServerConnection> класса.  
  
2.  Создайте экземпляр <xref:Microsoft.SqlServer.Replication.AgentProfile> класса. Имя профиля для набора <xref:Microsoft.SqlServer.Replication.AgentProfile.Name%2A> и <xref:Microsoft.SqlServer.Management.Common.ServerConnection> из шага 1 для <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A>.  
  
3.  Вызов <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> метод. Если метод вернул значение **false**, то имя указано неверно или профиль не существует на сервере.  
  
4.  Убедитесь, что <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A> свойству <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.User>, который указывает профиль клиента. Не следует удалять профиль, который имеет значение <xref:Microsoft.SqlServer.Replication.AgentProfileTypeOption.System> для <xref:Microsoft.SqlServer.Replication.AgentProfile.Type%2A>.  
  
5.  Вызов <xref:Microsoft.SqlServer.Replication.AgentProfile.Remove%2A> метод для удаления пользовательского профиля, представленный этим объектом с сервера.  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После изменения параметров агента  
 Изменения параметров агента вступают в действие при следующем запуске агента. Если агент выполняется в непрерывном режиме, следует остановить и перезапустить агент.  
  
## См. также:  
 [Профили агента репликации](../../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [Агент моментальных снимков репликации](../../../relational-databases/replication/agents/replication-snapshot-agent.md)   
 [Агент чтения журнала репликации](../../../relational-databases/replication/agents/replication-log-reader-agent.md)   
 [Агент распространения репликации](../../../relational-databases/replication/agents/replication-distribution-agent.md)   
 [Агент слияния репликации](../../../relational-databases/replication/agents/replication-merge-agent.md)   
 [Агент чтения очереди репликации](../../../relational-databases/replication/agents/replication-queue-reader-agent.md)  
  
  