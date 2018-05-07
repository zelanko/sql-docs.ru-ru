---
title: sp_help_fulltext_system_components (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_components_TSQL
- sp_help_fulltext_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_system_components
ms.assetid: ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 849f2bbd004c47992c6b6faecf06b5abe5bcc9ea
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="sphelpfulltextsystemcomponents-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Возвращает сведения о зарегистрированных средствах разбиения по словам, фильтрах и обработчиках протоколов. **sp_help_fulltext_system_components** также возвращает список идентификаторов баз данных и полнотекстовых каталогов, использовавших указанный компонент.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_fulltext_system_components   
         { 'all'| [ @component_type = ] 'component_type' }  
    , [ @param = ] 'param'  
```  
  
## <a name="arguments"></a>Аргументы  
 'all'  
 Возвращает сведения для всех полнотекстовых компонентов.  
  
 [  **@component_type=** ] *component_type*  
 Указывает тип компонента. *component_type* может принимать одно из следующих действий:  
  
-   **средство разбиения по словам**  
  
-   **фильтр**  
  
-   **обработчик протокола**  
  
-   **FullPath**  
  
 Если указан полный путь, в аргументе *param* необходимо также указать полный путь к DLL-библиотеке компонента. В противном случае будет возвращено сообщение об ошибке.  
  
 [  **@param=** ] *param*  
 В зависимости от типа компонента указывается одно из следующих значений: идентификатор локали (LCID), расширение файла с префиксом ".", полное имя компонента обработчика протокола или полный путь к DLL-компоненту.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Следующий результирующий набор возвращается для системных компонентов.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**componenttype**|**sysname**|Тип компонента. Это может быть:<br /><br /> фильтр<br /><br /> обработчик протокола<br /><br /> разделитель слов|  
|**componentname**|**sysname**|Имя компонента.|  
|**Идентификатор CLSID**|**uniqueidentifier**|Идентификатор класса компонента.|  
|**FullPath**|**nvarchar(256)**|Путь к расположению компонента.<br /><br /> NULL = вызывающая сторона не является членом **serveradmin** предопределенной роли сервера.|  
|**version**|**nvarchar(30)**|Версия компонента.|  
|**Изготовитель**|**sysname**|Имя производителя компонента.|  
  
 Следующий результирующий набор возвращается только в том случае, если один или более одного полнотекстового каталога, использующий *component_type*.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**dbid**|**int**|Идентификатор базы данных.|  
|**ftcatid**|**int**|Идентификатор полнотекстового каталога.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **открытый** роли; тем не менее, пользователи могут видеть только сведения о полнотекстовых каталогах, для которых у них есть разрешение VIEW DEFINITION. Значения столбца **fullpath** могут просматривать только члены предопределенной роли сервера **serveradmin** .  
  
## <a name="remarks"></a>Замечания  
 Этот метод очень важен при подготовке к обновлению. Запустите хранимую процедуру в определенной базе данных и используйте результаты, чтобы определить, будет ли определенный каталог затронут обновлением.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-all-full-text-system-components"></a>A. Перечисление всех полнотекстовых системных компонентов  
 В следующем примере перечислены все полнотекстовые системные компоненты, зарегистрированные на экземпляре сервера.  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>Б. Перечисление средств разбиения по словам  
 В следующем примере перечислены все средства разбиения по словам, зарегистрированные в экземпляре сервера.  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>В. Определение того, зарегистрировано ли средство разбиения по словам  
 В следующем примере будет выведено средство разбиения по словам для турецкого языка (LCID = 1055), если оно установлено в системе и зарегистрировано в экземпляре сервера. В этом примере задаются имена параметров, **@component_type** и **@param**.  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 По умолчанию средство разбиения по словам не установлено, поэтому результирующий набор будет пустым.  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>Г. Определение того, зарегистрирован ли тот или иной фильтр  
 В следующем примере приведен фильтр для компонента XDOC, если он был вручную установлен в системе и зарегистрирован в экземпляре сервера.  
  
```  
EXEC sp_help_fulltext_system_components 'filter', '.xdoc';  
GO  
```  
  
 По умолчанию этот фильтр не устанавливается, поэтому результирующий набор будет пустым.  
  
### <a name="e-listing-a-specific-dll-file"></a>Д. Листинг конкретного DLL-файла  
 В следующем примере выводится конкретный DDL-файл `nlhtml.dll`, установленный по умолчанию.  
  
```  
EXEC sp_help_fulltext_system_components 'fullpath',   
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\nlhtml.dll';  
GO  
  
```  
  
## <a name="see-also"></a>См. также  
 [Просмотр или изменение зарегистрированных фильтры и средства разбиения по словам](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [Настройка и управление средством разбиения на слова и парадигматические модули для поиска](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [Настройка поисковых фильтров и управление ими](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Компонент Full-Text Search и семантический поиск хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  
