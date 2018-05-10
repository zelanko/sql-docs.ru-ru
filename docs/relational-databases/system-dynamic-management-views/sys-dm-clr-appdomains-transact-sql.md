---
title: sys.dm_clr_appdomains (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_clr_appdomains
- sys.dm_clr_appdomains
- dm_clr_appdomains_TSQL
- sys.dm_clr_appdomains_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_clr_appdomains dynamic management dynamic management view
ms.assetid: 9fe0d4fd-950a-4274-a493-85e776278045
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 501e126a3064489852987671c83326f0d4a53832
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmclrappdomains-transact-sql"></a>sys.dm_clr_appdomains (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку на каждый домен приложения на сервере. Домен приложения (**AppDomain**) представляет собой конструкцию в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] общеязыковая среда выполнения (CLR), являющейся единицей изоляции для приложения. Это представление можно использовать для исследования и устранения проблем объектов интеграции со средой CLR, выполняющихся в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Существует несколько типов управляемых объектов CLR для баз данных. Общие сведения об этих объектах см. в разделе [построение объектов базы данных с интеграцией Common Language Runtime (CLR)](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md). Каждый раз, когда эти объекты выполняются, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] создает **AppDomain** под его можно загружать и выполнять требуемый код. Уровень изоляции для **AppDomain** — один **AppDomain** каждой базы данных владельца. То есть все объекты среды CLR, принадлежащие пользователю всегда выполняются в том же **AppDomain** каждой базы данных (если пользователь регистрирует объекты базы данных среды CLR в разных базах данных, базы данных среды CLR, объекты, работают в разных доменах приложений). **AppDomain** не уничтожается после завершения выполнения кода. Вместо этого он кэшируется в памяти для последующего использования. Это улучшает производительность.  
  
 Дополнительные сведения см. в разделе [домены приложений](http://go.microsoft.com/fwlink/p/?LinkId=299658).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**appdomain_address**|**varbinary(8)**|Адрес **AppDomain**. Все управляемые базы данных, объекты, принадлежащие пользователю, всегда загружаются в одном **AppDomain**. Этот столбец можно использовать для поиска всех сборок, загруженных в данный момент в этом **AppDomain** в **sys.dm_clr_loaded_assemblies**.|  
|**appdomain_id**|**int**|Идентификатор **AppDomain**. Каждый **AppDomain** имеет уникальный идентификатор.|  
|**appdomain_name**|**varchar(386)**|Имя **AppDomain** , назначенный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**creation_time**|**datetime**|Время, когда **AppDomain** был создан. Поскольку **доменов приложений** кэшируются и используются повторно для повышения производительности, **creation_time** не обязательно является время выполнения кода.|  
|**db_id**|**int**|Идентификатор базы данных, в котором **AppDomain** был создан. Код, хранимый в двух разных базах данных не могут совместно использовать один **AppDomain**.|  
|**user_id**|**int**|Идентификатор пользователя, объекты которого могут выполняться в этом **AppDomain**.|  
|**state**|**nvarchar(128)**|Дескриптор для текущего состояния **AppDomain**. Домен приложения может быть в различных состояниях — от создания до удаления. Дополнительные сведения см. в подразделе «Примечания».|  
|**strong_refcount**|**int**|Количество жестких ссылок на **AppDomain**. Это отражает количество выполняющихся пакетов, использующих этот **AppDomain**. Обратите внимание, что выполнение этого представления создаст **счетчик жестких ссылок**, даже если нет кода в данный момент, **strong_refcount** будет иметь значение 1.|  
|**weak_refcount**|**int**|Количество слабых ссылок на это **AppDomain**. Это указывает, сколько объектов внутри **AppDomain** кэшируются. При выполнении управляемого объекта базы данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] кэширует его в **AppDomain** для повторного использования в будущем. Это улучшает производительность.|  
|**Стоимость**|**int**|Стоимость в сумме **AppDomain**. Чем выше стоимость, тем выше вероятность это **AppDomain** будет выгружен при недостатке свободной памяти. Стоимость обычно зависит от объема памяти, необходимые для повторного создания данного **AppDomain**.|  
|**value**|**int**|Значение **AppDomain**. Чем меньше значение, тем выше вероятность это **AppDomain** будет выгружен при недостатке свободной памяти. Значение обычно зависит от количества соединений или пакетов, использующих этот **AppDomain**.|  
|**total_processor_time_ms**|**bigint**|Суммарное время процессора в миллисекундах, использованное всеми потоками при выполнении в текущем домене приложения с момента запуска процесса. Это эквивалентно **System.AppDomain.MonitoringTotalProcessorTime**.|  
|**total_allocated_memory_kb**|**bigint**|Общий размер (в килобайтах) всей выделенной памяти, которая была выделена в домене приложения с момента его создания (без вычета освобожденной и собранной памяти). Это эквивалентно **System.AppDomain.MonitoringTotalAllocatedMemorySize**.|  
|**survived_memory_kb**|**bigint**|Количество килобайт, сохранившихся после последней полной, блокирующей сборки мусора, на которые заведомо существуют ссылки из текущего домена приложения. Это эквивалентно **System.AppDomain.MonitoringSurvivedMemorySize**.|  
  
## <a name="remarks"></a>Замечания  
 Имеется отношение "один ко многим" между **dm_clr_appdomains.appdomain_address** и **dm_clr_loaded_assemblies.appdomain_address**.  
  
 В следующих таблицах список возможных **состояние** значения, их описания и в случае, если **AppDomain** жизненного цикла. Эти сведения можно использовать, чтобы отслеживать жизненный цикл **AppDomain** , контролировать подозрительную или повторяющуюся **AppDomain** экземпляров домена приложений без необходимости анализировать журнал событий Windows.  
  
## <a name="appdomain-initialization"></a>Инициализация домена приложений  
  
|Состояние|Описание|  
|-----------|-----------------|  
|E_APPDOMAIN_CREATING|**AppDomain** находится в процессе создания.|  
  
## <a name="appdomain-usage"></a>Использование домена приложений  
  
|Состояние|Описание|  
|-----------|-----------------|  
|E_APPDOMAIN_SHARED|Среда выполнения **AppDomain** готов для использования несколькими пользователями.|  
|E_APPDOMAIN_SINGLEUSER|**AppDomain** готов для использования в операциях DDL. Это отличается от E_APPDOMAIN_SHARED, в котором используется общий домен приложения для выполнения интеграции CLR в качестве противопоставления операциям DDL. Такие домены приложения изолированы от остальных текущих операций.|  
|E_APPDOMAIN_DOOMED|**AppDomain** запланирована выгрузка, но в данный момент потоков, выполняющихся в ней.|  
  
## <a name="appdomain-cleanup"></a>Очистка домена приложений  
  
|Состояние|Описание|  
|-----------|-----------------|  
|E_APPDOMAIN_UNLOADING|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] был запрошен, среда CLR выгружала **AppDomain**, как правило, так как сборка, содержащая управляемые объекты базы данных была изменена или удалена.|  
|E_APPDOMAIN_UNLOADED|Среда CLR выгрузила **AppDomain**. Это обычно является результатом процедуры из-за **ThreadAbort**, **OutOfMemory**, или необработанное исключение в пользовательском коде.|  
|E_APPDOMAIN_ENQUEUE_DESTROY|**AppDomain** выгружен в среде CLR и задать будет уничтожен [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_DESTROY|**AppDomain** в процессе удаления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|E_APPDOMAIN_ZOMBIE|**AppDomain** Ликвидировано [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], однако не все ссылки на **AppDomain** были очищены.|  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения VIEW SERVER STATE на базу данных.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как просмотреть сведения о **AppDomain** для данной сборки:  
  
```  
select appdomain_id, creation_time, db_id, user_id, state  
from sys.dm_clr_appdomains a  
where appdomain_address =   
(select appdomain_address   
 from sys.dm_clr_loaded_assemblies  
   where assembly_id = 500);  
```  
  
 В следующем примере показано, как просмотреть все сборки в данной **AppDomain**:  
  
```  
select a.name, a.assembly_id, a.permission_set_desc, a.is_visible, a.create_date, l.load_time   
from sys.dm_clr_loaded_assemblies as l   
inner join sys.assemblies as a  
on l.assembly_id = a.assembly_id  
where l.appdomain_address =   
(select appdomain_address   
from sys.dm_clr_appdomains  
where appdomain_id = 15);  
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_clr_loaded_assemblies &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-clr-loaded-assemblies-transact-sql.md)   
 [Динамические административные представления, связанные с общеязыковой &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/common-language-runtime-related-dynamic-management-views-transact-sql.md)  
  
  
