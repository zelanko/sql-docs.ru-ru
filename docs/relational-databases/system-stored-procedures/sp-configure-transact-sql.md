---
title: sp_configure (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 09/07/2018
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_configure
- sp_configure_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_configure
ms.assetid: d18b251d-b37a-4f5f-b50c-502d689594c8
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 22d8f61af08f183e10910544e42614769b9dafd9
ms.sourcegitcommit: f6bfe4a0647ce7efebaca11d95412d6a9a92cd98
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974351"
---
# <a name="sp_configure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-pdw-md.md)]

  Отображает или изменяет глобальные параметры конфигурации текущего сервера.

> [!NOTE]  
> Сведения о параметрах конфигурации уровня базы данных см. в разделе [ALTER &#40;Database scoped&#41;Configuration Transact-SQL](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Сведения о настройке программной архитектуры NUMA см. в разделе [Soft-numa &#40;&#41;SQL Server](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
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
`[ @configname = ] 'option_name'` — имя параметра конфигурации. Аргумент*option_name* имеет тип **varchar(35)** , значение по умолчанию — NULL. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] распознает любую уникальную строку, являющуюся частью имени конфигурации. Если этот параметр отсутствует, возвращается список всех параметров.  
  
 Сведения о доступных параметрах конфигурации и их параметрах см. в разделе [Параметры &#40;конфигурации&#41;сервера SQL Server](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
`[ @configvalue = ] 'value'` — это новый параметр конфигурации. Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Максимальное значение зависит от конкретного параметра.  
  
 Чтобы увидеть максимальное значение для каждого параметра, см. столбец **Максимальное** в представлении каталога **sys. Configurations** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 При выполнении без параметров **хранимая процедура sp_configure** возвращает результирующий набор с пятью столбцами и упорядочивает параметры в алфавитном порядке по возрастанию, как показано в следующей таблице.  
  
 Значения для **config_value** и **run_value** не эквивалентны автоматически. После обновления параметра конфигурации с помощью **хранимой процедуры sp_configure**системный администратор должен обновить выполняемое значение конфигурации, используя перенастройку или ПЕРЕнастроить с помощью переопределения. Дополнительные сведения см. в разделе "Примечания".  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**minimum**|**int**|Минимальное значение параметра конфигурации.|  
|**maximum**|**int**|Максимальное значение параметра конфигурации.|  
|**config_value**|**int**|Значение, для которого параметр конфигурации был задан с помощью **хранимой процедуры sp_configure** (значение в **sys. Configurations. Value**). Дополнительные сведения об этих параметрах см. в разделе [Параметры &#40;конфигурации&#41; сервера SQL Server](../../database-engine/configure-windows/server-configuration-options-sql-server.md) и [sys &#40;. Configurations&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
|**run_value**|**int**|Текущее значение параметра конфигурации (значение в **sys. Configurations. value_in_use**).<br /><br /> Дополнительные сведения см. в разделе [sys. &#40;Configurations Transact&#41;-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
  
## <a name="remarks"></a>Примечания  
 Используйте **хранимую процедуру sp_configure** для вывода или изменения параметров серверного уровня. Для изменения параметров уровня базы данных используйте инструкцию ALTER DATABASE. Для изменения параметров, влияющих только на сеанс текущего пользователя, используйте инструкцию SET.  
  
## <a name="updating-the-running-configuration-value"></a>Обновление активного значения конфигурации  
 При указании нового *значения* для *параметра*результирующий набор показывает это значение в столбце **config_value** . Изначально это значение отличается от значения в столбце **run_value** , которое показывает текущее выполняемое значение конфигурации. Чтобы обновить значение выполняющейся конфигурации в столбце **run_value** , системный администратор должен выполнить перенастройку или ПЕРЕнастроить с переопределением.  
  
 Обе инструкции — и RECONFIGURE, и RECONFIGURE WITH OVERRIDE — работают с любым параметром конфигурации. Однако базовая инструкция RECONFIGURE отклоняет значение параметра, выходящее за разумный диапазон или способное вызвать конфликт параметров. Например, ПОВТОРная настройка выдает ошибку, если значение **интервала восстановления** превышает 60 минут или если значение **маски сходства** пересекается со значением **сходства ввода-вывода** . В противоположность этому, инструкция RECONFIGURE WITH OVERRIDE принимает любое значение параметра с правильным типом данных и инициирует повторную конфигурацию с заданным значением.  
  
> [!CAUTION]  
> Недопустимое значение параметра может отрицательно сказаться на конфигурации экземпляра сервера. Поэтому использовать инструкцию RECONFIGURE WITH OVERRIDE следует с осторожностью.  
  
 Инструкция RECONFIGURE выполняет динамическое обновление некоторых параметров; для обновления других параметров необходимо остановить и перезапустить сервер. Например, параметры **min server memory** и **max server memory** Server динамически обновляются в [!INCLUDE[ssDE](../../includes/ssde-md.md)]; Поэтому их можно изменить без перезапуска сервера. В отличие от этого, для повторной настройки значения, выполняемого для параметра **fill factor** , необходимо перезапустить [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
 После выполнения команды "изменить конфигурацию" для параметра конфигурации можно определить, был ли обновлен параметр динамически, выполнив **процедуру sp_configure "***option_name***"** . Значения в столбцах **run_value** и **config_value** должны соответствовать динамически обновляемым параметрам. Можно также проверить, какие параметры являются динамическими, просмотрев столбец **is_dynamic** представления каталога **sys. Configurations** .  
 
 Это изменение также записывается в SQL Server журнал ошибок.
  
> [!NOTE]  
>  Если указанное *значение* слишком велико для параметра, столбец **run_value** отражает тот факт, что [!INCLUDE[ssDE](../../includes/ssde-md.md)] по умолчанию имеет значение динамической памяти, а не использует недопустимый параметр.  
  
 Дополнительные сведения см. в разделе [Повторная настройка &#40;Transact&#41;-SQL](../../t-sql/language-elements/reconfigure-transact-sql.md).  
  
## <a name="advanced-options"></a>Дополнительные параметры  
 Некоторые параметры конфигурации, такие как **маска сходства** и **интервал восстановления**, обозначены как дополнительные параметры. По умолчанию эти параметры недоступны для просмотра и изменения. Чтобы сделать их доступными, установите для параметра конфигурации **шовадванцедоптионс** значение 1.  
  
 Дополнительные сведения о параметрах конфигурации и их параметрах см. в разделе [Параметры &#40;конфигурации&#41;сервера SQL Server](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Чтобы выполнить **хранимую процедуру sp_configure** с обоими параметрами для изменения параметра конфигурации или выполнения инструкции RECONFIGURE, необходимо обладать разрешением ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. Вывод списка дополнительных параметров конфигурации  
 В следующем примере демонстрируется, как установить и отобразить все параметры конфигурации. Дополнительные параметры конфигурации отображаются, если предварительно параметру `show advanced option` присвоить значение `1`. После изменения этого параметра выполнение хранимой процедуры `sp_configure` без аргументов выводит все параметры конфигурации.  
  
```sql  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 Вот сообщение: "Параметр конфигурации" Показывать дополнительные параметры "изменен с 0 на 1. Выполните инструкцию RECONFIGURE для установки.  
  
 Выполните инструкцию `RECONFIGURE` и отобразите все параметры конфигурации:  
  
```sql  
RECONFIGURE;  
EXEC sp_configure;  
```  
  
### <a name="b-changing-a-configuration-option"></a>Б. Изменение параметра конфигурации  
 В следующем примере системный параметр `recovery interval` устанавливается в `3` минуты.  
  
```sql  
USE master;  
GO  
EXEC sp_configure 'recovery interval', '3';  
RECONFIGURE WITH OVERRIDE;  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>В. Список всех доступных параметров конфигурации.  
 В следующем примере демонстрируется, как создать список всех параметров конфигурации.  
  
```sql  
EXEC sp_configure;  
```  
  
 В результате возвращается имя параметра, за которым следуют его минимальное и максимальное значения. **Config_value** — это значение, которое [!INCLUDE[ssDW](../../includes/ssdw-md.md)] будет использоваться при завершении перенастройки. **run_value** — это значение, которое используется в настоящий момент. Значения **config_value** и **run_value** , как правило, совпадают, если не находятся в процессе изменения.  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>Г. Список параметров конфигурации для одного имени конфигурации.  
  
```sql  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>Д. Установка подключения к Hadoop.  
 Настройка подключения Hadoop требует выполнения еще нескольких действий в дополнение к запуску процедуры sp_configure. Полную процедуру см. в разделе [Создание внешнего источника &#40;данных Transact-SQL&#41;](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
## <a name="see-also"></a>См. также  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.configurations (Transact-SQL)](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ALTER DATABASE SCOPED CONFIGURATION (Transact-SQL)](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
