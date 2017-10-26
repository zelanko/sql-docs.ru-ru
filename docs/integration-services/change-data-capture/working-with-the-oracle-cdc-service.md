---
title: "Работа со службой Oracle CDC | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04be5896-2301-45f5-a8ce-5f4ef2b69aa5
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 69eb7087530b82c7ba75a9d8ff87fd8fff815f16
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="working-with-the-oracle-cdc-service"></a>Работа со службой CDC Oracle
  В этом разделе описываются некоторые важные понятия, относящиеся к службе Oracle CDC Service. В разделе описываются следующие понятия.  
  
-   [База данных MSXDBCDC](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_MSXDBCDC)  
  
     В данном разделе описываются таблицы, включаемые в эту базу данных, и их значение для CDC.  
  
-   [Базы данных CDC](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_CDCdatabase)  
  
     В этом разделе приведено краткое описание баз данных CDC. Эти базы данных создаются с помощью консоли конструктора Oracle CDC. Для получения дополнительных сведений о базах данных CDC ознакомьтесь с документацией по консоли конструктора CDC.  
  
-   [Использование интерфейса командной строки для настройки службы CDC Service](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_CommandConfigCDC)  
  
     В этом разделе описаны команды командной строки, используемые для настройки службы Oracle CDC Service.  
  
##  <a name="BKMK_MSXDBCDC"></a> База данных MSXDBCDC  
 База данных MSXDBCDC (Microsoft External-Database CDC) ― это специальная база данных, необходимая при использовании служб CDC Service для Oracle совместно с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Имя этой базы данных изменить невозможно. Если в базовом экземпляре размещения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существует база данных с именем MSXDBCDC и содержит таблицы, отличные от определенных службой CDC Service для Oracle, базовый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать нельзя.  
  
 Эта база данных используется в следующих основных целях.  
  
-   В качестве реестра служб Oracle CDC Service, связанных с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эти данные используются для настройки службы и создания компонентов, а также для поддержки координации нескольких служб CDC с одним и тем же именем на различных узлах, один из которых является активным.  
  
-   В качестве реестра экземпляров Oracle CDC, содержащихся в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , служба CDC, обрабатывающая каждый экземпляр, и версий конфигураций, которые они используют. Эти данные эквивалентны столбцу **is_cdc_enabled** в таблице **sys.databases** базы данных master. Служба CDC периодически сканирует таблицу **dbo.xdbcdc_databases** в поисках новых изменений конфигурации CDC или списка отслеживаемых экземпляров.  
  
