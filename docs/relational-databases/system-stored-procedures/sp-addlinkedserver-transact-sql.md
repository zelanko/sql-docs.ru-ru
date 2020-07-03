---
title: sp_addlinkedserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addlinkedserver_TSQL
- sp_addlinkedserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addlinkedserver
ms.assetid: fed3adb0-4c15-4a1a-8acd-1b184aff558f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fce303bf12158014dd2dfc28da19b900f2cd46f3
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85877812"
---
# <a name="sp_addlinkedserver-transact-sql"></a>sp_addlinkedserver (Transact-SQL)
[!INCLUDE [SQL Server - ASDBMI](../../includes/applies-to-version/sql-asdbmi.md)]

  Создает связанный сервер. Связанные серверы позволяют выполнять распределенные разнородные запросы к источникам данных OLE DB. После создания связанного сервера с помощью **sp_addlinkedserver**можно выполнить распределенные запросы к этому серверу. Если связанный сервер определен в качестве экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на нем могут выполняться удаленные хранимые процедуры.  
  
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
[ @server =] * \' сервер \' *          
Имя создаваемого связанного сервера. Аргумент*server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
[ @srvproduct =] * \' product_name \' *          
Введите название продукта для источника данных OLE DB, который добавляется в качестве связанного сервера. *product_name* имеет тип **nvarchar (** 128 **)** и значение по умолчанию NULL. Если **SQL Server**, *provider_name*, *data_source*, *Расположение*, *provider_string*и *Каталог* не должны быть указаны.  
  
[ @provider =] * \' provider_name \' *          
Введите уникальный программный идентификатор (PROGID) поставщика OLE DB, соответствующий этому источнику данных. *provider_name* должны быть уникальными для указанного поставщика OLE DB, установленного на текущем компьютере. *provider_name* имеет тип **nvarchar (128)** и значение по умолчанию NULL. Однако если *provider_name* опущен, используется sqlncli. 

