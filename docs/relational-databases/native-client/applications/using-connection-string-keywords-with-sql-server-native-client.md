---
title: Родной клиент, ключевые слова соединения S'L
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- sql13.swb.connecttoserver.options.registeredservers.f1
helpviewer_keywords:
- data access [SQL Server Native Client], connection string keywords
- SQLNCLI, connection string keywords
- connection strings [SQL Server Native Client]
- SQL Server Native Client, connection string keywords
ms.assetid: 16008eec-eddf-4d10-ae99-29db26ed6372
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d4c6dd4f0cecc7b2772e82386d552e8b391d6dfd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303925"
---
# <a name="using-connection-string-keywords-with-sql-server-native-client"></a>Использование ключевых слов строки подключения с собственным клиентом SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Некоторые API собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используют строки подключения, чтобы указать свойства соединения. Строки подключения являются списками ключевых слов и связанных значений, причем каждое ключевое слово определяет определенный атрибут соединения.  

> [!IMPORTANT]
> Родной [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] клиент OLE DB (S'LNCLI) по-прежнему является амортизированным, и не рекомендуется использовать его для новых работ по разработке. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.    
> Для получения информации [см.](../../../connect/oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

> [!NOTE]
> Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает неоднозначность строк соединения для обеспечения обратной совместимости (например, некоторые ключевые слова могут быть указаны несколько раз, и конфликты ключевых слов могут разрешаться на основании их положения или приоритета). При изменении приложения для работы с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо предусмотреть устранение любых зависимостей от неоднозначности строки соединения.  
  
 В следующих разделах описываются ключевые слова, которые могут использоваться с поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и объектами данных ActiveX (ADO) при использовании собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в качестве поставщика данных.  
  
## <a name="odbc-driver-connection-string-keywords"></a>Ключевые слова строки строки соединения ДРАЙВЕРа ODBC  
 Приложения ODBC используют строки соединения в качестве параметров для функций [S'LDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) и [S'LBrowseConnect.](../../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md)  
  
 Строки подключения, используемые ODBC, имеют следующий синтаксис:  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[{]attribute-value[}]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 Значения атрибутов можно (и рекомендуется) дополнительно заключить в фигурные скобки. Это позволяет избежать проблем, если значения атрибутов содержат символы, отличные от буквенно-цифровых. Предполагается, что первая закрывающая фигурная скобка в значении служит признаком конца значения, поэтому само значение не может содержать символы закрывающей фигурной скобки.  
  
 В следующей таблице описываются ключевые слова, которые можно использовать со строкой соединения ODBC.  
  
|Ключевое слово|Описание|  
|-------------|-----------------|  
|**Addr**|Синоним для «Address».|  
|**Адрес**|Сетевой адрес сервера, на котором выполняется экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. **Address** обычно является сетевым именем сервера, но может быть и другим именем, например именем канала, IP-адресом или портом TCP/IP с адресом сокета.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Значение **Адреса** имеет приоритет над значением, передаваемым **серверу** в строках подключения ODBC при использовании [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Также обратите `Address=;` внимание, что будет подключаться к серверу, `Address=(local);` указанному в ключевом слове **сервера,** в то время как `Address= ;, Address=.;`, `Address=localhost;`и все это вызывает подключение к локальному серверу.<br /><br /> Далее представлен полный синтаксис ключевого слова **Address**.<br /><br /> [_protocol_**:**]*Address*[**,**_port &#124;\pipe\pipename_]<br /><br /> Параметр*протокол* может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы). Дополнительные сведения см. в статье [Настройка клиентских протоколов](../../../database-engine/configure-windows/configure-client-protocols.md).<br /><br /> Если ни *протокол,* ни ключевое [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] слово **Сети** не указаны, родной клиент будет использовать порядок протокола, указанный в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.|  
|**AnsiNPW**|Если задано значение «yes», то в драйвере используются определяемые стандартами ANSI правила обработки сравнений со значением NULL, дополнения символьных данных, формирования предупреждений и выполнения операция объединений со значением NULL. При использовании значения «no» определенные стандартом ANSI действия не используются. Для получения дополнительной информации о поведении ANSI NPW [см.](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)|  
|**Приложение**|Название приложения, вызывающего [S'LDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) (необязательно). Если указано, это значение хранится в столбце **master.dbo.sysprocesses** **program_name** и возвращается [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) и [APP_NAME](../../../t-sql/functions/app-name-transact-sql.md) функций.|  
|**ApplicationНамерение**|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения **ReadOnly** и **ReadWrite**. Значение по умолчанию — **ReadWrite**.  Пример:<br /><br /> `ApplicationIntent=ReadOnly`<br /><br /> Для получения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более подробной информации о поддержке родного [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]клиента, см. [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)|  
|**AttachDBFileName**|Имя первичного файла присоединяемой базы данных. Необходимо указать полный путь и экранировать любые символы \ при использовании символьной строковой переменной C:<br /><br /> `AttachDBFileName=c:\\MyFolder\\MyDB.mdf`<br /><br /> Эта база данных присоединяется и становится для соединения базой данных по умолчанию. Для использования **AttachDBFileName** необходимо также указать имя базы данных либо в параметре [sLDriverConnect](../../../relational-databases/native-client-odbc-api/sqldriverconnect.md) DATABASE, либо в SQL_COPT_CURRENT_CATALOG атрибуте соединения. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**AutoTranslate**|Если имеет значение «yes», строки символов ANSI, которыми обмениваются клиент и сервер, переводятся с использованием Юникода, чтобы минимизировать проблемы сопоставления символов национальных алфавитов кодовых страниц клиента и сервера.<br /><br /> Клиент SQL_C_CHAR данные, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] отправленные на **символ,** **varchar**, или **текст** переменной, параметр, или столбец преобразуется из символа в Unicode с помощью клиента ANSI страницы кода (ACP), а затем преобразуется из Unicode в символ с помощью ACP сервера.<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]**char,** **varchar**или **текстовые** данные, отправленные клиенту SQL_C_CHAR переменной преобразуется из символа в Unicode с помощью сервера ACP, а затем преобразуется из Unicode в символ с помощью клиента ACP.<br /><br /> Эти преобразования выполняются на клиенте драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Для этого необходимо, чтобы на сервере была доступна такая же кодовая страница ANSI, какая используется на клиенте.<br /><br /> Следующие параметры не влияют на преобразования, выполняемые для этих передач.<br /><br /> \*Unicode SQL_C_WCHAR данные клиента, отправленные на **char,** **varchar**или **текст** на сервере.<br /><br /> &#42; **char,** **varchar** **или** текстовые данные сервера, отправленные в unicode SQL_C_WCHAR переменной клиента.<br /><br /> \*ANSI SQL_C_CHAR данные клиента, отправленные в Unicode **nchar,** **nvarchar**или **ntext** на сервере.<br /><br /> \*Unicode **nchar**, **nvarchar**или **данные сервера ntext,** отправленные в SQL_C_CHAR an ANSI на клиенте.<br /><br /> Если имеет значение «no», перевод символов не выполняется.<br /><br /> Драйвер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC не переводит символ ANSI SQL_C_CHAR данные, отправленные на **символ,** **varchar**или **текстовые** переменные, параметры или столбцы на сервере. Перевод не выполняется на **char,** **varchar**или **текстовых** данных, отправленных с сервера для SQL_C_CHAR переменных на клиенте.<br /><br /> Если клиент и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используют разные кодовые страницы ANSI, символы национального алфавита могут быть переведены неправильно.|  
|**База данных**|Имя базы данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], используемой для соединения по умолчанию. Если **база данных** не указана, используется база данных по умолчанию, определенная для входа. База данных по умолчанию из источника данных ODBC переопределяет базу данных по умолчанию, определенную для имени входа. База данных должна быть существующей базой данных, если не указано **также AttachDBFileName.** Если также указан **AttachDBFileName,** основной файл, на который он указывает, прикрепляется и присваивается имя базы данных, указанное **Базисом данных.**|  
|**Драйвер**|Имя водителя, возвращенное [S'LDrivers](../../../relational-databases/native-client-odbc-api/sqldrivers.md). Значение ключевого слова для драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] – «{SQL Server Native Client 11.0}». Ключевое слово **Сервера** требуется, если **драйвер** указан и **DriverCompletion** установлен SQL_DRIVER_NOPROMPT.<br /><br /> Для получения более подробной информации об именах драйверов [см.](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)|  
|**Dsn**|Имя существующего пользователя ODBC или системного источника данных. Это ключевое слово переопределяет любые значения, которые могут быть указаны в ключевых словах **сервера,** **сети**и **адреса.**|  
|**Шифрование**|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**Резервный**|Это ключевое слово является устаревшим, и его значение не учитывается драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Failover_Partner**|Имя сервера партнера по обеспечению отработки отказа, которое будет использоваться, если невозможно установить соединение с сервером-источником.|  
|**FailoverPartnerSPN**|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное драйвером.|  
|**FileDSN**|Имя существующего файлового источника данных ODBC.|  
|**Язык**|Имя языка [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (необязательно). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]может хранить сообщения для нескольких языков в **sysmessages.** При подключении [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] к нескольким языкам **язык** определяет, какой набор сообщений используется для соединения.|  
|**MARS_Connection**|Включает или отключает режим MARS для соединения. Распознаются значения «yes» и «no». Значение по умолчанию — «no».|  
|**MultiSubnetFailover**|Всегда укажите **мультисубнетFailover-Да** при подключении к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] группе доступности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] слушателя группы доступности группы или Failover кластера Instance. **multiSubnetFailover-Yes** настраивает [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] родного клиента, чтобы обеспечить более быстрое обнаружение и подключение к (в настоящее время) активному серверу. Возможные значения **Да** и **Нет**. Значение по умолчанию — **No**. Пример:<br /><br /> `MultiSubnetFailover=Yes`<br /><br /> Для получения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более подробной информации о поддержке родного [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]клиента, см. [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)|  
|**Чистая**|Синоним для «Network».|  
|**Сеть**|Допустимые **значения: dbnmpntw** (названные трубы) и **dbmssocn** (TCP/IP).<br /><br /> Ошибочно указывать как значение для ключевого слова **Сети,** так и приставку протокола на ключевом слове **Сервера.**|  
|**Pwd**|Пароль для учетной записи входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], указанный в параметре UID. **PWD** не нужно указывать, есть ли у входа пароль`Trusted_Connection = yes`NULL или при использовании подлинности Windows ().|  
|**QueryLog_On**|Если имеет значение «yes», для соединения включается регистрация данных длительных запросов. Если имеет значение «no», данные длительных запросов не регистрируются.|  
|**QueryLogFile**|Полный путь и имя файла, используемого для регистрации данных длительных запросов.|  
|**КвириЛогТайм**|Строка цифровых символов, указывающая порог (в миллисекундах) для регистрации длительных запросов. Любой запрос, ответ на который не поступает за указанное время, записывается в файл регистрации длительных запросов.|  
|**QuotedId**|Если имеет значение «yes», параметр QUOTED_IDENTIFIERS при соединении устанавливается в значение ON. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует правила ISO в отношении использования кавычек в инструкциях SQL. Если параметр равен «no», то параметр QUOTED_IDENTIFIERS для соединения отключается (принимает значение OFF). В этом случае [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] следует правилам устаревших версий [!INCLUDE[tsql](../../../includes/tsql-md.md)] относительно использования кавычек в инструкциях SQL. Для получения дополнительной [информации см.](../../../relational-databases/native-client-odbc-queries/executing-statements/effects-of-iso-options.md)|  
|**Региональные**|Если имеет значение «yes», драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует настройки клиента при преобразовании данных валюты, даты и времени в символьные данные. Преобразование является односторонним, то есть драйвер не распознает строки даты и значения валюты, отличные от стандарта ODBC, например, параметры инструкций INSERT или UPDATE. Если имеет значение «no», драйвер использует стандартные строки ODBC для представления данных валюты, даты и времени, преобразуемых в символьные данные.|  
|**SaveFile**|Имя исходного файла данных ODBC, в который сохраняются атрибуты текущего соединения, если соединение успешно установлено.|  
|**Server**|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Значением должно быть имя сервера в сети, IP-адрес или имя псевдонима диспетчера конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Ключевое слово **Address** переопределяет ключевое слово **Server**.<br /><br /> Чтобы подключиться к экземпляру по умолчанию на локальном сервере, можно указать одно из следующих ключевых слов:<br /><br /> **Сервер;**<br /><br /> **Сервера.;**<br /><br /> **Server=(local);**<br /><br /> **Server=(local);**<br /><br /> **Server=(localhost);**<br /><br /> **Server=(localdb)\\** _instancename_ **;**<br /><br /> Для получения более подробной информации о поддержке LocalDB, [SQL Server Native Client Support for LocalDB](../../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)см.<br /><br /> Указать названный [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]экземпляр , **\\**приложение _InstanceName_.<br /><br /> Если сервер не указан, устанавливается соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Если указывается IP-адрес, убедитесь, что в диспетчере конфигурации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включен протокол TCP/IP или протокол именованных каналов.<br /><br /> Далее представлен полный синтаксис ключевого слова **Server**.<br /><br /> **Server=**[_protocol_**:**]*Server*[**,**_port_]<br /><br /> Параметр*протокол* может иметь значение **tcp** (TCP/IP), **lpc** (общая память) или **np** (именованные каналы).<br /><br /> Ниже приводится пример указания именованного канала:<br /><br /> `np:\\.\pipe\MSSQL$MYINST01\sql\query`<br /><br /> Эта строка указывает протокол именованных каналов, именованный канал на локальном компьютере (`\\.\pipe`), имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (`MSSQL$MYINST01`) и имя по умолчанию для именованного канала (`sql/query`).<br /><br /> Если ни *протокол,* ни ключевое [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] слово **Сети** не указаны, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] родной клиент будет использовать порядок протокола, указанный в configuration Manager.<br /><br /> *port* — это порт указанного сервера, к которому выполняется подключение. По умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует порт 1433.<br /><br /> Пробелы игнорируются в начале значения, передаваемого **серверу** в строках подключения ODBC при использовании [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|**СерверSPN**|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное драйвером.|  
|**StatsLog_On**|Если имеет значение «yes», включается сбор данных производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Если имеет значение «no», данные производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для соединения недоступны.|  
|**StatsLogFile**|Полный путь и имя файла для записи статистики производительности драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Trusted_Connection**|Значение «yes» предписывает драйверу ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать режим проверки подлинности Windows для проверки имени входа. В противном случае для проверки имени входа драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен использовать имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также необходимо указать ключевые слова UID и PWD.|  
|**TrustServerCertificate**|При использовании с **шифрованием**позволяет шифрование с помощью самоподписанного серверного сертификата.|  
|**ИД пользователя**|Допустимая учетная запись входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ключевое слово UID не нужно указывать при использовании проверки подлинности Windows.|  
|**UseProcForPrepare**|Это ключевое слово является устаревшим, и его значение не учитывается драйвером ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**WSID**|Идентификатор рабочей станции. Обычно это сетевое имя компьютера, на котором находится приложение (необязательно). Если указано, это значение хранится в **хост-имя** столбца **master.dbo.sysprocesses** и возвращается [sp_who](../../../relational-databases/system-stored-procedures/sp-who-transact-sql.md) и [функцией HOST_NAME.](../../../t-sql/functions/host-name-transact-sql.md)|  
  
> **ПРИМЕЧАНИЕ:** Региональные параметры конверсии применяются к типам данных валюты, числимы, даты и времени. Параметры преобразования применяются только при выходных преобразованиях и видны только тогда, когда значения валюты, цифровые данные и данные даты-времени преобразуются в строки символов.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует настройки локали текущего пользователя, установленные в реестре. Драйвер не выполняет приоритет ы, если приложение устанавливает его после подключения, например, вызывая **SetThreadLocale.**  
  
 Изменение режима работы источника данных с региональными параметрами может привести к ошибке приложения. Изменение этого значения может отрицательно повлиять на работу приложения, анализирующего строки даты и предполагающего, что строки даты будут выводиться в виде, определенном ODBC.  
  
## <a name="ole-db-provider-connection-string-keywords"></a>Ключевые слова строки подключения поставщика OLE DB  
 Приложения OLE DB могут инициализировать объекты источника данных двумя способами:  
  
-   **IDBInitialize::Initialize**  
  
-   **IDataInitialize::GetDataSource**  
  
 В первом случае строка поставщика может использоваться для инициализации свойств соединения посредством установки свойства DBPROP_INIT_PROVIDERSTRING в наборе свойств DBPROPSET_DBINIT. Во втором случае строка инициализации может быть передана методу **IDataInitialize::GetDataSource** для инициализации свойств соединения. При использовании каждого из этих методов инициализируются одни и те же свойства соединения OLE DB, однако, для этого применяются разные наборы ключевых слов. Набор ключевых слов, используемых методом **IDataInitialize::GetDataSource**, представляет собой по меньшей мере описание свойств, входящих в группу свойств инициализации.  
  
 Для любого параметра, указанного в строке поставщика, который имеет соответствующее свойство OLE DB, устанавливаемое в некоторое значение по умолчанию или явным образом установленное в некоторое значение, значение свойства OLE DB переопределяет значение, указанное в строке поставщика.  
  
 Логические свойства, установленные в строках поставщика через значения DBPROP_INIT_PROVIDERSTRING, устанавливаются с помощью значений «yes» и «no». Логические свойства, установленные в строках инициализации с помощью метода **IDataInitialize::GetDataSource**, устанавливаются с использованием значений true и false.  
  
 Приложения, использующие метод **IDataInitialize::GetDataSource**, также могут использовать ключевые слова, используемые методом **IDBInitialize::Initialize**, но только для свойств, у которых отсутствуют значения по умолчанию. Если приложение одновременно использует в строке инициализации ключевые слова методов **IDataInitialize::GetDataSource** и **IDBInitialize::Initialize**, используется ключевое слово метода **IDataInitialize::GetDataSource**. Настоятельно рекомендуется не использовать в приложениях ключевые слова **IDBInitialize::Initialize** в строках подключения **IDataInitialize:GetDataSource**, так как это поведение может не поддерживаться в будущих версиях.  
  
> [!NOTE]  
>  Строка подключения, передаваемая в метод **IDataInitialize::GetDataSource**, преобразуется в свойства, которые применяются методом **IDBProperties::SetProperties**. Если службы компонентов обнаруживают описание свойства в **IDBProperties::GetPropertyInfo**, это свойство будет применяться в качестве изолированного. В противном случае оно будет применяться через свойство DBPROP_PROVIDERSTRING. Например, если указать строку подключения **Data Source=server1;Server=server2**, ключевое слово **Data Source** будет задано в качестве свойства, но **Server** перейдет в строку поставщика.  
  
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
|**Адрес**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Для получения дополнительной информации о действительном **Address** синтаксисе адреса, см.|  
|**Приложение**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**ApplicationНамерение**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Для получения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более подробной информации о поддержке родного [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]клиента, см. [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)|  
|**AttachDBFileName**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Чтобы использовать ключевое слово **AttachDBFileName**, необходимо также указать имя базы данных с помощью ключевого слова Database в строке поставщика. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «yes» и «no».|  
|**База данных**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Шифрование**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**FailoverPartner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**FailoverPartnerSPN**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Язык**|SSPROP_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**MarsConn**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Допустимы значения «yes» и «no». Значение по умолчанию — «no».|  
|**Чистая**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**Сеть**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Синоним для «Network».|  
|**PacketSize**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**PersistSensitive**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «yes» и «no». Если используется значение «no», объекту источника данных запрещено хранить конфиденциальные данные проверки подлинности.|  
|**Pwd**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Server**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Для получения дополнительной информации о действительном **Server** синтаксисе адреса, см.|  
|**СерверSPN**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Времени ожидания**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Trusted_Connection**|DBPROP_AUTH_INTEGRATED|Значение «yes» предписывает поставщику OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использовать режим проверки подлинности Windows для проверки имени входа. В противном случае для проверки имени входа поставщик OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должен использовать имя пользователя и пароль [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также необходимо указать ключевые слова UID и PWD.|  
|**TrustServerCertificate**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «yes» и «no». По умолчанию имеет значение «no», которое указывает, что сертификат сервера будет проверяться.|  
|**ИД пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**UseProcForPrepare**|SSPROP_INIT_USEPROCFORPREP|Это ключевое слово является устаревшим, и его значение не обрабатывается поставщиком OLE DB собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**WSID**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 Строки подключения, используемые приложениями OLE DB, в которых используется **IDataInitialize::GetDataSource**, имеют следующий синтаксис.  
  
 `connection-string ::= empty-string[;] | attribute[;] | attribute; connection-string`  
  
 `empty-string ::=`  
  
 `attribute ::= attribute-keyword=[quote]attribute-value[quote]`  
  
 `attribute-value ::= character-string`  
  
 `attribute-keyword ::= identifier`  
  
 `quote ::= " | '`  
  
 Использование свойства должно соответствовать синтаксическим правилам, действующим в его области.  Например, в **WSID** вместо кавычек используются фигурные скобки (**{}**), а в **Application Name** используются апострофы (**'**) или двойные кавычки (**"**). Заключать в кавычки можно только строковые свойства. Заключение в кавычки целочисленного или перечисляемого свойства приведет к ошибке «Строка подключения не соответствует спецификации OLE DB».  
  
 Значения атрибутов можно при желании заключать в одинарные или двойные кавычки, а фактически это даже рекомендуется. Это позволяет избежать проблем, если значения содержат символы, отличные от буквенно-цифровых. Используемый символ кавычек может также появиться в значении при условии его удвоения.  
  
 Пробельный символ после знака равенства (=) в строке подключения будет считаться литералом, даже если значение заключено в кавычки.  
  
 Если строка подключения содержит несколько свойств из тех, которые приведены в следующей таблице, то будет использоваться значение последнего свойства.  
  
 В следующей таблице рассматриваются ключевые слова, которые можно использовать с **IDataInitialize::GetDataSource**.  
  
|Ключевое слово|Свойство инициализации|Описание|  
|-------------|-----------------------------|-----------------|  
|**Имя приложения**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Намерение приложения**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Для получения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более подробной информации о поддержке родного [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]клиента, см. [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Время ожидания соединения**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Текущий язык**|SSPROP_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Для получения дополнительной информации о действительном **Server** синтаксисе адреса, см.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Указывает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**Имя участника-службы партнера по обеспечению отработки отказа**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Для использования **AttachDBFileName**необходимо также указать имя базы данных с ключевым словом DATABASE. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Интегрированная безопасность**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения. Распознаются значения «true» и «false». Значение по умолчанию — «false».|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Для получения дополнительной информации о действительном **Address** синтаксисе адреса, см.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Размер пакета**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Сохранять сведения о безопасности**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо указывать значение «SQLNCLI11».|  
|**Имя участника-службы сервера**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Сертификат доверительного сервера**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**ИД пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Идентификатор рабочей станции**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
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
|**Намерение приложения**|SSPROP_INIT_APPLICATIONINTENT|Объявляет тип рабочей нагрузки приложения при соединении с сервером. Возможные значения **ReadOnly** и **ReadWrite**.<br /><br /> Значение по умолчанию — **ReadWrite**. Для получения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] более подробной информации о поддержке родного [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]клиента, см. [SQL Server Native Client Support for High Availability, Disaster Recovery](../../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)|  
|**Имя приложения**|SSPROP_INIT_APPNAME|Строка, идентифицирующая приложение.|  
|**Автоматическое преобразование**|SSPROP_INIT_AUTOTRANSLATE|Синоним для «AutoTranslate».|  
|**AutoTranslate**|SSPROP_INIT_AUTOTRANSLATE|Настраивает перевод символов OEM/ANSI. Распознаются значения «true» и «false».|  
|**Время ожидания соединения**|DBPROP_INIT_TIMEOUT|Время (в секундах), в течение которого ожидается завершение инициализации источника данных.|  
|**Текущий язык**|SSPROP_INIT_CURRENTLANGUAGE|Язык [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Источник данных**|DBPROP_INIT_DATASOURCE|Имя экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Если имя не задано, то производится соединение с экземпляром по умолчанию на локальном компьютере.<br /><br /> Для получения дополнительной информации о действительном **Server** синтаксисе адреса, см.|  
|**DataTypeCompatibility**|SSPROP_INIT_DATATYPECOMPATIBILITY|Задает используемый режим обработки типов данных. Распознаются значения «0» (для типов данных поставщика) и «80» (для типов данных SQL Server 2000).|  
|**Failover Partner**|SSPROP_INIT_FAILOVERPARTNER|Имя сервера отработки отказа, используемого для зеркального отображения базы данных.|  
|**Имя участника-службы партнера по обеспечению отработки отказа**|SSPROP_INIT_FAILOVERPARTNERSPN|Имя участника-службы для партнера по обеспечению отработки отказа. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Исходный каталог**|DBPROP_INIT_CATALOG|Имя базы данных.|  
|**Исходное имя файла**|SSPROP_INIT_FILENAME|Имя первичного файла присоединяемой базы данных (включает полный путь). Для использования **AttachDBFileName**необходимо также указать имя базы данных с ключевым словом DATABASE. Если база данных уже присоединена, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не присоединяет ее повторно, а использует для соединения присоединенную базу данных по умолчанию.|  
|**Интегрированная безопасность**|DBPROP_AUTH_INTEGRATED|Принимает значение «SSPI» для проверки подлинности Windows.|  
|**MARS Connection**|SSPROP_INIT_MARSCONNECTION|Включает или отключает режим MARS для соединения для сервера версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] или более поздней версии. Распознаются значения «true» и «false». По умолчанию используется значение «false».|  
|**Network Address**|SSPROP_INIT_NETWORKADDRESS|Сетевой адрес экземпляра [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.<br /><br /> Для получения дополнительной информации о действительном **Address** синтаксисе адреса, см.|  
|**Network Library**|SSPROP_INIT_NETWORKLIBRARY|Сетевая библиотека, используемая для установления соединения с экземпляром [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в организации.|  
|**Размер пакета**|SSPROP_INIT_PACKETSIZE|Размер сетевого пакета. Значение по умолчанию — 4096.|  
|**Пароль**|DBPROP_AUTH_PASSWORD|Пароль имени входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Сохранять сведения о безопасности**|DBPROP_AUTH_PERSIST_SENSITIVE_AUTHINFO|Принимает в качестве значений строки «true» и «false». Если указано значение «false», объекту источника данных не разрешается сохранять конфиденциальные сведения проверки подлинности.|  
|**Поставщик**||Для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] необходимо указывать значение «SQLNCLI11».|  
|**Имя участника-службы сервера**|SSPROP_INIT_SERVERSPN|Имя участника-службы для сервера. Значение по умолчанию — пустая строка. Если указана пустая строка, собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] использует имя участника-службы по умолчанию, сформированное поставщиком.|  
|**Сертификат доверительного сервера**|SSPROP_INIT_TRUST_SERVER_CERTIFICATE|Принимает в качестве значений строки «true» и «false». По умолчанию имеет значение «false», которое указывает, что сертификат сервера будет проверяться.|  
|**Use Encryption for Data**|SSPROP_INIT_ENCRYPT|Указывает, необходимо ли шифрование данных перед их отправкой по сети. Возможными значениями являются «true» и «false». Значение по умолчанию — «false».|  
|**ИД пользователя**|DBPROP_AUTH_USERID|Имя входа [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|**Идентификатор рабочей станции**|SSPROP_INIT_WSID|Идентификатор рабочей станции.|  
  
 **Примечание**. В строке подключения свойство Old Password устанавливает значение свойства SSPROP_AUTH_OLD_PASSWORD, которое является текущим паролем (возможно, с истекшим сроком действия), недоступным через свойство строки поставщика.  
  
## <a name="see-also"></a>См. также  
 [Построение приложений с использованием собственного клиента SQL Server](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