-   Содержание хранимых процедур, принадлежащих **sysadmin**, которые позволяют создавать и обслуживать экземпляры CDC. Они похожи на системные процедуры, которые используются для реализации функции CDC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="creating-the-msxdbcdc-database"></a>Создание базы данных MSXDBCDC  
 Базу данных MSXDBCDC следует создать до определения службы Oracle CDC Service. В экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно создать только одну базу данных MSXDBCDC. База данных MSXDBCDC создается при подготовке базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для Oracle CDC. Это можно сделать с помощью консоли конфигурации служб CDC Oracle или скрипта создания, сформированного консолью конфигурации служб CDC.  
  
 Владельцем этой базы данных является администратор служб Oracle CDC Service. Он может управлять всеми экземплярами Oracle CDC, размещенными на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **См. также**  
  
 [Как подготовить SQL Server для CDC](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
### <a name="the-msxdbcdc-database-tables"></a>Таблицы базы данных MSXDBCDC  
 В данном разделе описаны следующие таблицы базы данных MSXDBCDC.  
  
-   [dbo.xdbcdc_trace](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_trace)  
  
-   [dbo.xdbcdc_databases](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_databases)  
  
-   [dbo.xdbcdc_services](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_services)  
  
###  <a name="BKMK_dboxdbcdc_trace"></a> dbo.xdbcdc_trace  
 В этой таблице хранятся данные трассировки для службы Oracle CDC Service. Сведения, хранящиеся в этой таблице, включают в себя важные изменения состояния и записи трассировки.  
  
 Служба Oracle CDC Service создает записи об ошибках и некоторые информационные записи как в журнал событий Windows, так и в таблице трассировки. В некоторых случаях таблица трассировки может быть недоступна. Тогда сведения об ошибках можно найти в журнале событий.  
  
 Далее описаны элементы, содержащиеся в таблице **dbo.xdbcdc_trace** .  
  
|Элемент|Description|  
|----------|-----------------|  
|timestamp|Точная отметка времени в формате UTC, когда была создана запись трассировки.|  
|type|Содержит одно из следующих значений:<br /><br /> ошибка<br /><br /> INFO<br /><br /> трассировка|  
|node|Имя узла, на котором была создана запись.|  
|status|Код состояния, который используется в таблице состояний.|  
|sub_status|Код подсостояния, который используется в таблице состояний.|  
|status_message|Сообщение состояния, которое используется в таблице состояний.|  
|источник|Имя компонента Oracle CDC, который произвел запись трассировки.|  
|text_data|Дополнительные текстовые данные в тех случаях, когда запись ошибки или трассировки содержит полезную текстовую информацию.|  
|binary_data|Дополнительные двоичные данные в тех случаях, когда запись ошибки или трассировки содержит полезную двоичную информацию.|  
  
 Экземпляр Oracle CDC удаляет старые строки таблицы трассировки в соответствии с политикой сохранения таблицы изменений.  
  
###  <a name="BKMK_dboxdbcdc_databases"></a> dbo.xdbcdc_databases  
 В этой таблице содержатся имена баз данных CDC службы CDC Service для Oracle в текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Каждая база данных соответствует экземпляру Oracle CDC. Служба Oracle CDC Service использует эту таблицу для определения экземпляров, которые следует запустить, остановить или перенастроить.  
  
 В следующей таблице описаны элементы, содержащиеся в таблице **dbo.xdbcdc_trace** .  
  
|Элемент|Description|  
|----------|-----------------|  
|имя|Имя базы данных Oracle, содержащейся в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|config_version|Отметка времени в формате (UTC) последнего изменения в соответствующей таблице **xdbcdc_config** базы данных CDC или отметка времени (UTC) текущей строки этой таблицы.<br /><br /> Триггер UPDATE принудительно присваивает этому элементу значение GETUTCDATE(). **config_version** сообщает службе CDC, какой экземпляр CDC следует проверить на предмет наличия изменений в конфигурации, отключить или включить.|  
|cdc_service_name|Этот элемент определяет, какая из служб Oracle CDC Service обрабатывает выбранную базу данных Oracle.|  
|включено|Указывает, активен (1) или отключен (0) экземпляр Oracle CDC. При запуске службы Oracle CDC Service запускаются только экземпляры, отмеченные «включить» (1).<br /><br /> **Примечание.**Экземпляр Oracle CDC может перейти в отключенное состояние из-за ошибки, не дающей возможности повторить операцию. В этом случае экземпляр следует перезапустить вручную после устранения ошибки.|  
  
###  <a name="BKMK_dboxdbcdc_services"></a> dbo.xdbcdc_services  
 В этой таблице перечислены службы CDC, связанные с базовым экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Эта таблица используется консолью конструктора CDC для определения списка служб CDC, настроенных для локального экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Она также используется службой CDC для обеспечения обработки данного имени службы Oracle CDC Service только одной запущенной службой Windows.  
  
 Далее описаны элементы состояния отслеживания изменений, содержащиеся в таблице **dbo.xdbcdc_databases** .  
  
|Элемент|Description|  
|----------|-----------------|  
|cdc_service_name|Имя службы Oracle CDC Service (имя службы Windows).|  
|cdc_service_sql_login|Имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемое службой Oracle CDC Service для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Новый пользователь SQL с именем cdc_service создается и связывается с этим именем входа, а затем добавляется к предопределенным ролям базы данных db_ddladmin, db_datareader и db_datawriter для каждой базы данных CDC, обрабатываемой данной службой.|  
|ref_count|Этот элемент подсчитывает количество компьютеров, где установлена одна и та же служба Oracle CDC Service. Этот счетчик увеличивается при каждом добавлении службы Oracle CDC Service с тем же именем и уменьшается, когда такая служба удаляется. Когда значение счетчика достигнет нуля, эта строка будет удалена.|  
|active_service_node|Имя узла Windows, который в настоящее время обрабатывает службу CDC. Если служба была остановлена корректно, в этот столбец помещается значение NULL, указывающее, что служба больше не активна.|  
|active_service_heartbeat|Этот элемент отслеживает текущую службу CDC, чтобы определить, активна ли она.<br /><br /> Для активной службы CDC этот элемент обновляется через равные промежутки времени, получая значение текущей отметки времени в формате UTC базы данных. Интервал по умолчанию составляет 30 секунд, но его можно менять.<br /><br /> Если ожидающая служба CDC обнаруживает, что тактовый импульс не обновлялся на протяжении заданного интервала, она пытается взять на себя роль активной службы CDC.|  
|параметры|Этот элемент указывает дополнительные параметры, такие как настройка или трассировка. Он имеет вид: **имя[= значение][; ]**. В строке параметров используется та же семантика, что и в строке подключения ODBC. Если параметр принадлежит к логическому типу (со значением «да/нет»), значение может содержать только имя.<br /><br /> Параметр trace может принимать одно из следующих возможных значений:<br /><br /> **true**<br /><br /> **on**<br /><br /> **false**<br /><br /> **off**<br /><br /> **\<Имя класса > [, имя_класса >]**<br /><br /> <br /><br /> Значение по умолчанию — **false**.<br /><br /> **service_heartbeat_interval** ― это временной интервал (в секундах), на протяжении которого служба должна обновить столбец active_service_heartbeat. Значение по умолчанию — **30**. Максимальное значение равно **3600**.<br /><br /> **service_config_polling_interval** ― это интервал опроса (в секундах), который служба CDC использует для проверки изменений конфигурации. Значение по умолчанию — **30**. Максимальное значение равно **3600**.<br /><br /> **sql_command_timeout** ― время ожидания для команды, взаимодействующей с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Значение по умолчанию — **1**. Максимальное значение равно **3600**.|  
||  
  
### <a name="the-msxdbcdc-database-stored-procedures"></a>Хранимые процедуры базы данных MSXDBCDC  
 В этом разделе описаны следующие хранимые процедуры базы данных MSXDBCDC.  
  
-   [dbo.xcbcdc_reset_db(имя базы данных)](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxcbcdc_reset_db)  
  
-   [dbo.xdbcdc_disable_db(имя_базы_данных)](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_disable_db)  
  
-   [dbo.xcbcdc_add_service(svcname,sqlusr)](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxcbcdc_add_service)  
  
-   [dbo.xdbcdc_start(имя_базы_данных)](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_start)  
  
-   [dbo.xdbcdc_stop(имя_базы_данных)](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_dboxdbcdc_stop)  
  
###  <a name="BKMK_dboxcbcdc_reset_db"></a> dbo.xcbcdc_reset_db(имя базы данных)  
 Эта процедура очищает данные экземпляра Oracle CDC. Она используется:  
  
-   для перезапуска отслеживания данных с игнорированием предыдущих данных, например после восстановления базы данных-источника или после периода неактивности при недоступности некоторых журналов транзакций Oracle;  
  
-   при порче состояния CDC (особенно порче любых данных из таблиц cdc.*tables).  
  
 Процедура **dbo.xcbcdc_reset_db** выполняет следующие задачи:  
  
-   останавливает экземпляр CDC (если он активен);  
  
-   усекает таблицы изменений, таблицу **cdc_lsn_mapping** и таблицу **cdc_ddl_history** ;  
  
-   очищает таблицу **cdc_xdbcdc_state** ;  
  
-   очищает столбец start_lsn для каждой строки таблицы **cdc_change_table**.  
  
 Для использования процедуры **dbo.xcbcdc_reset_db** пользователь должен быть членом роли **db_owner** указанной базы данных экземпляра CDC или членом одной из следующих предопределенных ролей сервера: **sysadmin** или **serveradmin** .  
  
 Дополнительные сведения о таблицах CDC см. в разделе *Базы данных CDC* в справочной системе консоли конструктора CDC.  
  
###  <a name="BKMK_dboxdbcdc_disable_db"></a> dbo.xdbcdc_disable_db(имя_базы_данных)  
 Процедура **dbo.xcbcdc_disable_db** выполняет следующую задачу:  
  
-   удаляет запись в таблице MSXDBCDC.xdbcdc_databases для выбранной базы данных CDC.  
  
 Для использования процедуры **dbo.xcbcdc_disable_db** пользователь должен быть членом роли базы данных **db_owner** указанного экземпляра CDC или членом одной из следующих предопределенных ролей сервера: **sysadmin** или **serveradmin** .  
  
 Дополнительные сведения о таблицах CDC см. в разделе «Базы данных CDC» в справочной системе консоли конструктора CDC.  
  
###  <a name="BKMK_dboxcbcdc_add_service"></a> dbo.xcbcdc_add_service(svcname,sqlusr)  
 Процедура **dbo.xcbcdc_add_service** добавляет запись в таблицу **MSXDBCDC.xdbcdc_services** и увеличивает на единицу счетчик ref_count для данного имени службы в таблице **MSXDBCDC.xdbcdc_services** . Если значение **ref_count** становится равным 0, процедура удаляет эту строку.  
  
 Для использования **dbo.xcbcdc_add_service\<имени службы, имя пользователя >** процедуры, пользователь должен быть членом **db_owner** роли базы данных, именованный экземпляр базы данных CDC или членом **sysadmin** или **serveradmin** предопределенной роли сервера.  
  
###  <a name="BKMK_dboxdbcdc_start"></a> dbo.xdbcdc_start(имя_базы_данных)  
 Процедура **dbo.xdbcdc_start** посылает запрос на запуск службе CDC, обрабатывающей выбранный экземпляр CDC, чтобы начать обработку изменений.  
  
 Для использования процедуры **dbo.xcbcdc_start** пользователь должен быть членом роли **db_owner** указанной базы данных CDC или членом одной из следующих предопределенных ролей сервера: **sysadmin** или **serveradmin** для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
###  <a name="BKMK_dboxdbcdc_stop"></a> dbo.xdbcdc_stop(имя_базы_данных)  
 Процедура **dbo.xdbcdc_start** посылает запрос на остановку службе CDC, обрабатывающей выбранный экземпляр CDC, чтобы прекратить обработку изменений.  
  
 Для использования процедуры **dbo.xcbcdc_stop** пользователь должен быть членом роли **db_owner** указанной базы данных CDC или членом одной из следующих предопределенных ролей сервера: **sysadmin** или **serveradmin** для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="BKMK_CDCdatabase"></a> Базы данных CDC  
 Каждый экземпляр Oracle CDC, используемый службой CDC, связан с определенной базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая называется базой данных CDC. Эта база данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] размещается в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , связанном со службой Oracle CDC Service.  
  
 База данных CDC содержит специальную схему cdc. Служба Oracle CDC Service использует эту схему с именами таблиц с префиксом **xdbcdc_**. Эта схема используется в целях обеспечения безопасности и согласованности.  
  
 И экземпляр Oracle CDC, и базы данных CDC создаются с помощью консоли конструктора Oracle CDC. Дополнительные сведения о базах данных CDC см. в документации, поставляемой вместе с консолью конструктора CDC.  
  
