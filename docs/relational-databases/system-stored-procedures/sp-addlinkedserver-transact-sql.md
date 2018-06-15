---
title: sp_addlinkedserver (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addlinkedserver_TSQL
- sp_addlinkedserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedserver
ms.assetid: fed3adb0-4c15-4a1a-8acd-1b184aff558f
caps.latest.revision: 70
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 54fc43ecec6c26435165c9c3491bfba2f1f675ea
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33240534"
---
# <a name="spaddlinkedserver-transact-sql"></a>sp_addlinkedserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает связанный сервер. Связанные серверы позволяют выполнять распределенные разнородные запросы к источникам данных OLE DB. После создания связанного сервера с помощью **sp_addlinkedserver**распределенные запросы могут выполняться на этом сервере. Если связанный сервер определен в качестве экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на нем могут выполняться удаленные хранимые процедуры.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addlinkedserver [ @server= ] 'server' [ , [ @srvproduct= ] 'product_name' ]   
     [ , [ @provider= ] 'provider_name' ]  
     [ , [ @datasrc= ] 'data_source' ]   
     [ , [ @location= ] 'location' ]   
     [ , [ @provstr= ] 'provider_string' ]   
     [ , [ @catalog= ] 'catalog' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@server=** ] **'***server***'**  
 Имя создаваемого связанного сервера. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 [  **@srvproduct=** ] **"***product_name***"**  
 Введите название продукта для источника данных OLE DB, который добавляется в качестве связанного сервера. *product_name* — **nvarchar (** 128 **)**, значение по умолчанию NULL. Если **SQL Server**, *provider_name*, *источник_данных*, *расположение*, *provider_string*, и *каталога* не должны быть указаны.  
  
 [  **@provider=** ] **"***provider_name***"**  
 Введите уникальный программный идентификатор (PROGID) поставщика OLE DB, соответствующий этому источнику данных. *provider_name* должно быть уникальным для указанного поставщика OLE DB, который установлен на данном компьютере. *provider_name* — **nvarchar (** 128 **)**, значение по умолчанию NULL; тем не менее, если *provider_name* — этот параметр опущен, используется значение SQLNCLI. (При использовании SQLNCLI [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет использовать последнюю версию поставщика OLE DB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].) Предполагается, что поставщик OLE DB будет зарегистрирован в реестре с указанным идентификатором PROGID.  
  
 [  **@datasrc=** ] **"***источник_данных***"**  
 Имя источника данных, как оно интерпретируется поставщиком OLE DB. *источник_данных* — **nvarchar (** 4000 **)**. *источник_данных* передается как свойство DBPROP_INIT_DATASOURCE для инициализации поставщика OLE DB.  
  
 [  **@location=** ] **"***расположение***"**  
 Введите местонахождение базы данных, понятное поставщику OLE DB. *расположение* — **nvarchar (** 4000 **)**, значение по умолчанию NULL. *расположение* передается как свойство DBPROP_INIT_LOCATION для инициализации поставщика OLE DB.  
  
 [  **@provstr=** ] **"***provider_string***"**  
 Строка подключения для конкретного поставщика OLE DB, указывающая уникальный источник данных. *provider_string* — **nvarchar (** 4000 **)**, значение по умолчанию NULL. *provstr* передаваемый IDataInitialize или задается как свойство DBPROP_INIT_PROVIDERSTRING для инициализации поставщика OLE DB.  
  
 При создании связанного сервера для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента экземпляра можно указать с помощью ключевого слова SERVER как сервер =*servername*\\*instancename*для указания определенного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *ServerName* — имя компьютера, на котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает, и *instancename* имя конкретного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которой будет подключен пользователь.  
  
> [!NOTE]  
>  Чтобы получить доступ к зеркальной базе данных, строка соединения должна содержать имя базы данных. Это имя необходимо, чтобы предоставить поставщику доступа к данным возможность пытаться отработать отказ. Базы данных могут быть указаны в **@provstr** или **@catalog** параметра. Кроме того, строка соединения может содержать имя партнера по обеспечению отработки отказа.  
  
 [  **@catalog=** ] **"***каталога***"**  
 Каталог, который должен использоваться при подключении к поставщику OLE DB. *каталог* — **sysname**, значение по умолчанию NULL. *каталог* передается как свойство DBPROP_INIT_CATALOG для инициализации поставщика OLE DB. Если связанный сервер определен для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то каталог ссылается на базу данных по умолчанию, с которой сопоставлен связанный сервер.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице показаны способы настройки связанного сервера для источников данных, доступных через поставщик OLE DB. Связанный сервер может быть настроен несколькими способами для конкретного источника данных; для одного типа источника данных возможны несколько строк. В этой таблице также показаны **sp_addlinkedserver** значения параметров, используемые для настройки связанного сервера.  
  
|Удаленный источник данных OLE DB|Поставщик OLE DB|product_name|provider_name|data_source|location|provider_string|catalog|  
|-------------------------------|---------------------|-------------------|--------------------|------------------|--------------|----------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <sup>1</sup> (по умолчанию)||||||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента||**SQLNCLI**|Сетевое имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (для экземпляра по умолчанию)|||Имя базы данных (необязательно)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB для собственного клиента||**SQLNCLI**|*ServerName*\\*instancename* (для конкретного экземпляра)|||Имя базы данных (необязательно)|  
|Oracle, версия 8 или более поздняя|Поставщик Oracle для OLE DB|Любой|**(Oraoledb.Oracle)**|Псевдоним для базы данных Oracle||||  
|Access/Jet|Поставщик OLE DB для Jet (Майкрософт)|Любой|**Microsoft.Jet.OLEDB.4.0**|Полный путь к файлу базы данных Jet||||  
|Источник данных ODBC|Поставщик Microsoft OLE DB для ODBC|Любой|**MSDASQL**|Системный DSN источника данных ODBC||||  
|Источник данных ODBC|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для ODBC|Любой|**MSDASQL**|||Строка подключения ODBC||  
|Файловая система|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для службы индексирования|Любой|**MSIDXS**|Имя каталога службы индексирования||||  
|Электронная таблица [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet|Любой|**Microsoft.Jet.OLEDB.4.0**|Полный путь к файлу Excel||Excel 5.0||  
|База данных IBM DB2|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для DB2|Любой|**DB2OLEDB**|||В разделе [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщик OLE DB для документации DB2.|Имя каталога базы данных DB2|  
  
 <sup>1</sup> этом способе настройки связанного сервера заставляет имя связанного сервера должен совпадать с сетевое имя удаленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте *источник_данных* для указания этого сервера.  
  
 <sup>2</sup> «Любой» указывает, что имя продукта может быть любым.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщика OLE DB для собственного клиента — это поставщик, используемый с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если имя поставщика не указано или если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указывается как имя продукта. Даже если указано имя предыдущего поставщика (SQLOLEDB), оно все равно будет изменено на SQLNCLI при сохранении в каталог.  
  
 *Источник_данных*, *расположение*, *provider_string*, и *каталога* параметры идентификации базы данных, связанные Указывает сервер. Если значение одного из этих аргументов равно NULL, то соответствующее свойство инициализации поставщика OLE DB не установлено.  
  
 В кластеризованной среде при указании имен файлов для указания источников данных OLE DB используйте формат UNC или общие диски для указания расположения.  
  
 **sp_addlinkedserver** не может выполняться внутри пользовательской транзакции.  
  
> [!IMPORTANT]  
>  При создании связанного сервера с помощью **sp_addlinkedserver**, для всех локальных имен входа добавляется Самосопоставление по умолчанию. Поставщики, отличные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], для которых выполнена проверка подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], могут получить доступ к поставщику под учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Администраторам нужно рассмотреть применение процедуры `sp_droplinkedsrvlogin <linkedserver_name>, NULL` для удаления глобального сопоставления.  
  
## <a name="permissions"></a>Разрешения  
 `sp_addlinkedserver` Оператора требуется `ALTER ANY LINKED SERVER` разрешение. (SSMS **создать связанный сервер** диалоговое окно реализуется в виде, необходимо быть членом `sysadmin` предопределенной роли сервера.)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-microsoft-sql-server-native-client-ole-db-provider"></a>A. Использование поставщика OLE DB для собственного клиента Microsoft SQL Server  
 В следующем примере показано создание связанного сервера с именем `SEATTLESales`. Название продукта — `SQL Server`, имя поставщика не используется.  
  
```  
USE master;  
GO  
EXEC sp_addlinkedserver   
   N'SEATTLESales',  
   N'SQL Server';  
GO  
```  
  
 В следующем примере создается связанный сервер `S1_instance1` экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB для собственного клиента.  
  
```  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'SQLNCLI',   
   @datasrc=N'S1\instance1';  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-microsoft-access"></a>Б. Использование поставщика Microsoft OLE DB для Microsoft Access  
 Поставщик Microsoft.Jet.OLEDB.4.0 соединяется с базами данных Microsoft Access в формате 2002–2003. В следующем примере показано создание связанного сервера с именем `SEATTLE Mktg`.  
  
> [!NOTE]  
>  В этом примере предполагается, что оба [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access и образец **Northwind** установлены базы данных и что **Northwind** база данных находится в C:\Msoffice\Access\Samples.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.Jet.OLEDB.4.0',   
   @srvproduct = N'OLE DB Provider for Jet',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.mdb';  
GO  
```  
  
 Поставщик Microsoft.ACE.OLEDB.12.0 соединяется с базами данных Microsoft Access в формате 2007. В следующем примере показано создание связанного сервера с именем `SEATTLE Mktg`.  
  
> [!NOTE]  
>  В этом примере предполагается, что оба [!INCLUDE[msCoName](../../includes/msconame-md.md)] Access и образец **Northwind** установлены базы данных и что **Northwind** база данных находится в C:\Msoffice\Access\Samples.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.ACE.OLEDB.12.0',   
   @srvproduct = N'OLE DB Provider for ACE',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.accdb';  
GO  
```  
  
### <a name="c-using-the-microsoft-ole-db-provider-for-odbc-with-the-datasource-parameter"></a>В. Использование поставщика Microsoft OLE DB для ODBC с аргументом источника данных  
 В следующем примере создается связанный сервер с именем `SEATTLE Payroll` , использующий [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщик OLE DB для ODBC (`MSDASQL`) и *источник_данных* параметра.  
  
> [!NOTE]  
>  Указанный источник данных ODBC должен быть определен как системный DSN на сервере до того, как будет использоваться связанный сервер.  
  
```  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Payroll',   
   @srvproduct = N'',  
   @provider = N'MSDASQL',   
   @datasrc = N'LocalServer';  
GO  
```  
  
### <a name="d-using-the-microsoft-ole-db-provider-for-excel-spreadsheet"></a>Г. Использование поставщика Microsoft OLE DB для электронных таблиц Excel  
 Для создания определения связанного сервера с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщик OLE DB для Jet для доступа к электронным таблицам Excel в формате 1997-2003, сначала необходимо создать именованный диапазон в Excel путем указания столбцов и строк на листе Excel для выбора. Затем на имя диапазона можно будет ссылаться в распределенном запросе как на имя таблицы.  
  
```  
EXEC sp_addlinkedserver 'ExcelSource',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   'c:\MyData\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
GO  
```  
  
 Для доступа к данным в электронной таблице Excel требуется указать имя для диапазона ячеек. Следующий запрос используется для получения доступа к указанному диапазону ячеек `SalesData` как к таблице с помощью предварительно настроенного связанного сервера.  
  
```  
SELECT *  
   FROM ExcelSource...SalesData;  
GO  
```  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется под учетной записью домена, имеющего доступ к удаленной общей папке, то вместо сопоставленного диска может использоваться путь в формате UNC.  
  
```  
EXEC sp_addlinkedserver 'ExcelShare',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   '\\MyServer\MyShare\Spreadsheets\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
```  
  
 Чтобы подключиться к электронной таблице Excel в формате Excel 2007, используйте поставщик ACE.  
  
```  
EXEC sp_addlinkedserver @server = N'ExcelDataSource',   
@srvproduct=N'ExcelData', @provider=N'Microsoft.ACE.OLEDB.12.0',   
@datasrc=N'C:\DataFolder\People.xlsx',  
@provstr=N'EXCEL 12.0' ;  
  
```  
  
### <a name="e-using-the-microsoft-ole-db-provider-for-jet-to-access-a-text-file"></a>Д. Использование поставщика Microsoft OLE DB для Jet для доступа к текстовым файлам  
 Данный пример показывает, как создать связанный сервер для прямого доступа к текстовым файлам без соединения с ними как с таблицами MDB-файла СУБД Access. Поставщик `Microsoft.Jet.OLEDB.4.0` и строка поставщика `Text`.  
  
 Источник данных — это полный путь к каталогу, который содержит тестовые файлы. Файл schema.ini, который описывает структуру текстовых файлов, должен находиться в том же каталоге, что и текстовые файлы. Дополнительные сведения о том, как создать файл Schema.ini, см. в документации по ядру СУБД Jet.  
  
```  
--Create a linked server.  
EXEC sp_addlinkedserver txtsrv, N'Jet 4.0',   
   N'Microsoft.Jet.OLEDB.4.0',  
   N'c:\data\distqry',  
   NULL,  
   N'Text';  
GO  
  
--Set up login mappings.  
EXEC sp_addlinkedsrvlogin txtsrv, FALSE, Admin, NULL;  
GO  
  
--List the tables in the linked server.  
EXEC sp_tables_ex txtsrv;  
GO  
  
--Query one of the tables: file1#txt  
--using a four-part name.   
SELECT *   
FROM txtsrv...[file1#txt];  
```  
  
### <a name="f-using-the-microsoft-ole-db-provider-for-db2"></a>Е. Использование поставщика данных Microsoft OLE DB для DB2  
 В следующем примере показано создание связанного сервера с именем `DB2`, который использует `Microsoft OLE DB Provider for DB2`.  
  
```  
EXEC sp_addlinkedserver  
   @server=N'DB2',  
   @srvproduct=N'Microsoft OLE DB Provider for DB2',  
   @catalog=N'DB2',  
   @provider=N'DB2OLEDB',  
   @provstr=N'Initial Catalog=PUBS;  
       Data Source=DB2;  
       HostCCSID=1252;  
       Network Address=XYZ;  
       Network Port=50000;  
       Package Collection=admin;  
       Default Schema=admin;';  
```  
  
### <a name="g-add-a-includesssdsfullincludessssdsfull-mdmd-as-a-linked-server-for-use-with-distributed-queries-on-cloud-and-on-premise-databases"></a>Ж. Добавить [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] как связанный сервер для использования с распределенными запросами на облачных и локальных баз данных  
 Можно добавить [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] как связанный сервер и затем с помощью распределенные запросы, которые в локальной и облачной базы данных. Это компонент для базы данных гибридные решения охват корпоративной сети в локальной среде и облаке Windows Azure.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Продукт поле содержит компонентом распределенного запроса, который позволяет составлять запросы, чтобы объединить данные из локальных источников данных и данные из удаленных источников (включая данные, отличными от[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источники данных) определенным как связанные серверы. Каждый [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (кроме master виртуальный) можно добавить в качестве отдельного связанного сервера и затем непосредственно использовать в приложениях базы данных как и любые другие базы данных.  
  
 Преимущества использования [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] включают управляемость, высокий уровень доступности, масштабируемость, знакомую модель разработки и реляционную модель данных. Определить требования приложения базы данных, как его использовать [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] в облаке. Перемещение всех данных за один раз в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], или постепенно переместить некоторые данные, сохранив оставшихся данных локальной. Для таких гибридное приложение базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] возможность добавления как связанные серверы и базы данных приложения может выдавать распределенные запросы для объединения данных из [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] и локальными источниками данных.  
  
 Ниже приведен простой пример, объясняющий, как подключиться к [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] использования распределенных запросов:  
  
```  
------ Configure the linked server  
-- Add one Windows Azure SQL DB as Linked Server  
EXEC sp_addlinkedserver  
@server='myLinkedServer', -- here you can specify the name of the linked server  
@srvproduct='',       
@provider='sqlncli', -- using SQL Server Native Client  
@datasrc='myServer.database.windows.net',   -- add here your server name  
@location='',  
@provstr='',  
@catalog='myDatabase'  -- add here your database name as initial catalog (you cannot connect to the master database)  
-- Add credentials and options to this linked server  
EXEC sp_addlinkedsrvlogin  
@rmtsrvname = 'myLinkedServer',  
@useself = 'false',  
@rmtuser = 'myLogin',             -- add here your login on Azure DB  
@rmtpassword = 'myPassword' -- add here your password on Azure DB  
EXEC sp_serveroption 'myLinkedServer', 'rpc out', true;  
------ Now you can use the linked server to execute 4-part queries  
-- You can create a new table in the Azure DB  
exec ('CREATE TABLE t1tutut2(col1 int not null CONSTRAINT PK_col1 PRIMARY KEY CLUSTERED (col1) )') at myLinkedServer  
-- Insert data from your local SQL Server  
exec ('INSERT INTO t1tutut2 VALUES(1),(2),(3)') at myLinkedServer  
  
-- Query the data using 4-part names  
select * from myLinkedServer.myDatabase.dbo.myTable  
```  
  
## <a name="see-also"></a>См. также  
 [Распределенные запросы хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [sp_setnetname &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
