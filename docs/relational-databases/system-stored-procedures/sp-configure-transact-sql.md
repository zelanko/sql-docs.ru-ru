---
title: "sp_configure (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: d6ff78066f307e70f37880eb57e2430774c242ae
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spconfigure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Отображает или изменяет глобальные параметры конфигурации текущего сервера.  
  
> [!NOTE]  
>  Параметры конфигурации уровня базы данных см. в разделе [ALTER DATABASE SCOPED CONFIGURATION &#40; Transact-SQL &#41; ](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Для настройки программной архитектуры NUMA см [программной архитектуры NUMA &#40; SQL Server &#41; ](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server  
  
sp_configure [ [ @configname = ] 'option_name'   
    [ , [ @configvalue = ] 'value' ] ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
-- List all of the configuration options  
sp_configure  
[;]  
  
-- Configure Hadoop connectivity  
sp_configure [ @configname= ] 'hadoop connectivity',  
             [ @configvalue = ] { 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 }  
[;]  
RECONFIGURE  
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@configname=** ] **"***имя_параметра***"**  
 Имя параметра конфигурации. Аргумент*option_name* имеет тип **varchar(35)**, значение по умолчанию — NULL. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] распознает любую уникальную строку, являющуюся частью имени конфигурации. Если этот параметр отсутствует, возвращается список всех параметров.  
  
 Сведения о доступных параметрах конфигурации и их значениях см. в разделе [параметры конфигурации сервера &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
 [ **@configvalue=** ] **"***значение***"**  
 Новое значение параметра конфигурации. Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Максимальное значение зависит от конкретного параметра.  
  
 Максимальное значение для каждого параметра см. в разделе **максимальное** столбец **sys.configurations** представления каталога.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 При выполнении без параметров, **sp_configure** возвращает результирующий набор с пятью столбцами и упорядочивает параметры в алфавитном порядке по возрастанию, как показано в следующей таблице.  
  
 Значения для **config_value** и **run_value** не всегда эквивалентны. После обновления параметра конфигурации с помощью **sp_configure**, администратор системы должен обновить активное значение с помощью RECONFIGURE или RECONFIGURE WITH OVERRIDE. Дополнительные сведения см. в разделе «Примечания».  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**minimum**|**int**|Минимальное значение параметра конфигурации.|  
|**maximum**|**int**|Максимальное значение параметра конфигурации.|  
|**config_value**|**int**|Значение, к которому было установлено для параметра конфигурации с помощью **sp_configure** (значение в **sys.configurations.value**). Дополнительные сведения об этих параметрах см. в разделе [параметры конфигурации сервера &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md) и [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
|**run_value**|**int**|Текущее активное значение параметра конфигурации (значение в **sys.configurations.value_in_use**).<br /><br /> Дополнительные сведения см. в разделе [sys.configurations &#40; Transact-SQL &#41; ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
  
## <a name="remarks"></a>Замечания  
 Используйте **sp_configure** для отображения или изменения параметров уровня сервера. Для изменения параметров уровня базы данных используйте инструкцию ALTER DATABASE. Для изменения параметров, влияющих только на сеанс текущего пользователя, используйте инструкцию SET.  
  
## <a name="updating-the-running-configuration-value"></a>Обновление активного значения конфигурации  
 При указании нового *значение* для *параметр*, результирующий набор отображает это значение в **config_value** столбца. Это значение сначала отличается от значения в **run_value** столбец, в котором показано текущее значение конфигурации. Обновление активного значения параметра конфигурации в **run_value** столбца, администратор системы должен выполнить инструкцию RECONFIGURE или RECONFIGURE WITH OVERRIDE.  
  
 Обе инструкции — и RECONFIGURE, и RECONFIGURE WITH OVERRIDE — работают с любым параметром конфигурации. Однако базовая инструкция RECONFIGURE отклоняет значение параметра, выходящее за разумный диапазон или способное вызвать конфликт параметров. Например, инструкция RECONFIGURE возвращает ошибку, если **интервал восстановления** значение больше 60 минут или если **маска схожести** пересекается с **маска схожести ввода-вывода**значение. В противоположность этому, инструкция RECONFIGURE WITH OVERRIDE принимает любое значение параметра с правильным типом данных и инициирует повторную конфигурацию с заданным значением.  
  
> [!CAUTION]  
>  Недопустимое значение параметра может отрицательно сказаться на конфигурации экземпляра сервера. Поэтому использовать инструкцию RECONFIGURE WITH OVERRIDE следует с осторожностью.  
  
 Инструкция RECONFIGURE выполняет динамическое обновление некоторых параметров; для обновления других параметров необходимо остановить и перезапустить сервер. Например **параметре min server memory** и **Макс. памяти сервера** параметры памяти сервера динамически обновляются в [!INCLUDE[ssDE](../../includes/ssde-md.md)], поэтому их можно менять без перезапуска сервера. В отличие от этого изменения активного значения из **коэффициент заполнения** необходим перезапуск [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 После выполнения инструкции RECONFIGURE для параметра конфигурации, видно ли параметр был обновлен динамически при выполнении **sp_configure'***option_name***"**. Значения в **run_value** и **config_value** должны совпадать, если для параметра обновляется динамически. Можно также проверить, чтобы увидеть, какие параметры обновляются динамически, просмотрев **is_dynamic** столбец **sys.configurations** представления каталога.  
  
> [!NOTE]  
>  Если указанный *значение* слишком велико для параметра, **run_value** отражает тот факт, [!INCLUDE[ssDE](../../includes/ssde-md.md)] может динамической памяти, а не использовать параметр, который не является допустимым.  
  
 Дополнительные сведения см. в разделе [RECONFIGURE &#40; Transact-SQL &#41; ](../../t-sql/language-elements/reconfigure-transact-sql.md).  
  
## <a name="advanced-options"></a>Дополнительные параметры  
 Некоторые параметры конфигурации, такие как **маска схожести** и **интервал восстановления**, определенных в качестве дополнительных параметров. По умолчанию эти параметры недоступны для просмотра и изменения. Чтобы сделать их доступными, присвойте **ShowAdvancedOptions** параметр конфигурации 1.  
  
 Дополнительные сведения о параметрах конфигурации и их значениях см. в разделе [параметры конфигурации сервера &#40; SQL Server &#41; ](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
## <a name="permissions"></a>Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения **sp_configure** с обоими параметрами для изменения параметра конфигурации или выполнения инструкции RECONFIGURE необходимо предоставить разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. Вывод списка дополнительных параметров конфигурации  
 В следующем примере демонстрируется, как установить и отобразить все параметры конфигурации. Дополнительные параметры конфигурации отображаются, если предварительно параметру `show advanced option` присвоить значение `1`. После изменения этого параметра выполнение хранимой процедуры `sp_configure` без аргументов выводит все параметры конфигурации.  
  
```  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 Так выглядит ответное сообщение: «параметр конфигурации «show advanced options» изменен с 0 на 1. Выполните инструкцию RECONFIGURE для установки.  
  
 Выполните инструкцию `RECONFIGURE` и отобразите все параметры конфигурации:  
  
```  
RECONFIGURE;  
EXEC sp_configure;  
```  
  
### <a name="b-changing-a-configuration-option"></a>Б. Изменение параметра конфигурации  
 В следующем примере системный параметр `recovery interval` устанавливается в `3` минуты.  
  
```  
USE master;  
GO  
EXEC sp_configure 'recovery interval', '3';  
RECONFIGURE WITH OVERRIDE;  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>В. Список всех доступных параметров конфигурации.  
 В следующем примере демонстрируется, как создать список всех параметров конфигурации.  
  
```  
EXEC sp_configure;  
```  
  
 В результате возвращается имя параметра, за которым следуют его минимальное и максимальное значения. **Config_value** является значением, [!INCLUDE[ssDW](../../includes/ssdw-md.md)] будет использоваться после завершения перенастройки. **run_value** — это значение, которое используется в настоящий момент. Значения **config_value** и **run_value** , как правило, совпадают, если не находятся в процессе изменения.  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>Г. Список параметров конфигурации для одного имени конфигурации.  
  
```  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>Д. Установка подключения к Hadoop.  
 Для настройки подключения к Hadoop требуется еще несколько шагов, наряду с выполнением хранимой процедуры sp_configure. Полную процедуру в статье [CREATE EXTERNAL DATA SOURCE &#40; Transact-SQL &#41; ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