##  <a name="BKMK_CommandConfigCDC"></a> Использование интерфейса командной строки для настройки службы CDC Service  
 Вы можете управлять служебной программой Oracle CDC Service (xdbcdcsvc.exe) из командной строки. Служебная программа CDC представляет собой 32-/64-разрядный исполняемый файл Windows.  
  
 **См. также:**  
  
 [Как использовать интерфейс командной строки службы CDC](../../integration-services/change-data-capture/how-to-use-the-cdc-service-command-line-interface.md)  
  
### <a name="service-program-commands"></a>Команды служебной программы  
 В этом разделе описаны следующие команды для настройки службы CDC.  
  
-   [Config](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_config)  
  
-   [Создание](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_create)  
  
-   [Delete](../../integration-services/change-data-capture/working-with-the-oracle-cdc-service.md#BKMK_delete)  
  
###  <a name="BKMK_config"></a> Config  
 Команда `Config` используется для обновления конфигурации службы Oracle CDC Service с помощью скрипта. Эту команду можно использовать для изменения отдельных настроек службы CDC (например, только строки подключения, не зная пароля асимметричного ключа). Эта команда должна выполняться администратором компьютера. Далее приведен пример использования команды `Config` .  
  
```  
"<path>xdbcdcsvc.exe" config  
     <cdc-service-name>  
     [connect= <sql-server-connection-string>]  
     [key= <asym-key-password>]  
     [svcacct= <windows-account> <windows-password>]  
     [sqlacct= <sql-username> <sql-password>]  
  
```  
  
 Где:  
  
 **cdc-service-name** ― это имя службы CDC, настройки которой нужно изменить. Это обязательный параметр.  
  
 **sql-server-connection-string** ― это строка подключения, которую нужно изменить. Если строка подключения содержит пробелы или кавычки, ее следует заключить в двойные кавычки ("). Внедренные кавычки экранируются удвоением кавычек.  
  
 **asym-key-password** ― это пароль, который нужно изменить.  
  
 **windows-account**, **windows-password** ― это учетная запись Windows для службы, которую нужно изменить.  
  
 **sql-username**, **sql-password** ― это учетные данные для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которые нужно изменить. Если у sqlacct пусты и имя пользователя, и пароль, то служба Oracle CDC Service подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows.  
  
 **Примечание.**Любой параметр, который содержит пробелы или кавычки, должен быть заключен в двойные кавычки ("). Встроенные двойные кавычки необходимо удвоить (например, для использования **"A#B" D** в качестве пароля введите **""A#B"" D"**).  
  
###  <a name="BKMK_create"></a> Создание  
 Команда `Create` используется для создания службы Oracle CDC Service с помощью скрипта. Эта команда должна выполняться администратором компьютера. Далее приведен пример использования команды `Create` .  
  
```  
"<path>xdbcdcsvc.exe" create  
     <cdc-service-name>  
     [connect= "<sql-server-connection-string>"]  
     [key= <asym-key-password>]  
     [svcacct <windows-account> <windows-password>]  
     [sqlacct <sql-username> <sql-password>]  
```  
  
 Где:  
  
 **cdc-service-name** ― это имя создаваемой службы. Если служба с таким именем уже существует, программа возвращает ошибку. Не следует использовать длинные имена и имена с пробелами. В имени службы нельзя использовать символы "/" и "\\". Это обязательный параметр.  
  
 **sql-server-connection-string** ― строка подключения, используемая для соединения с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , который связан с новой службой Oracle CDC.  
  
 **asym-key-password** ― это пароль, который защищает асимметричный ключ, используемый для хранения учетных данных средства интеллектуального анализа журнала базы данных-источника.  
  
 **windows-account**, **windows-password** ― это имя учетной записи и пароль, связанные с создаваемой службой Oracle CDC Service.  
  
 **sql-username**, **sql-password** ― это имя учетной записи и пароль [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , используемые для подключения к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Если оба этих параметра пусты, то служба CDC Service для Oracle подключается к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием проверки подлинности Windows.  
  
 **Примечание.**Любой параметр, который содержит пробелы или кавычки, должен быть заключен в двойные кавычки ("). Встроенные двойные кавычки необходимо удвоить (например, для использования **"A#B" D** в качестве пароля введите **""A#B"" D"**).  
  
###  <a name="BKMK_delete"></a> Delete  
 Команда `Delete` используется для аккуратного удаления службы Oracle CDC Service с помощью скрипта. Эта команда должна выполняться администратором компьютера. Далее приведен пример использования команды `Delete` .  
  
```  
"<path>xdbcdcsvc.exe" delete  
    <cdc-service-name>  
  
```  
  
 Где:  
  
 **cdc-service-name** ― это имя службы CDC, которую нужно удалить.  
  
 **Примечание.**Любой параметр, который содержит пробелы или кавычки, должен быть заключен в двойные кавычки ("). Встроенные двойные кавычки необходимо удвоить (например, для использования **"A#B" D** в качестве пароля введите **""A#B"" D"**).  
  
## <a name="see-also"></a>См. также:  
 [Как использовать интерфейс командной строки службы CDC](../../integration-services/change-data-capture/how-to-use-the-cdc-service-command-line-interface.md)   
 [Подготовка SQL Server для CDC](../../integration-services/change-data-capture/how-to-prepare-sql-server-for-cdc.md)  
  
  

