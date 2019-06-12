---
title: Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server | Документация Майкрософт
description: Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], connection string keywords
- MSOLEDBSQL, connection string keywords
- connection strings [OLE DB Driver for SQL Server]
- OLE DB Driver for SQL Server, connection string keywords
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 91e498a1db30df380d7f2009f0fe34a9b4541467
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778026"
---
# <a name="using-connection-string-keywords-with-ole-db-driver-for-sql-server"></a>Использование ключевых слов строки подключения с драйвером OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Некоторые драйвер OLE DB для API-интерфейсы SQL Server позволяет указать атрибуты соединения строки подключения. Строки подключения являются списками ключевых слов и связанных значений, причем каждое ключевое слово определяет определенный атрибут соединения.  
  
> [!NOTE]
> Драйвер OLE DB для SQL Server поддерживает неоднозначность строк соединения для обеспечения обратной совместимости (например, некоторые ключевые слова могут быть указаны несколько раз, и конфликты ключевых слов могут разрешаться на основании их положения или приоритета). Будущих версиях драйвер OLE DB для SQL Server не может разрешить неоднозначность в строках подключения. При изменении приложения для работы с драйвером OLE DB для SQL Server необходимо предусмотреть устранение любых зависимостей от неоднозначности строки соединения.  
  
 В следующих разделах описаны ключевые слова, которые могут использоваться с драйвером OLE DB для SQL Server и объекты данных ActiveX (ADO) при использовании драйвера OLE DB для SQL Server в качестве поставщика данных.  

  
## <a name="ole-db-driver-connection-string-keywords"></a>Ключевые слова в строке подключения драйвера OLE DB  
 Приложения OLE DB могут инициализировать объекты источника данных двумя способами:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 В первом случае строка поставщика может использоваться для инициализации свойств соединения посредством установки свойства DBPROP_INIT_PROVIDERSTRING в наборе свойств DBPROPSET_DBINIT. Во втором случае строка инициализации может быть передана методу **IDataInitialize::GetDataSource** для инициализации свойств соединения. При использовании каждого из этих методов инициализируются одни и те же свойства соединения OLE DB, однако, для этого применяются разные наборы ключевых слов. Набор ключевых слов, используемых методом **IDataInitialize::GetDataSource**, представляет собой по меньшей мере описание свойств, входящих в группу свойств инициализации.  
  
 Для любого параметра, указанного в строке поставщика, который имеет соответствующее свойство OLE DB, устанавливаемое в некоторое значение по умолчанию или явным образом установленное в некоторое значение, значение свойства OLE DB переопределяет значение, указанное в строке поставщика.  
  
 Логические свойства, установленные в строках поставщика через значения DBPROP_INIT_PROVIDERSTRING, устанавливаются с помощью значений «yes» и «no». Логические свойства, установленные в строках инициализации с помощью метода **IDataInitialize::GetDataSource**, устанавливаются с использованием значений true и false.  
  
 Приложения, использующие метод **IDataInitialize::GetDataSource**, также могут использовать ключевые слова, используемые методом **IDBInitialize::Initialize**, но только для свойств, у которых отсутствуют значения по умолчанию. Если приложение одновременно использует в строке инициализации ключевые слова методов **IDataInitialize::GetDataSource** и **IDBInitialize::Initialize**, используется ключевое слово метода **IDataInitialize::GetDataSource**. Настоятельно рекомендуется не использовать в приложениях ключевые слова **IDBInitialize::Initialize** в строках подключения **IDataInitialize:GetDataSource**, так как это поведение может не поддерживаться в будущих версиях.  
  
