---
title: Использование ключевых слов строки подключения с помощью драйвера OLE DB для SQL Server | Документы Microsoft
description: Использование ключевых слов строки подключения с помощью драйвера OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb|applications
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7917f0c1344ff8e79250791d1b262cece9ca3c4c
ms.sourcegitcommit: 8b332c12850c283ae413e0b04b2b290ac2edb672
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2018
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Использование ключевых слов строки подключения с помощью драйвера OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Некоторые драйвер OLE DB для SQL Server API позволяет указать атрибуты соединения строки подключения. Строки подключения являются списками ключевых слов и связанных значений, причем каждое ключевое слово определяет определенный атрибут соединения.  
  
> **Примечание:** драйвер OLE DB для SQL Server поддерживает неоднозначность строк соединения для обеспечения обратной совместимости (например, некоторые ключевые слова могут быть указаны несколько раз и конфликтующих ключевых слов могут разрешаться по положению или приоритет). Будущие выпуски драйвер OLE DB для SQL Server могут не позволять неоднозначность в строках соединения. Рекомендуется при изменении приложениям использовать драйвер OLE DB для SQL Server, чтобы предусмотреть Устранение любых зависимостей от неоднозначности строки соединения.  
  
 В следующих разделах описаны ключевые слова, которые можно использовать с помощью драйвера OLE DB для SQL Server и объекты данных ActiveX (ADO) при использовании драйвера OLE DB для SQL Server в качестве поставщика данных.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Ключевые слова строки подключения OLE DB для драйверов  
 Приложения OLE DB могут инициализировать объекты источника данных двумя способами:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 В первом случае строка поставщика может использоваться для инициализации свойств соединения посредством установки свойства DBPROP_INIT_PROVIDERSTRING в наборе свойств DBPROPSET_DBINIT. Во втором случае строка инициализации может быть передан **IDataInitialize::GetDataSource** метод для инициализации свойств соединения. При использовании каждого из этих методов инициализируются одни и те же свойства соединения OLE DB, однако, для этого применяются разные наборы ключевых слов. Набор ключевых слов, используемых **IDataInitialize::GetDataSource** является как минимум описание свойств, входящих в группу свойств инициализации.  
  
 Для любого параметра, указанного в строке поставщика, который имеет соответствующее свойство OLE DB, устанавливаемое в некоторое значение по умолчанию или явным образом установленное в некоторое значение, значение свойства OLE DB переопределяет значение, указанное в строке поставщика.  
  
 Логические свойства, установленные в строках поставщика через значения DBPROP_INIT_PROVIDERSTRING, устанавливаются с помощью значений «yes» и «no». Логические свойства, установленные в строках инициализации с помощью **IDataInitialize::GetDataSource** задаются с использованием значения «true» и «false».  
  
 Приложения, использующие **IDataInitialize::GetDataSource** также можно использовать ключевые слова, используемые **IDBInitialize::Initialize** , но только для свойств, которые не имеют значения по умолчанию. Если приложение использует оба **IDataInitialize::GetDataSource** ключевое слово и **IDBInitialize::Initialize** ключевое слово в строке инициализации **IDataInitialize::GetDataSource** применяется ключевое слово. Настоятельно рекомендуется, чтобы приложения не используют **IDBInitialize::Initialize** ключевые слова в **IDataInitialize: Getdatasource** строки подключения, как это поведение может не поддерживаться в будущих выпусках.  
  
> [!NOTE]  
>  Строка соединения, передаваемая через **IDataInitialize::GetDataSource** преобразуется в свойства и применять через **IDBProperties::SetProperties**. Если службы компонентов обнаруживают описание свойства в **IDBProperties::GetPropertyInfo**, это свойство будет применяться в качестве изолированного. В противном случае оно будет применяться через свойство DBPROP_PROVIDERSTRING. Например, если указать строку подключения **источник данных = server1; Server = server2**, **источника данных** задается как свойство, но **сервера** будет передано в строку поставщика.  
  
 Если указать несколько экземпляров одного свойства поставщика, то будет использоваться первое значение первого свойства.  
  
 Строки подключения, используемые приложениями OLE DB используется DBPROP_INIT_PROVIDERSTRING и **IDBInitialize::Initialize** имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в фигурные скобки. Это позволяет избежать проблем, если значения атрибутов содержат символы, отличные от буквенно-цифровых. Предполагается, что первая закрывающая фигурная скобка в значении служит признаком конца значения, поэтому само значение не может содержать символы закрывающей фигурной скобки.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 В следующей таблице рассматриваются ключевые слова, которые можно использовать со свойством DBPROP_INIT_PROVIDERSTRING.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|**Addr**|SSPROP_INIT_NETWORKADDRESS|Синоним для «Address».|  