> [!NOTE]
> При использовании SQLNCLI будет выполнено перенаправление [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к последней версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB собственного клиента. Предполагается, что поставщик OLE DB будет зарегистрирован в реестре с указанным идентификатором PROGID.

> [!IMPORTANT] 
> Предыдущие поставщики Microsoft OLE DB для SQL Server (SQLOLEDB) и собственный клиент OLE DB для SQL Server (SQLNCLI) объявляются нерекомендуемыми для новых разработок. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.
  
[ @datasrc =] * \' data_source \' *          
 Имя источника данных, как оно интерпретируется поставщиком OLE DB. *data_source* имеет тип **nvarchar (** 4000 **)**. *data_source* передается как свойство DBPROP_INIT_DATASOURCE для инициализации поставщика OLE DB.  
  
[ @location =] * \' расположение \' *          
 Введите местонахождение базы данных, понятное поставщику OLE DB. *Location* имеет тип **nvarchar (** 4000 **)** и значение по умолчанию NULL. *Расположение* передается как свойство DBPROP_INIT_LOCATION для инициализации поставщика OLE DB.  
  
[ @provstr =] * \' provider_string \' *          
 Строка подключения для конкретного поставщика OLE DB, указывающая уникальный источник данных. *provider_string* имеет тип **nvarchar (** 4000 **)** и значение по умолчанию NULL. *provstr* передается в IDataInitialize или устанавливается как свойство DBPROP_INIT_PROVIDERSTRING для инициализации поставщика OLE DB.  
  
 При создании связанного сервера для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLE DB собственного клиента экземпляр можно указать с помощью ключевого слова Server Server =*ServerName* \\ *имя_экземпляра* , чтобы указать конкретный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . *ServerName* — это имя компьютера, на котором [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется, а *instanceName* — имя конкретного экземпляра, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] к которому будет подключен пользователь.  
  
> [!NOTE]
> Чтобы получить доступ к зеркальной базе данных, строка соединения должна содержать имя базы данных. Это имя необходимо, чтобы предоставить поставщику доступа к данным возможность пытаться отработать отказ. База данных может быть указана в параметре ** \@ provstr** или ** \@ Catalog** . Кроме того, строка соединения может содержать имя партнера по обеспечению отработки отказа.  
  
[ @catalog =] * \' каталог \' *       
 Каталог, который должен использоваться при подключении к поставщику OLE DB. *Catalog* имеет тип **sysname**и значение по умолчанию NULL. *Каталог* передается как свойство DBPROP_INIT_CATALOG для инициализации поставщика OLE DB. Если связанный сервер определен для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то каталог ссылается на базу данных по умолчанию, с которой сопоставлен связанный сервер.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Комментарии  
 В следующей таблице показаны способы настройки связанного сервера для источников данных, доступных через поставщик OLE DB. Связанный сервер может быть настроен несколькими способами для конкретного источника данных; для одного типа источника данных возможны несколько строк. В этой таблице также показаны значения параметров **sp_addlinkedserver** , которые будут использоваться для настройки связанного сервера.  
  
|Удаленный источник данных OLE DB|Поставщик OLE DB|product_name|provider_name|data_source|location|provider_string|catalog|  
|-------------------------------|---------------------|-------------------|--------------------|------------------|--------------|----------------------|-------------|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <sup>1</sup> (по умолчанию)||||||  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB||**SQLNCLI**|Сетевое имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (для экземпляра по умолчанию)|||Имя базы данных (необязательно)|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поставщик собственного клиента OLE DB||**SQLNCLI**|*имя сервера* \\ *instanceName* (для конкретного экземпляра)|||Имя базы данных (необязательно)|  
|Oracle, версия 8 или более поздняя|Поставщик Oracle для OLE DB|Любой|**OraOLEDB.Oracle**|Псевдоним для базы данных Oracle||||  
|Access/Jet|Поставщик OLE DB для Jet (Майкрософт)|Любой|**Microsoft.Jet.OLEDB.4.0**|Полный путь к файлу базы данных Jet||||  
|Источник данных ODBC|Поставщик Microsoft OLE DB для ODBC|Любой|**MSDASQL**|Системный DSN источника данных ODBC||||  
|Источник данных ODBC|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для ODBC|Любой|**MSDASQL**|||Строка подключения ODBC||  
|Файловая система|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для службы индексирования|Любой|**MSIDXS**|Имя каталога службы индексирования||||  
|Электронная таблица [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для Jet|Любой|**Microsoft.Jet.OLEDB.4.0**|Полный путь к файлу Excel||Excel 5,0||  
|База данных IBM DB2|Поставщик [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для DB2|Любой|**DB2OLEDB**|||См [!INCLUDE[msCoName](../../includes/msconame-md.md)] . документацию по поставщику OLE DB для DB2.|Имя каталога базы данных DB2|  
  
 <sup>1</sup> такой способ настройки связанного сервера приводит к тому, что имя связанного сервера будет совпадать с сетевым именем удаленного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Укажите сервер с помощью *data_source* .  
  
 <sup>2</sup> "Any" означает, что название продукта может быть любым.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Поставщик OLE DB собственного клиента — это поставщик, который используется с, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Если имя поставщика не указано или указано в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] качестве имени продукта. Даже если указано имя предыдущего поставщика (SQLOLEDB), оно все равно будет изменено на SQLNCLI при сохранении в каталог.  
  
 Параметры *data_source*, *Location*, *provider_string*и *Catalog* указывают на базу данных или базы данных, на которые указывает связанный сервер. Если значение одного из этих аргументов равно NULL, то соответствующее свойство инициализации поставщика OLE DB не установлено.  
  
 В кластеризованной среде при указании имен файлов для указания источников данных OLE DB используйте формат UNC или общие диски для указания расположения.  
  
 **sp_addlinkedserver** не может быть выполнена в пользовательской транзакции.  
  
> [!IMPORTANT]
> При создании связанного сервера с помощью **sp_addlinkedserver**для всех локальных имен входа добавляется автоматическое сопоставление по умолчанию. Для пользователей, не являющихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщиками, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверенные имена входа могут иметь возможность получить доступ к поставщику в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы. Администраторам нужно рассмотреть применение процедуры `sp_droplinkedsrvlogin <linkedserver_name>, NULL` для удаления глобального сопоставления.  
  
## <a name="permissions"></a>Разрешения  
 `sp_addlinkedserver`Инструкции требуется `ALTER ANY LINKED SERVER` разрешение. (Элемент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Диалоговое окно **Создание связанного сервера** реализуется таким образом, что требует членства в `sysadmin` предопределенной роли сервера.)  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-microsoft-sql-server-ole-db-provider"></a>A. Использование поставщика Microsoft SQL Server OLE DB  
 В следующем примере показано создание связанного сервера с именем `SEATTLESales`. Название продукта — `SQL Server`, имя поставщика не используется.  
  
```sql  
USE master;  
GO  
EXEC sp_addlinkedserver   
   N'SEATTLESales',  
   N'SQL Server';  
GO  
```  

 В следующем примере создается связанный сервер `S1_instance1` на экземпляре с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвера OLE DB.  

```sql  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'MSOLEDBSQL',   
   @datasrc=N'S1\instance1';  
```  

 В следующем примере создается связанный сервер `S1_instance1` на экземпляре с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] помощью [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB Provider.  
 
> [!IMPORTANT] 
> Собственный клиент OLE DB для SQL Server (SQLNCLI) объявляется нерекомендуемым для новых разработок. Вместо этого используйте новый драйвер [Microsoft OLE DB для SQL Server](../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL), который будет обновлен с самыми последними серверными компонентами.
  
```sql  
EXEC sp_addlinkedserver     
   @server=N'S1_instance1',   
   @srvproduct=N'',  
   @provider=N'SQLNCLI',   
   @datasrc=N'S1\instance1';  
```  
  
### <a name="b-using-the-microsoft-ole-db-provider-for-microsoft-access"></a>Б. Использование поставщика Microsoft OLE DB для Microsoft Access  
 Поставщик Microsoft.Jet.OLEDB.4.0 соединяется с базами данных Microsoft Access в формате 2002–2003. В следующем примере показано создание связанного сервера с именем `SEATTLE Mktg`.  
  
> [!NOTE]  
> В этом примере предполагается, что [!INCLUDE[msCoName](../../includes/msconame-md.md)] установлен и доступ, и образец базы данных **Northwind** , а база данных **Northwind** находится в к:\мсоффице\акцесс\самплес.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.Jet.OLEDB.4.0',   
   @srvproduct = N'OLE DB Provider for Jet',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.mdb';  
GO  
```  
  
 Поставщик Microsoft.ACE.OLEDB.12.0 соединяется с базами данных Microsoft Access в формате 2007. В следующем примере показано создание связанного сервера с именем `SEATTLE Mktg`.  
  
> [!NOTE]  
> В этом примере предполагается, что [!INCLUDE[msCoName](../../includes/msconame-md.md)] установлен и доступ, и образец базы данных **Northwind** , а база данных **Northwind** находится в к:\мсоффице\акцесс\самплес.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Mktg',   
   @provider = N'Microsoft.ACE.OLEDB.12.0',   
   @srvproduct = N'OLE DB Provider for ACE',  
   @datasrc = N'C:\MSOffice\Access\Samples\Northwind.accdb';  
GO  
```  
  
### <a name="c-using-the-microsoft-ole-db-provider-for-odbc-with-the-data_source-parameter"></a>В. Использование поставщика Microsoft OLE DB для ODBC с аргументом источника данных  
 В следующем примере создается связанный сервер с именем `SEATTLE Payroll` , который использует [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщик OLE DB для ODBC ( `MSDASQL` ) и параметр *data_source* .  
  
> [!NOTE]  
> Указанный источник данных ODBC должен быть определен как системный DSN на сервере до того, как будет использоваться связанный сервер.  
  
```sql  
EXEC sp_addlinkedserver   
   @server = N'SEATTLE Payroll',   
   @srvproduct = N'',  
   @provider = N'MSDASQL',   
   @datasrc = N'LocalServer';  
GO  
```  
  
### <a name="d-using-the-microsoft-ole-db-provider-for-excel-spreadsheet"></a>Г. Использование поставщика Microsoft OLE DB для электронных таблиц Excel  
 Чтобы создать определение связанного сервера с помощью [!INCLUDE[msCoName](../../includes/msconame-md.md)] поставщика OLE DB для Jet для доступа к электронной таблице Excel в формате 1997-2003, сначала создайте именованный диапазон в Excel, указав столбцы и строки листа Excel для выбора. Затем на имя диапазона можно будет ссылаться в распределенном запросе как на имя таблицы.  
  
```sql  
EXEC sp_addlinkedserver 'ExcelSource',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   'c:\MyData\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
GO  
```  
  
 Для доступа к данным в электронной таблице Excel требуется указать имя для диапазона ячеек. Следующий запрос используется для получения доступа к указанному диапазону ячеек `SalesData` как к таблице с помощью предварительно настроенного связанного сервера.  
  
```sql  
SELECT *  
   FROM ExcelSource...SalesData;  
GO  
```  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняется под учетной записью домена, имеющего доступ к удаленной общей папке, то вместо сопоставленного диска может использоваться путь в формате UNC.  
  
```sql  
EXEC sp_addlinkedserver 'ExcelShare',  
   'Jet 4.0',  
   'Microsoft.Jet.OLEDB.4.0',  
   '\\MyServer\MyShare\Spreadsheets\DistExcl.xls',  
   NULL,  
   'Excel 5.0';  
```  
  
 Чтобы подключиться к электронной таблице Excel в формате Excel 2007, используйте поставщик ACE.  
  
```sql  
EXEC sp_addlinkedserver @server = N'ExcelDataSource',   
@srvproduct=N'ExcelData', @provider=N'Microsoft.ACE.OLEDB.12.0',   
@datasrc=N'C:\DataFolder\People.xlsx',  
@provstr=N'EXCEL 12.0' ;  
  
```  
  
### <a name="e-using-the-microsoft-ole-db-provider-for-jet-to-access-a-text-file"></a>Д. Использование поставщика Microsoft OLE DB для Jet для доступа к текстовым файлам  
 Данный пример показывает, как создать связанный сервер для прямого доступа к текстовым файлам без соединения с ними как с таблицами MDB-файла СУБД Access. Поставщик `Microsoft.Jet.OLEDB.4.0` и строка поставщика `Text`.  
  
 Источник данных — это полный путь к каталогу, который содержит тестовые файлы. Файл schema.ini, который описывает структуру текстовых файлов, должен находиться в том же каталоге, что и текстовые файлы. Дополнительные сведения о том, как создать файл Schema.ini, см. в документации по ядру СУБД Jet.  
  
```sql  
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
  
```sql  
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
  
### <a name="g-add-a-sssdsfull-as-a-linked-server-for-use-with-distributed-queries-on-cloud-and-on-premises-databases"></a>Ж. Добавление в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] качестве связанного сервера для использования с распределенными запросами в облачных и локальных базах данных  
 Можно добавить в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] качестве связанного сервера, а затем использовать его с распределенными запросами, охватывающими локальные и облачные базы данных. Это компонент для гибридных решений баз данных, охватывающих локальные корпоративные сети и облако Azure.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Поле Product содержит функцию распределенных запросов, которая позволяет создавать запросы для объединения данных из локальных источников данных и данных из удаленных источников (включая данные из источников, не являющихся [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] источниками данных), определенных в качестве связанных серверов. Каждый [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] (за исключением виртуального экземпляра) может быть добавлен в качестве отдельного связанного сервера и затем использоваться непосредственно в приложениях базы данных в качестве любой другой базы данных.  
  
 Преимущества использования [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] включают управляемость, высокий уровень доступности, масштабируемость, работу с привычной моделью разработки и реляционную модель данных. Требования приложения базы данных определяют, как она будет использоваться [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] в облаке. Вы можете переместить все данные одновременно в [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] или последовательно перемещать некоторые данные, сохраняя оставшиеся данные в локальной среде. Для такого гибридного приложения базы данных [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] теперь можно добавить в качестве связанных серверов, а приложение базы данных может выдавать распределенные запросы для объединения данных из [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] локальных источников данных.  
  
 Ниже приведен простой пример, в котором объясняется, как подключиться к с [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] помощью распределенных запросов.  
  
```sql  
-- Configure the linked server  
-- Add one Azure SQL DB as Linked Server  
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

-- Now you can use the linked server to execute 4-part queries  
-- You can create a new table in the Azure DB  
EXEC ('CREATE TABLE t1tutut2(col1 int not null CONSTRAINT PK_col1 PRIMARY KEY CLUSTERED (col1) )') at myLinkedServer  
-- Insert data from your local SQL Server  
EXEC ('INSERT INTO t1tutut2 VALUES(1),(2),(3)') at myLinkedServer  
  
-- Query the data using 4-part names  
SELECT * FROM myLinkedServer.myDatabase.dbo.myTable  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры распределенных запросов &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [sp_setnetname &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-setnetname-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Системные таблицы (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