> [!NOTE]  
>  Строка подключения, передаваемая в метод **IDataInitialize::GetDataSource**, преобразуется в свойства, которые применяются методом **IDBProperties::SetProperties**. Если службы компонентов обнаруживают описание свойства в **IDBProperties::GetPropertyInfo**, это свойство будет применяться в качестве изолированного. В противном случае оно будет применяться через свойство DBPROP_PROVIDERSTRING. Например, если указать строку подключения **источник данных = server1; Server = server2**, **источника данных** устанавливается как свойство, но **Server** будет передано в строку поставщика.  
  
 Если указать несколько экземпляров одного свойства поставщика, то будет использоваться первое значение первого свойства.  
  
 Строки подключения, используемые в приложениях OLE DB, в которых используется DBPROP_INIT_PROVIDERSTRING и **IDBInitialize::Initialize**, имеют следующий синтаксис.  
  
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
|**Адрес**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес сервера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** обычно является сетевым именем сервера, но может быть и другим именем, например именем канала, IP-адресом или портом TCP/IP с адресом сокета.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Значение **адрес** имеет приоритет над значением, передаваемым в **Server** в строках соединения при использовании драйвера OLE DB для SQL Server. Также следует отметить, что строка `Address=;` соединяется с сервером, указанным в ключевом слове **Server**, а при использовании ключевых слов `Address= ;, Address=.;`, `Address=localhost;` и `Address=(local);`устанавливается соединение с локальным сервером.<br /><br /> Далее представлен полный синтаксис ключевого слова **Address**.<br /><br /> [_протокола_ **:** ]_адрес_[ **,** _порт &#124;\pipe\pipename_]<br /><br /> Параметр_протокол_ может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы). Дополнительные сведения о протоколах см. в разделе [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Если ни один из _протокола_ ни **сети** указывается ключевое слово, драйвер OLE DB для SQL Server будет использовать порядок протоколов, заданный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.|   
|**APP**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**ApplicationIntent**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения — **ReadOnly** и **ReadWrite**.<br /><br /> По умолчанию используется **ReadWrite**. Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова Database в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Проверка подлинности**<a href="#table1_1"><sup id="table1_authmode">**1**</sup></a>|SSPROP_AUTH_MODE|Указывает, используется проверка подлинности SQL или Active Directory. Допустимые значения:<br/><ul><li>`(not set)`: Режим проверки подлинности определяется другими ключевыми словами.</li><li>`ActiveDirectoryPassword:` Проверка подлинности Active Directory с помощью имени и пароля.</li><li>`ActiveDirectoryIntegrated:` Встроенная проверка подлинности Active Directory, используя учетные данные учетной записи Windows текущего вошедшего в систему пользователя.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `Integrated Security` (или `Trusted_Connection`) ключевые слова проверки подлинности или их соответствующие свойства установите для параметра `Authentication` ключевое слово (или его соответствующее свойство) для `ActiveDirectoryIntegrated` для включения нового поведения проверки шифрования и сертификат.<br/><br/><li>`SqlPassword:` Аутентификация с использованием имени и пароля.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `SQL Server` проверки подлинности установите для параметра `Authentication` ключевое слово (или его соответствующее свойство), чтобы `SqlPassword` для включения нового шифрования и поведение проверки сертификата.</ul>|
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «yes» и «no».|  
|**База данных**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Шифрование**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Язык**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover=Yes** при соединении с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=Yes** настраивает драйвер OLE DB для SQL Server для ускоренного обнаружения активного (в данный момент) сервера и подключения к нему. Возможные значения: **Да** и **Нет**. Значение по умолчанию — **No**. Пример:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Net**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**Network**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «yes» и «no». Если используется значение «no», объекту источника данных запрещено хранить конфиденциальные данные проверки подлинности.|  
|**PWD**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значением должно быть имя сервера в сети, IP-адрес или имя псевдонима диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> **Адрес** ключевого слова переопределяет **Server** ключевое слово.<br /><br /> Чтобы подключиться к экземпляру по умолчанию на локальном сервере, можно указать одно из следующих ключевых слов:<br /><br /> **Server=;**<br /><br /> **Server=;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(LocalDB)\\**  *instancename* **;**<br /><br /> Дополнительные сведения о поддержке LocalDB см. в разделе [драйвер OLE DB для SQL Server поддержка LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md).<br /><br /> Чтобы указать именованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], добавьте **\\** _InstanceName_.<br /><br /> Если сервер не указан, устанавливается соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Далее представлен полный синтаксис ключевого слова **Server**.<br /><br /> **Server =** [_протокола_ **:** ]*Server*[ **,** _порт_]<br /><br /> Параметр_протокол_ может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы).<br /><br /> Ниже приводится пример указания именованного канала:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Эта строка указывает протокол именованных каналов, именованный канал на локальном компьютере (`\\.\pipe`), имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) и имя по умолчанию для именованного канала (`sql/query`).<br /><br /> Если ни один из *протокола* ни **сети** указывается ключевое слово, драйвер OLE DB для SQL Server будет использовать порядок протоколов, заданный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.<br /><br /> Пробелы учитываются в начале значение, передаваемое **Server** в строках соединения при использовании драйвера OLE DB для SQL Server.|   
|**ServerSPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Если «Да», указывает, что драйвер OLE DB для SQL Server для использования режима проверки подлинности Windows для проверки имени входа. В противном случае для проверки имени входа драйвер OLE DB для SQL Server должен использовать имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; необходимо также указать ключевые слова UID и PWD.|  
|**TrustServerCertificate**<a href="#table1_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «yes» и «no». По умолчанию имеет значение «no», которое указывает, что сертификат сервера будет проверяться.|  
|**UID**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseFMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] определяет способ получения метаданных при подключении к  и более новым версиям. Допустимы значения «yes» и «no». Значение по умолчанию — «no».<br /><br />По умолчанию использует драйвер OLE DB для SQL Server [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) и [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) хранимые процедуры для получения метаданных. Эти хранимые процедуры имеют некоторые ограничения (например они завершится ошибкой, если временные таблицы). Установка **UseFMTONLY** «Да» указывает, что драйвер на использование [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) для извлечения метаданных вместо этого.|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Это ключевое слово является устаревшим, и его значение учитывается драйвером OLE DB для SQL Server.|  
|**WSID**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
<b id="table1_1">[1]:</b> для повышения безопасности при использовании токена доступа для проверки подлинности/свойства инициализации и их соответствующих ключевых слов строки подключения, изменяется поведение проверки шифрования и сертификат. Дополнительные сведения см. в разделе [шифрование и проверку сертификатов](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 Строки подключения, используемые приложениями OLE DB, в которых используется **IDataInitialize::GetDataSource**, имеют следующий синтаксис.  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Использование свойства должно соответствовать синтаксическим правилам, действующим в его области.  Например, в **WSID** вместо кавычек используются фигурные скобки ( **{}** ), а в **Application Name** используются апострофы ( **'** ) или двойные кавычки ( **"** ). Заключать в кавычки можно только строковые свойства. Заключение в кавычки целочисленного или перечисляемого свойства приведет к ошибке «Строка подключения не соответствует спецификации OLE DB».  
  
 Значения атрибутов можно при желании заключать в одинарные или двойные кавычки, а фактически это даже рекомендуется. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Используемый символ кавычек может также появиться в значении при условии его удвоения.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 Если строка подключения содержит несколько свойств из тех, которые приведены в следующей таблице, то будет использоваться значение последнего свойства.  
  
 В следующей таблице рассматриваются ключевые слова, которые можно использовать с **IDataInitialize::GetDataSource**.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|**Маркер доступа**<a href="#table2_1"><sup id="table2_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|Маркер доступа, используемый для проверки подлинности в Azure Active Directory. <br/><br/>**Примечание:** является ошибкой для указания этого ключевого слова, а также `UID`, `PWD`, `Trusted_Connection`, или `Authentication` их соответствующие свойства и ключевые слова или ключевых слов строки подключения.|
|**Application Name**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения — **ReadOnly** и **ReadWrite**.<br /><br /> По умолчанию используется **ReadWrite**. Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Проверка подлинности**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Указывает, используется проверка подлинности SQL или Active Directory. Допустимые значения:<br/><ul><li>`(not set)`: Режим проверки подлинности определяется другими ключевыми словами.</li><li>`ActiveDirectoryPassword:` Проверка подлинности Active Directory с помощью имени и пароля.</li><li>`ActiveDirectoryIntegrated:` Встроенная проверка подлинности Active Directory, используя учетные данные учетной записи Windows текущего вошедшего в систему пользователя.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `Integrated Security` (или `Trusted_Connection`) ключевые слова проверки подлинности или их соответствующие свойства установите для параметра `Authentication` ключевое слово (или его соответствующее свойство) для `ActiveDirectoryIntegrated` для включения нового поведения проверки шифрования и сертификат.<br/><br/><li>`SqlPassword:` Аутентификация с использованием имени и пароля.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `SQL Server` проверки подлинности установите для параметра `Authentication` ключевое слово (или его соответствующее свойство), чтобы `SqlPassword` для включения нового шифрования и поведение проверки сертификата.</ul>|
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова **Server** в этом разделе.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова DATABASE в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Встроенные функции безопасности**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения. Распознаются значения «true» и «false». Значение по умолчанию — «false».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover=True** при соединении с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** настраивает драйвер OLE DB для SQL Server для ускоренного обнаружения активного (в данный момент) сервера и подключения к нему. Допустимые значения — **True** и **False**. По умолчанию **False**. Пример:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова **Address** в этом разделе.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Для драйвер OLE DB для SQL Server это должен быть «MSOLEDBSQL».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Надежный сертификат сервера**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Использование шифрования данных**<a href="#table2_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] определяет способ получения метаданных при подключении к  и более новым версиям. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».<br /><br />По умолчанию использует драйвер OLE DB для SQL Server [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) и [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) хранимые процедуры для получения метаданных. Эти хранимые процедуры имеют некоторые ограничения (например они завершится ошибкой, если временные таблицы). Установка **использовать FMTONLY** в «true» указывает драйвер на использование [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) для извлечения метаданных вместо этого.|  
|**Идентификатор пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
<b id="table2_1">[1]:</b> для повышения безопасности при использовании токена доступа для проверки подлинности/свойства инициализации и их соответствующих ключевых слов строки подключения, изменяется поведение проверки шифрования и сертификат. Дополнительные сведения см. в разделе [шифрование и проверку сертификатов](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Примечание**. В строке подключения свойство Old Password устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которое является текущим паролем (возможно, с истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="activex-data-objects-ado-connection-string-keywords"></a>Ключевые слова строки подключения объектов данных ActiveX (ADO)  
 Приложения ADO устанавливают свойство **ConnectionString** объектов **ADODBConnection** или указывают строку подключения как параметр метода **Open** объектов **ADODBConnection**.  
  
 В приложениях ADO также могут применяться ключевые слова, используемые методом OLE DB **IDBInitialize::Initialize**, но только для свойств, у которых отсутствует значение по умолчанию. Если в строке инициализации приложения содержатся ключевые слова ADO и ключевые слова **IDBInitialize::Initialize**, используется параметр ключевого слова ADO. Настоятельно рекомендуется, чтобы приложение использовало для строк соединения только ключевые слова ADO.  
  
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
|**Маркер доступа**<a href="#table3_1"><sup id="table3_accesstoken">**1**</sup></a>|SSPROP_AUTH_ACCESS_TOKEN|Маркер доступа, используемый для проверки подлинности в Azure Active Directory.<br/><br/>**Примечание:** является ошибкой для указания этого ключевого слова, а также `UID`, `PWD`, `Trusted_Connection`, или `Authentication` их соответствующие свойства и ключевые слова или ключевых слов строки подключения.|
|**Application Intent**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения — **ReadOnly** и **ReadWrite**.<br /><br /> По умолчанию используется **ReadWrite**. Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Application Name**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Проверка подлинности**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_AUTH_MODE|Указывает, используется проверка подлинности SQL или Active Directory. Допустимые значения:<br/><ul><li>`(not set)`: Режим проверки подлинности определяется другими ключевыми словами.</li><li>`ActiveDirectoryPassword:` Проверка подлинности Active Directory с помощью имени и пароля.</li><li>`ActiveDirectoryIntegrated:` Встроенная проверка подлинности Active Directory, используя учетные данные учетной записи Windows текущего вошедшего в систему пользователя.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `Integrated Security` (или `Trusted_Connection`) ключевые слова проверки подлинности или их соответствующие свойства установите для параметра `Authentication` ключевое слово (или его соответствующее свойство) для `ActiveDirectoryIntegrated` для включения нового поведения проверки шифрования и сертификат.<br/><br/><li>`SqlPassword:` Аутентификация с использованием имени и пароля.</li><br/>**Примечание:** он имеет **рекомендуется** , приложениями, использующими `SQL Server` проверки подлинности установите для параметра `Authentication` ключевое слово (или его соответствующее свойство), чтобы `SqlPassword` для включения нового шифрования и поведение проверки сертификата.</ul>|
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Connect Timeout**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Current Language**|SSPROPT_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова **Server** в этом разделе.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Задает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**Failover Partner SPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова DATABASE в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Встроенные функции безопасности**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Распознаются значения «true» и «false». По умолчанию используется значение «false».|  
|**MultiSubnetFailover**|SSPROP_INIT_MULTISUBNETFAILOVER|Всегда указывайте **MultiSubnetFailover=True** при соединении с прослушивателем группы доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или экземпляром отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **MultiSubnetFailover=True** настраивает драйвер OLE DB для SQL Server для ускоренного обнаружения активного (в данный момент) сервера и подключения к нему. Допустимые значения — **True** и **False**. По умолчанию **False**. Пример:<br /><br /> `MultiSubnetFailover=True`<br /><br /> Дополнительные сведения о драйвере OLE DB для SQL Server поддерживается для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], см. в разделе [драйвер OLE DB для SQL Server поддерживает высокую доступность, аварийное восстановление](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Дополнительные сведения о допустимом синтаксисе адресов см. в описании ключевого слова **Address** в этом разделе.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Packet Size**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Persist Security Info**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Для драйвер OLE DB для SQL Server это должен быть «MSOLEDBSQL».|  
|**Server SPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Пустая строка вызывает драйвер OLE DB для SQL Server для использования по умолчанию, сформированное поставщиком имя участника-службы.|  
|**Надежный сертификат сервера**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Использование шифрования данных**<a href="#table3_1"><sup>**1**</sup></a>|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**Use FMTONLY**|SSPROP_INIT_USEFMTONLY|[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] определяет способ получения метаданных при подключении к  и более новым версиям. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».<br /><br />По умолчанию использует драйвер OLE DB для SQL Server [sp_describe_first_result_set](../../../relational-databases/system-stored-procedures/sp-describe-first-result-set-transact-sql.md) и [sp_describe_undeclared_parameters](../../../relational-databases/system-stored-procedures/sp-describe-undeclared-parameters-transact-sql.md) хранимые процедуры для получения метаданных. Эти хранимые процедуры имеют некоторые ограничения (например они завершится ошибкой, если временные таблицы). Установка **использовать FMTONLY** в «true» указывает драйвер на использование [SET FMTONLY](../../../t-sql/statements/set-fmtonly-transact-sql.md) для извлечения метаданных вместо этого.|  
|**Идентификатор пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Workstation ID**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
<b id="table3_1">[1]:</b> для повышения безопасности при использовании токена доступа для проверки подлинности/свойства инициализации и их соответствующих ключевых слов строки подключения, изменяется поведение проверки шифрования и сертификат. Дополнительные сведения см. в разделе [шифрование и проверку сертификатов](../features/using-azure-active-directory.md#encryption-and-certificate-validation).

 **Примечание**. В строке подключения свойство Old Password устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которое является текущим паролем (возможно, с истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="see-also"></a>См. также раздел  
 [Создание приложений с помощью драйвера OLE DB для SQL Server](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
  
  