|**Адрес**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес сервера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Адрес** обычно является сетевым именем сервера, но могут быть другие имена, например канала, IP-адрес или порт и адрес TCP/IP.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Значение **адрес** имеет приоритет над значением, передаваемым в **сервера** в строках соединения при использовании драйвера OLE DB для SQL Server. Также Обратите внимание, что `Address=;` будут подключаться к серверу, указанному в **сервера** ключевое слово, тогда как `Address= ;, Address=.;`, `Address=localhost;`, и `Address=(local);` устанавливается соединение с локальным сервером.<br /><br /> Полный синтаксис **адрес** ключевое слово является следующим образом:<br /><br /> [*протокола ***:**]*адрес*[**, *** порт &#124;\pipe\pipename*]<br /><br /> Параметр*протокол* может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы). Дополнительные сведения о протоколах см. в разделе [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Если ни одна из *протокола* ни **сети** указано ключевое слово, драйвер OLE DB для SQL Server будет использовать порядок протоколов, заданный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *порт* — это порт для подключения к, на указанном сервере. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Для использования **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова базы данных в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**Функция AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «yes» и «no».|  
|**База данных**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Шифрование**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Язык**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover = Yes** при подключении к прослушивателю группы доступности из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] группы доступности или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра отказоустойчивого кластера. **MultiSubnetFailover = Yes** настраивает драйвер OLE DB для SQL Server для обеспечения более быстрое обнаружение и подключение к серверу (активного). Возможные значения: **Да** и **Нет**. Значение по умолчанию — **нет**. Например:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Сетевая библиотека**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «yes» и «no». Если используется значение «no», объекту источника данных запрещено хранить конфиденциальные данные проверки подлинности.|  
|**PWD**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значением должно быть имя сервера в сети, IP-адрес или имя псевдонима диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> **Адрес** ключевого слова переопределяет **сервера** ключевое слово.<br /><br /> Чтобы подключиться к экземпляру по умолчанию на локальном сервере, можно указать одно из следующих ключевых слов:<br /><br /> **Server=;**<br /><br /> **Server=.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** *instancename* **;**<br /><br /> Дополнительные сведения о поддержке LocalDB см. в разделе [драйвер OLE DB для SQL Server поддержка LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Чтобы указать именованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], добавьте  **\\ ***InstanceName*.<br /><br /> Если сервер не указан, соединение устанавливается с экземпляром по умолчанию на локальном компьютере.<br /><br /> Если указать IP-адрес, убедитесь, что включен протокол TCP/IP или именованных каналов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> Полный синтаксис **сервера** ключевое слово является следующим:<br /> <br /> **Server =**[*протокола***:**] *Сервер*[**, *** порт*]<br /><br /> Параметр*протокол* может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы).<br /><br /> Ниже приводится пример указания именованного канала:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Эта строка указывает протокол именованных каналов, именованный канал на локальном компьютере (`\\.\pipe`), имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) и имя по умолчанию для именованного канала (`sql/query`).<br /><br /> Если ни одна из *протокола* ни **сети** указано ключевое слово, драйвер OLE DB для SQL Server будет использовать порядок протоколов, заданный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *порт* — это порт для подключения к, на указанном сервере. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.<br /><br /> Пробелы учитываются в начале значение, передаваемое **сервера** в строках соединения при использовании драйвера OLE DB для SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Когда «yes» указывает, что драйвер OLE DB для SQL Server использовать проверку подлинности Windows для проверки имени входа. В противном случае значение указывает, что драйвер OLE DB для SQL Server для использования [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо указать имя пользователя и пароль для проверки имени входа и ключевые слова UID и PWD.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «yes» и «no». По умолчанию имеет значение «no», которое указывает, что сертификат сервера будет проверяться.|  
|**UID**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Это ключевое слово является устаревшим, и его значение учитывается драйвером OLE DB для SQL Server.|  
|**WSID**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 Строки подключения, используемые приложениями OLE DB с помощью **IDataInitialize::GetDataSource** имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Использование свойства должно соответствовать синтаксическим правилам, действующим в его области.  Например **WSID** используются фигурные скобки (**{}**) кавычки и **имя_приложения** апострофы (**"**) или двойные (**«**) кавычки. Заключать в кавычки можно только строковые свойства. Заключение в кавычки целочисленного или перечисляемого свойства приведет к ошибке «Строка подключения не соответствует спецификации OLE DB».  
  
 Значения атрибутов можно при желании заключать в одинарные или двойные кавычки, а фактически это даже рекомендуется. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Используемый символ кавычек может также появиться в значении при условии его удвоения.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 Если строка подключения содержит несколько свойств из тех, которые приведены в следующей таблице, то будет использоваться значение последнего свойства.  
  
 В следующей таблице описываются ключевые слова, которые могут быть использованы с **IDataInitialize::GetDataSource**:  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|**Application Name**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Назначение приложения**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**Функция AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Текущий язык**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании **сервера** ключевого слова в этом разделе.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**FailOver Partner имени участника-службы**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Для использования **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова базы данных в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Встроенные функции безопасности**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**Соединения режима MARS**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения. Распознаются значения «true» и «false». Значение по умолчанию — «false».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover = True** при подключении к прослушивателю группы доступности из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] группы доступности или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра отказоустойчивого кластера. **MultiSubnetFailover = True** настраивает драйвер OLE DB для SQL Server для обеспечения более быстрое обнаружение и подключение к серверу (активного). Допустимые значения — **True** и **False**. По умолчанию **False**. Например:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Сетевой адрес**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании **адрес** ключевого слова в этом разделе.|  
|**Сетевая библиотека**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Сохранять сведения о безопасности**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Драйвер OLE DB для SQL Server это будет «MSOLEDBSQL».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Надежный сертификат сервера**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**Идентификатор пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Идентификатор рабочей станции**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 **Примечание** в строке подключения свойство «Old Password» устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которой является текущий пароль (возможно истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Ключевые слова строки подключения объектов данных ActiveX (ADO)  
 Приложения ADO устанавливают **ConnectionString** свойство **ADODBConnection** объектов или указать строку подключения в качестве параметра **откройте** метод **ADODBConnection** объектов.  
  
 Приложения ADO могут использовать ключевые слова, используемые в OLE DB **IDBInitialize::Initialize** метода, но только для свойств, которые не имеют значения по умолчанию. Если приложение использует оба ключевых слова ADO и **IDBInitialize::Initialize** будет использовать ключевые слова в строке инициализации параметр ключевого слова ADO. Настоятельно рекомендуется, чтобы приложение использовало для строк соединения только ключевые слова ADO.  
  
 Строки подключения, используемые ADO, имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=["]attribute-value["]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в двойные кавычки. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Значения атрибутов не могут содержать двойные кавычки.  
  
 В следующей таблице описываются ключевые слова, которые можно использовать со строками соединения ADO.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|**Назначение приложения**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможными значениями являются **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**Функция AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Текущий язык**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании **сервера** ключевого слова в этом разделе.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Задает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**FailOver Partner имени участника-службы**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Для использования **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова базы данных в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Встроенные функции безопасности**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**Соединения режима MARS**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Распознаются значения «true» и «false». По умолчанию используется значение «false».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover = True** при подключении к прослушивателю группы доступности из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] группы доступности или [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] экземпляра отказоустойчивого кластера. **MultiSubnetFailover = True** настраивает драйвер OLE DB для SQL Server для обеспечения более быстрое обнаружение и подключение к серверу (активного). Допустимые значения — **True** и **False**. По умолчанию **False**. Например:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Дополнительные сведения о драйвер OLE DB для SQL Server поддержку [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], в разделе [драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Сетевой адрес**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании **адрес** ключевого слова в этом разделе.|  
|**Сетевая библиотека**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Сохранять сведения о безопасности**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Драйвер OLE DB для SQL Server это будет «MSOLEDBSQL».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы в результате пустая строка.|  
|**Надежный сертификат сервера**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**Идентификатор пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Идентификатор рабочей станции**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 **Примечание** в строке подключения свойство «Old Password» устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которой является текущий пароль (возможно истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
