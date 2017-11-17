---
title: "SERVERPROPERTY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SERVERPROPERTY_TSQL
- SERVERPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- SERVERPROPERTY function
- server instance property information [SQL Server]
- IsHadrEnabled server property
- instances of SQL Server, property information
- server properties [SQL Server]
ms.assetid: 11e166fa-3dd2-42d8-ac4b-04f18c612c4a
caps.latest.revision: 128
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7060a8aaf668a69184503fa0995dd4f37085d5f1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="serverproperty-transact-sql"></a>SERVERPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о свойстве экземпляра сервера.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
SERVERPROPERTY ( 'propertyname' )  
```  
  
## <a name="arguments"></a>Аргументы  
 *PropertyName*  
 Выражение, содержащее сведения о свойстве, которые необходимо вернуть для сервера. *PropertyName* может принимать одно из следующих значений.  
  
|Свойство|Возвращаемые значения|  
|--------------|---------------------|  
|BuildClrVersion|Версия [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] общеязыковая среда выполнения (CLR), была использована при построении экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|Параметры сортировки|Имя параметров сортировки для сервера, установленного по умолчанию.<br /><br /> NULL = недопустимый ввод или произошла ошибка.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|CollationID|Идентификатор параметров сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Базовый тип данных: **int**|  
|ComparisonStyle|Стиль сравнения Windows для параметров сортировки.<br /><br /> Базовый тип данных: **int**|  
|ComputerNamePhysicalNetBIOS|Имя NetBIOS для локального компьютера, на котором работает экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Для кластеризованного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на отказоустойчивом кластере это значение изменяется, когда экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] переключается на другие узлы в отказоустойчивом кластере.<br /><br /> Для изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] это значение остается постоянным и совпадает со значением, возвращаемым свойством MachineName.<br /><br /> **Примечание:** Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] находится в отказоустойчивом кластере и необходимо получить имя экземпляра отказоустойчивого кластера, воспользуйтесь свойством MachineName.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|Выпуск|Установленный выпуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте значение этого свойства для определения возможностей и ограничений, таких как [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md). В 64-разрядных версиях компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] к обозначению версии добавляется «(64-разрядная версия)».<br /><br /> Возвращает:<br /><br /> выпуск «Enterprise Edition»;<br /><br /> "Enterprise Edition: лицензирование по числу ядер"<br /><br /> выпуск «Enterprise Evaluation Edition»;<br /><br /> выпуск «Business Intelligence»;<br /><br /> выпуск «Developer Edition»;<br /><br /> выпуск «Express Edition»;<br /><br /> экспресс-выпуск с дополнительными службами;<br /><br /> выпуск «Standard Edition»;<br /><br /> «Web Edition».<br /><br /> Указывает «SQL Azure» [!INCLUDE[ssSDS](../../includes/sssds-md.md)] или[!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|EditionID|EditionID представляет установленный выпуск продукта для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Используйте значение этого свойства для определения возможностей и ограничений, таких как [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).<br /><br /> 1804890536 = Enterprise<br /><br /> 1872460670 = Enterprise Edition: лицензирование по числу ядер<br /><br /> 610778273 = Enterprise Evaluation<br /><br /> 284895786 = Business Intelligence<br /><br /> -2117995310 = Developer<br /><br /> -1592396055 = Express<br /><br /> -133711905= Express with Advanced Services<br /><br /> Значения -1534726760 = standard<br /><br /> 1293598313 = Web<br /><br /> 1674378470 = база данных SQL или хранилище данных SQL<br /><br /> Базовый тип данных: **bigint**|  
|EngineEdition|Выпуск компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], установленного на сервере.<br /><br /> 1 = Personal или Desktop Engine (недоступен для [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий).<br /><br /> 2 = Standard (возвращается для выпусков Standard, Web и Business Intelligence).<br /><br /> 3 = Enterprise (это значение возвращается для выпусков Evaluation Edition, Developer Edition и обоих вариантов Enterprise Edition).<br /><br /> 4 = Express (возвращается для выпусков Express, Express with Tools и Express with Advanced Services).<br /><br /> 5 = [!INCLUDE[ssSDS](../../includes/sssds-md.md)]<br /><br /> 6 - [!INCLUDE[ssDW](../../includes/ssdw-md.md)]<br /><br /> Базовый тип данных: **int**|  
|HadrManagerStatus|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Показывает, запущен ли диспетчер [!INCLUDE[ssHADR](../../includes/sshadr-md.md)].<br /><br /> 0 = не запущен, ожидает связи.<br /><br /> 1 = запущен и выполняется.<br /><br /> 2 = не запущен и завершился неудачно.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.|  
|InstanceDefaultDataPath|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Имя пути по умолчанию файлы данных экземпляра.|  
|InstanceDefaultLogPath|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Имя пути по умолчанию файлы журнала экземпляра.|  
|InstanceName|Имя экземпляра, к которому подключен пользователь.<br /><br /> Возвращает значение NULL в случае, если имя экземпляра установлено по умолчанию, при возникновении ошибки и в случае, если входные данные оказываются недопустимы.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|IsAdvancedAnalyticsInstalled|Возвращает 1, если компонент Advanced Analytics был установлен во время установки; 0, Если Advanced Analytics не установлен.|  
|IsClustered|Экземпляр сервера настроен для работы в отказоустойчивом кластере.<br /><br /> 1 = в кластере.<br /><br /> 0 = не в кластере.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|IsFullTextInstalled|На текущем экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлены компоненты полнотекстового и семантического индексирования.<br /><br /> 1 = компоненты полнотекстового и семантического индексирования установлены.<br /><br /> 0 = компоненты полнотекстового и семантического индексирования не установлены.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|IsHadrEnabled|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] включена на этом экземпляре сервера.<br /><br /> 0 = компонент [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] отключен.<br /><br /> 1 = компонент [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] включен.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**<br /><br /> Для реплик доступности, создаваемых и запускаемых на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на экземпляре сервера должна быть включена служба [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. Дополнительные сведения см. в разделе [Включение и отключение групп доступности AlwaysOn (SQL Server)](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md).<br /><br /> **Примечание:** IsHadrEnabled свойство относится только к [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]. Другие возможности высокого уровня доступности или аварийного восстановления, такие как зеркальное отображение базы данных или доставка журналов, не затрагиваются этим свойством сервера.|  
|IsIntegratedSecurityOnly|Сервер запущен во встроенном режиме безопасности.<br /><br /> 1 = встроенная безопасность (проверка подлинности Windows)<br /><br /> 0 = без встроенного режима безопасности. (Как проверка подлинности Windows, так и проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].)<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|IsLocalDB|**Область применения**: начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Сервер является экземпляром [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] LocalDB.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.|  
|IsPolybaseInstalled|**Область применения**: [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].<br /><br /> Показывает, имеет ли экземпляр сервера установлен компонент PolyBase.<br /><br /> 0 = PolyBase не установлен.<br /><br /> 1 = установки PolyBase.<br /><br /> Базовый тип данных: **int**|  
|IsSingleUser|Server запущен в однопользовательском режиме.<br /><br /> 1 = однопользовательский режим.<br /><br /> 0 = не однопользовательский режим.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|IsXTPSupported|**Применяется к**: SQL Server ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] через [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]), [!INCLUDE[ssSDS](../../includes/sssds-md.md)].<br /><br /> Сервер поддерживает компонент In-Memory OLTP.<br /><br /> 1 = сервер поддерживает компонент In-Memory OLTP.<br /><br /> 0= сервер не поддерживает компонент In-Memory OLTP.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|LCID|Код локали Windows для параметров сортировки.<br /><br /> Базовый тип данных: **int**|  
|LicenseType|Не используется. В продукте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сохраняются сведения о лицензии. Всегда возвращает DISABLED.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|MachineName|Имя компьютера Windows, на котором запущен экземпляр сервера.<br /><br /> Для кластеризованного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], работающего на виртуальном сервере службы кластеров (Майкрософт), возвращается имя виртуального сервера.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|NumLicenses|Не используется. В продукте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сохраняются сведения о лицензии. Всегда возвращает значение NULL.<br /><br /> Базовый тип данных: **int**|  
|ProcessID|Идентификатор процесса службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С помощью свойства ProcessID удобно определять, какой файл Sqlservr.exe принадлежит этому экземпляру.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.<br /><br /> Базовый тип данных: **int**|  
|ProductBuild|**Применяется к**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] начиная с октября 2015 г.<br /><br /> Номер сборки.|  
|ProductBuildType|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Тип сборки текущей сборки.<br /><br /> Возвращает одно из следующих значений.<br /><br /> OD = по запросу выпуска конкретного клиента.<br /><br /> GDR = общедоступная версия распространения, выпущенных Центром обновления windows.<br /><br /> NULL<br />= Неприменимо.|  
|ProductLevel|Уровень версии экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Возвращает одно из следующих значений.<br /><br /> 'RTM' = Исходная выпущенная версия<br /><br /> ' SP*n*' = версия пакета обновления<br /><br /> ' CTP*n*', = версия CTP-версии<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|ProductMajorVersion|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Основной номер версии.|  
|ProductMinorVersion|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Дополнительный номер версии.|  
|ProductUpdateLevel|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Обновление текущей сборки. CU указывает накопительный пакет обновления.<br /><br /> Возвращает одно из следующих значений.<br /><br /> CU *n*  = накопительного пакета обновления<br /><br /> NULL<br />= Неприменимо.|  
|ProductUpdateReference|**Применяется к**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] до текущей версии в обновления, начиная с поздним 2015.<br /><br /> Статья БАЗЫ знаний для этого выпуска.|  
|ProductVersion|Версия экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в виде "*major.minor.build.revision*".<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|ResourceLastUpdateDateTime|Отображаются дата и время последнего изменения базы данных Resource.<br /><br /> Базовый тип данных: **даты и времени**|  
|ResourceVersion|Возвращает версию базы данных Resource.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|ServerName|Сведения об экземпляре и сервере Windows, связанные с определенным экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> NULL = недопустимый ввод или произошла ошибка.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|SqlCharSet|Идентификатор кодировки SQL из идентификатора параметров сортировки.<br /><br /> Базовый тип данных: **tinyint**|  
|SqlCharSetName|Имя кодировки SQL из параметров сортировки.<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|SqlSortOrder|Идентификатор порядка сортировки SQL из параметров сортировки<br /><br /> Базовый тип данных: **tinyint**|  
|SqlSortOrderName|Имя порядка сортировки SQL из параметров сортировки<br /><br /> Базовый тип данных: **nvarchar(128)**|  
|FilestreamShareName|Имя общего ресурса, используемое FILESTREAM.<br /><br /> NULL = недопустимый ввод, ошибка или неприменимо.|  
|FilestreamConfiguredLevel|Настроенный уровень доступа FILESTREAM. Дополнительные сведения см. в разделе [уровень доступа filestream](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).|  
|FilestreamEffectiveLevel|Действующий уровень доступа FILESTREAM. Это значение может отличаться от значения FilestreamConfiguredLevel, если уровень был изменен и ожидается перезапуск экземпляра или перезагрузка компьютера. Дополнительные сведения см. в разделе [уровень доступа filestream](../../database-engine/configure-windows/filestream-access-level-server-configuration-option.md).|  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **sql_variant**  
  
## <a name="remarks"></a>Замечания  
  
### <a name="servername-property"></a>Свойство ServerName  
 `ServerName` Свойство `SERVERPROPERTY` функции и [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) возвращают аналогичные сведения. В свойстве `ServerName` задаются имена экземпляра и сервера Windows, которые вместе образуют уникальный экземпляр сервера. [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) предоставляет имя локального сервера, в настоящий момент.  
  
 `ServerName` Свойство и [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) возвращают одинаковые данные, если имя сервера по умолчанию во время установки не было изменено. Имя локального сервера можно настроить, выполнив следующие команды:  
  
```  
EXEC sp_dropserver 'current_server_name';  
GO  
EXEC sp_addserver 'new_server_name', 'local';  
GO  
```  
  
 Если имя локального сервера было изменено с имени сервера по умолчанию во время установки [@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) возвращает новое имя.  
  
### <a name="version-properties"></a>Свойства версии  
 `SERVERPROPERTY` Функция возвращает отдельные свойства, которые относятся к сведения о версии, а [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md) функция объединяет выходные данные в одну строку. Если приложению требуется отдельное свойство строки, можно использовать `SERVERPROPERTY` функция, возвращающая их вместо синтаксического анализа [@@VERSION ](../../t-sql/functions/version-transact-sql-configuration-functions.md) результаты.  

## <a name="permissions"></a>Permissions

Все пользователи могут запрашивать свойства сервера. 
  
## <a name="examples"></a>Примеры  
 В следующем примере используется `SERVERPROPERTY` функционировать в `SELECT` инструкции для возврата сведений о текущем экземпляре [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].   
  
```  
SELECT  
  SERVERPROPERTY('MachineName') AS ComputerName,
  SERVERPROPERTY('ServerName') AS InstanceName,  
  SERVERPROPERTY('Edition') AS Edition,
  SERVERPROPERTY('ProductVersion') AS ProductVersion,  
  SERVERPROPERTY('ProductLevel') AS ProductLevel;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Выпуски и компоненты SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)  
  
  

