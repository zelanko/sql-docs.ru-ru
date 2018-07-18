---
title: sys.fn_xe_file_target_read_file (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/22/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_xe_file_target_read_file_TSQL
- fn_xe_file_target_read_file
- sys.fn_xe_file_target_read_file_TSQL
- sys.fn_xe_file_target_read_file
dev_langs:
- TSQL
helpviewer_keywords:
- extended events [SQL Server], functions
- fn_xe_file_target_read_file function
- sys.fn_xe_file_target_read_file function
ms.assetid: cc0351ae-4882-4b67-b0d8-bd235d20c901
caps.latest.revision: 20
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f3836b2932d9856c59e1d511d53998df57856f08
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239254"
---
# <a name="sysfnxefiletargetreadfile-transact-sql"></a>sys.fn_xe_file_target_read_file (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Читает файлы, создаваемые асинхронным целевым файловым объектом расширенных событий. Возвращается одно событие в каждой строке в формате XML.  
  
> [!WARNING]  
>  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] и [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] принимают результаты трассировки, сформированные в формате XEL и XEM. [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] Расширенные события поддерживают только результаты трассировки в формате XEL. Для чтения результатов трассировки в формате XEL рекомендуется использовать SQL Server Management Studio.    
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_xe_file_target_read_file ( path, mdpath, initial_file_name, initial_offset )  
```  
  
## <a name="arguments"></a>Аргументы  
 *путь*  
 Путь к файлам для чтения. *путь* может содержать символы-шаблоны и включать имя файла. *путь* — **nvarchar(260)**. Значение по умолчанию отсутствует. В контексте базы данных SQL Azure это значение является URL-адрес HTTP для файла в хранилище Azure.
  
 *mdpath*  
 Путь к файлу метаданных, соответствующий файлу или файлам, указанным *путь* аргумент. *mdpath* — **nvarchar(260)**. Значение по умолчанию отсутствует. Начиная с SQL Server 2016, этот параметр может быть задан как null.
  
> [!NOTE]  
>  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] не требует *mdpath* параметра. Однако он используется для поддержки обратной совместимости фалов журналов, сформированных в предыдущих версиях SQL Server.  
  
 *initial_file_name*  
 Первый файл, из которого выполняется чтение *путь*. *initial_file_name* — **nvarchar(260)**. Значение по умолчанию отсутствует. Если **null** указывается как аргумент, всех файлов, найденных в *путь* доступны для чтения.  
  
> [!NOTE]  
>  *initial_file_name* и *initial_offset* парной аргументы. При указании значения для любого из этих аргументов необходимо также указать значение для второго аргумента.  
  
 *initial_offset*  
 Используется для указания последнего считанного ранее смещения и пропуска всех событий до смещения (включительно). Перечисление событий начинается после указанного смещения. *initial_offset* — **bigint**. Если **null** указывается как аргумент по всему файлу для чтения.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|module_guid|**uniqueidentifier**|Идентификатор GUID модуля событий. Не допускает значение NULL.|  
|package_guid|**uniqueidentifier**|Идентификатор GUID пакета событий. Не допускает значение NULL.|  
|object_name|**nvarchar(256)**|Имя события. Не допускает значение NULL.|  
|event_data|**nvarchar(max)**|Содержимое события в формате XML. Не допускает значение NULL.|  
|file_name|**nvarchar(260)**|Имя файла, содержащего событие. Не допускает значение NULL.|  
|file_offset|**bigint**|Смещение блока в файле, содержащем событие. Не допускает значение NULL.|  
|timestamp_utc|**datetime2**|**Применимо к**: с [!INCLUDE[ssSQLv14](../../includes/sssqlv14-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].<br /><br />Дата и время события (по Гринвичу). Не допускает значение NULL.|  

  
## <a name="remarks"></a>Замечания  
 Чтение больших результирующих наборов, выполнив **sys.fn_xe_file_target_read_file** в [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] может привести к возникновению ошибки. Используйте **результаты в файл** режим (**Ctrl + Shift + F**) для экспорта больших результирующих наборов в файл и вместо этого прочитать файл с помощью другого средства.  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-retrieving-data-from-file-targets"></a>A. Извлечение данных из целевых файлов  
 В следующем примере извлекаются все строки из всех файлов. В этом примере целевые файлы и метафайлы расположены в папке трассировки на диске «C:\».  
  
```  
SELECT * FROM sys.fn_xe_file_target_read_file('C:\traces\*.xel', 'C:\traces\metafile.xem', null, null);  
```  
  
## <a name="see-also"></a>См. также  
 [Динамические административные представления расширенных событий](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [Представления каталога расширенных событий (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
