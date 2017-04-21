---
title: "Агент чтения журнала репликации | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Log Reader Agent, executables
- Log Reader Agent, parameter reference
- agents [SQL Server replication], Log Reader Agent
- command prompt [SQL Server replication]
ms.assetid: 5487b645-d99b-454c-8bd2-aff470709a0e
caps.latest.revision: 51
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3107bcd2f7490c9583c0c8e9355ecc9ff9e20bd7
ms.lasthandoff: 04/11/2017

---
# <a name="replication-log-reader-agent"></a>Агент чтения журнала репликации
  Агент чтения журнала производит мониторинг журналов транзакций всех баз данных, включенных в репликацию транзакций, и копирует помеченные для репликации транзакции из журнала транзакций в базу данных распространителя.  
  
> [!NOTE]  
>  Параметры можно указывать в любом порядке. Если необязательные параметры не указаны, используются стандартные значения из профиля агента по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
logread [-?]   
-Publisher server_name[\instance_name]   
-PublisherDB publisher_database   
[-Continuous]  
[-DefinitionFile def_path_and_file_name]  
[-Distributor server_name[\instance_name]]  
[-DistributorLogin distributor_login]  
[-DistributorPassword distributor_password]  
[-DistributorSecurityMode [0|1]]  
[-EncryptionLevel [0|1|2]]  
[-ExtendedEventConfigFile configuration_path_and_file_name]  
[-HistoryVerboseLevel [0|1|2]]  
[-KeepAliveMessageInterval keep_alive_message_interval_seconds]  
[-LoginTimeOut login_time_out_seconds]  
[-LogScanThreshold scan_threshold]  
[-MaxCmdsInTran number_of_commands]  
[-MessageInterval message_interval]  
[-Output output_path_and_file_name]  
[-OutputVerboseLevel [0|1|2|3|4]]  
[-PacketSize packet_size]  
[-PollingInterval polling_interval]  
[-ProfileName profile_name]   
[-PublisherFailoverPartner server_name[\instance_name] ]  
[-PublisherSecurityMode [0|1]]  
[-PublisherLogin publisher_login]  
[-PublisherPassword publisher_password]   
[-QueryTimeOut query_time_out_seconds]  
[-ReadBatchSize number_of_transactions]   
[-ReadBatchThreshold read_batch_threshold]  
[-RecoverFromDataErrors]  
```  
  
## <a name="arguments"></a>Аргументы  
 **-?**  
 Отображает сведения об использовании.  
  
 **-Publisher** *server_name*[**\\***instance_name*]  
 Имя издателя. Укажите *server_name* , чтобы использовать экземпляр сервера [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию. Укажите *server_name***\\***instance_name* , чтобы обратиться к именованному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию.  
  
 **-PublisherDB** *publisher_database*  
 Имя базы данных издателя.  
  
 **-Continuous**  
 Указывает, производит ли агент непрерывный опрос транзакций для репликации. Если да, то он с заданным интервалом производит запрос из источника транзакций, даже если транзакции отсутствуют.  
  
 **-DefinitionFile** *путь_и_имя_файла_определения*  
 Путь к файлу определения агента. Файл определения агента содержит параметры командной строки для агента. Содержимое файла анализируется как для исполняемого файла. Значения аргумента, содержащие произвольные символы, следует заключать в двойные кавычки (").  
  
 **-Distributor** *server_name*[**\\***instance_name*]  
 Имя распространителя. Укажите *server_name* , чтобы использовать экземпляр сервера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию. Укажите *server_name***\\***instance_name* , чтобы обратиться к именованному экземпляру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] по умолчанию.  
  
 **-DistributorLogin** *distributor_login*  
 Имя входа распространителя.  
  
 **-DistributorPassword** *distributor_password*  
 Пароль распространителя.  
  
 **-DistributorSecurityMode** [ **0**| **1**]  
 Указывает режим безопасности распространителя. Значение **1** означает проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Windows, а значение **0** — проверку подлинности [!INCLUDE[msCoName](../../../includes/msconame-md.md)] (значение по умолчанию).  
  
 **-EncryptionLevel** [ **0** | **1** | **2** ]  
 Уровень шифрования по протоколу SSL, который используется агентом чтения журнала при установлении соединений.  
  
|Значение EncryptionLevel|Описание|  
|---------------------------|-----------------|  
|**0**|Указывает, что SSL не используется.|  
|**1**|Указывает, что SSL используется, но агент не проверяет, подписан ли сертификат сервера SSL надежным издателем.|  
|**2**|Указывает, что SSL используется и сертификат подтвержден.|  
  
 Дополнительные сведения см. в статье [Общие сведения о безопасности (репликация)](../../../relational-databases/replication/security/security-overview-replication.md).  
  
 **-ExtendedEventConfigFile** *configuration_path_and_file_name*  
 Задает путь и имя файла для XML-файла конфигурации расширенных событий. Файл конфигурации расширенных событий позволяет настраивать сеансы и включать события для трассировки.  
  
 **-HistoryVerboseLevel** [ **0**| **1**| **2**]  
 Указывает объем данных, заносимых в журнал во время операции чтения журнала. Влияние на производительность, оказываемое ведением журнала, можно максимально уменьшить, выбрав значение **1**.  
  
|Значение HistoryVerboseLevel|Описание|  
|-------------------------------|-----------------|  
|**0**||  
|**1**|По умолчанию. Всегда обновлять предыдущее сообщение журнала с таким же состоянием (запуск, выполнение, успех и т. д.). Если предыдущих сообщений с таким состоянием нет, то вставить новую запись.|  
|**2**|Если есть сообщения о таких событиях, как состояние простоя или долго выполняемое задание, то обновить предыдущие записи, в противном случае вставить новые записи журнала.|  
  
 **-KeepAliveMessageInterval** *keep_alive_message_interval_seconds*  
 Количество секунд до того, как поток журнала проверяет наличие соединений, ожидающих ответа от сервера. Это значение можно уменьшить, чтобы агент проверки не помечал агент чтения журнала как подозрительный при выполнении долго выполняющегося пакета. Значение по умолчанию — 300 секунд.  
  
 **-LoginTimeOut** *login_time_out_seconds*  
 Время ожидания входа в секундах. Значение по умолчанию — 15 секунд.  
  
 **-LogScanThreshold** *scan_threshold*  
 Только для внутреннего применения.  
  
 **-MaxCmdsInTran** *number_of_commands*  
 Задает максимальное количество инструкций, группируемых в транзакцию, когда агент чтения журнала записывает команды в базу данных распространителя. Использование этого параметра позволяет агенту чтения журнала и агенту распространителя разделять большие транзакции (состоящие из множества команд) на издателе на несколько меньших транзакций при применении команд на подписчике. Задание этого параметра может снизить вероятность состязаний на распространителе и уменьшить задержку при передаче данных между издателем и подписчиком. Поскольку исходная транзакция применяется меньшими по размеру блоками, подписчик может получить доступ к строкам большой логической транзакции издателя до завершения исходной транзакции, разбивая строгую атомарность транзакции. По умолчанию установлено значение **0**, сохраняющее границы транзакции издателя.  
  
> [!NOTE]  
>  Данный параметр не учитывается для публикаций, отличных от[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в подразделе «Настройка задания наборов транзакций» раздела [Performance Tuning for Oracle Publishers](../../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md).  
  
 **-MessageInterval** *message_interval*  
 Интервал времени, использующийся для ведения журнала. Событие регистрируется в журнале, когда после регистрации последнего события достигнуто значение **MessageInterval** .  
  
 При отсутствии реплицируемой транзакции на источнике агент передает распространителю сообщение об отсутствии транзакции. Данный параметр определяет период ожидания агента до передачи следующего сообщения об отсутствии транзакции. Агенты всегда передают сообщение об отсутствии транзакции, если на источнике после ранее обработанных реплицируемых транзакций не обнаруживается доступных транзакций. Значение по умолчанию — 60 секунд.  
  
 **-Output** *output_path_and_file_name*  
 Путь к выходному файлу агента. Если имя файла не указано, данные выводятся на консоль. Если указанный файл существует, то выходные данные добавляются в конец файла.  
  
 **-OutputVerboseLevel** [ **0**| **1**| **2** | **3** | **4** ]  
 Указывает, должны ли выводимые данные быть подробными.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**0**|Выводятся только сообщения об ошибках.|  
|**1**|Выводятся все сообщения о ходе выполнения агента.|  
|**2** (по умолчанию)|Выводятся все сообщения об ошибках и о ходе выполнения агента.|  
|**3**|Выводятся первые 100 байт для каждой реплицируемой команды.|  
|**4**|Выводятся все реплицируемые команды.|  
  
 Значения 2-4 могут оказаться полезными при отладке.  
  
 **-PacketSize** *packet_size*  
 Размер пакета в байтах. Значение по умолчанию равно 4 096 байт.  
  
 **-PollingInterval** *polling_interval*  
 Определяет частоту (в секундах) опроса журнала о реплицируемых транзакциях. Значение по умолчанию — 5 секунд.  
  
 **-ProfileName** *profile_name*  
 Указывает профиль агента, из которого берутся параметры агента. Если **ProfileName** имеет значение NULL, профиль агента отключен. Если значение **ProfileName** не указано, используется профиль по умолчанию для агентов этого типа. Дополнительные сведения см. в статье [Профили агента репликации](../../../relational-databases/replication/agents/replication-agent-profiles.md).  
  
 **-PublisherFailoverPartner** *server_name*[**\\***instance_name*]  
 Указывает партнера по обеспечению отработки отказа служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , участвующего в сеансе зеркального отображения базы данных с базой данных публикации. Дополнительные сведения см. в статье [Database Mirroring and Replication &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md).  
  
 **-PublisherSecurityMode** [ **0**| **1**]  
 Указывает режим безопасности издателя. Значение **0** означает проверку подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (по умолчанию), а значение **1** — проверку подлинности Windows.  
  
 **-PublisherLogin** *publisher_login*  
 Имя входа издателя.  
  
 **-PublisherPassword** *publisher_password*  
 Пароль издателя.  
  
 **-QueryTimeOut** *query_time_out_seconds*  
 Время ожидания запроса в секундах. Значение по умолчанию — 1800 секунд.  
  
 **-ReadBatchSize** *number_of_transactions*  
 Определяет максимальное число транзакций, которые считываются из журнала транзакций публикуемой базы данных за один цикл обработки (значение по умолчанию — 500). Агент будет продолжать считывать транзакции пакетами, пока все они не будут считаны из журнала. Этот параметр не поддерживается для издателей Oracle.  
  
 **-ReadBatchThreshold** *number_of_commands*  
 Определяет число команд репликации, которые считываются из журнала транзакций перед отправкой подписчику агентом распространителя. Значение по умолчанию равно 0. Если этот параметр не указан, то агент чтения журнала произведет считывание до конца журнала или до числа транзакций, указанного в параметре **-ReadBatchSize** .  
  
 **-RecoverFromDataErrors**  
 Указывает, что агент чтения журнала должен продолжить работу после возникновения ошибок данных в столбце, опубликованном издателем, отличным от SQL Server. По умолчанию такие ошибки приводят к завершению работы агента чтения журнала. Если указан параметр **-RecoverFromDataErrors**, то производится репликация ошибочных данных либо значениями NULL, либо другими соответствующими значениями, а предупреждающие сообщения записываются в таблицу [MSlogreader_history](../../../relational-databases/system-tables/mslogreader-history-transact-sql.md) . Этот параметр поддерживается только для издателей Oracle.  
  
## <a name="remarks"></a>Замечания  
  
> [!IMPORTANT]  
>  Если агент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] настроен для запуска от учетной записи локальной системы, а не пользователя домена (по умолчанию), то служба имеет доступ только к локальному компьютеру. Если агент чтения журнала, запускаемый агентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , настроен для входа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]с проверкой подлинности Windows, то работа агента слияния завершится ошибкой. Значением по умолчанию является проверка подлинности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения об изменении учетных записей безопасности см. в разделе [View and Modify Replication Security Settings](../../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Чтобы запустить агент чтения журнала, выполните из командной строки программу **logread.exe** . Дополнительные сведения см. в статье [Основные понятия исполняемых файлов агента репликации](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="change-history"></a>Журнал изменений  
  
|Обновленное содержимое|  
|---------------------|  
|Добавлен параметр **-ExtendedEventConfigFile** .|  
  
## <a name="see-also"></a>См. также:  
 [Администрирование агента репликации](../../../relational-databases/replication/agents/replication-agent-administration.md)  
  
  
