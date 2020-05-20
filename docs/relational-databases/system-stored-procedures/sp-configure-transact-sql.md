---
title: sp_configure (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2019
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
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: e8d3284d8231b01b58cc807aeb70c55f5fe18c2b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82828428"
---
# <a name="sp_configure-transact-sql"></a>sp_configure (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-pdw-md.md)]

  Отображает или изменяет глобальные параметры конфигурации текущего сервера.

> [!NOTE]  
> Сведения о параметрах конфигурации уровня базы данных см. в разделе [ALTER DATABASE scoped configuration &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md). Сведения о настройке программной архитектуры NUMA см. в разделе [Soft-numa &#40;SQL Server&#41;](../../database-engine/configure-windows/soft-numa-sql-server.md).  
  
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
`[ @configname = ] 'option_name'`Имя параметра конфигурации. Аргумент*option_name* имеет тип **varchar(35)**, значение по умолчанию — NULL. Компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] распознает любую уникальную строку, являющуюся частью имени конфигурации. Если этот параметр отсутствует, возвращается список всех параметров.  
  
 Сведения о доступных параметрах конфигурации и их параметрах см. в разделе [Параметры конфигурации сервера &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
`[ @configvalue = ] 'value'`— Это новый параметр конфигурации. Аргумент*value* имеет тип **int**и значение по умолчанию NULL. Максимальное значение зависит от конкретного параметра.  
  
 Чтобы увидеть максимальное значение для каждого параметра, см. столбец **Максимальное** в представлении каталога **sys. Configurations** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 При выполнении без параметров **sp_configure** возвращает результирующий набор с пятью столбцами и упорядочивает параметры в алфавитном порядке по возрастанию, как показано в следующей таблице.  
  
 Значения для **config_value** и **run_value** не эквивалентны автоматически. После обновления параметра конфигурации с помощью **sp_configure**системный администратор должен обновить значение выполняющейся конфигурации с помощью перенастройки или повторной настройки с переопределением. Дополнительные сведения см. в разделе «Примечания».  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**name**|**nvarchar(35)**|Имя параметра конфигурации.|  
|**минимальное**|**int**|Минимальное значение параметра конфигурации.|  
|**выше**|**int**|Максимальное значение параметра конфигурации.|  
|**config_value**|**int**|Значение, для которого параметр конфигурации был задан с помощью **sp_configure** (значение в **sys. Configurations. Value**). Дополнительные сведения об этих параметрах см. в разделе [Параметры конфигурации сервера &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) и [sys. Configurations &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
|**run_value**|**int**|Текущее значение параметра конфигурации (значение в **sys. Configurations. value_in_use**).<br /><br /> Дополнительные сведения см. в разделе [sys. configurations &#40;&#41;Transact-SQL ](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md).|  
  
## <a name="remarks"></a>Примечания  
 Используйте **sp_configure** для просмотра или изменения параметров серверного уровня. Для изменения параметров уровня базы данных используйте инструкцию ALTER DATABASE. Для изменения параметров, влияющих только на сеанс текущего пользователя, используйте инструкцию SET.  
  
### [!INCLUDE [ssbigdataclusters-ss-nover](../../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE [big-data-clusters-master-instance-ha-endpoint-requirement](../../includes/big-data-clusters-master-instance-ha-endpoint-requirement.md)]

## <a name="updating-the-running-configuration-value"></a>Обновление активного значения конфигурации  
 При указании нового *значения* для *параметра*результирующий набор показывает это значение в **config_value** столбце. Изначально это значение отличается от значения в столбце **run_value** , которое показывает текущее значение конфигурации. Чтобы обновить значение выполняющейся конфигурации в столбце **run_value** , системный администратор должен выполнить перенастройку или ПЕРЕнастроить с переопределением.  
  
 Обе инструкции — и RECONFIGURE, и RECONFIGURE WITH OVERRIDE — работают с любым параметром конфигурации. Однако базовая инструкция RECONFIGURE отклоняет значение параметра, выходящее за разумный диапазон или способное вызвать конфликт параметров. Например, ПОВТОРная настройка выдает ошибку, если значение **интервала восстановления** превышает 60 минут или если значение **маски сходства** пересекается со значением **сходства ввода-вывода** . В противоположность этому, инструкция RECONFIGURE WITH OVERRIDE принимает любое значение параметра с правильным типом данных и инициирует повторную конфигурацию с заданным значением.  
  
> [!CAUTION]  
> Недопустимое значение параметра может отрицательно сказаться на конфигурации экземпляра сервера. Поэтому использовать инструкцию RECONFIGURE WITH OVERRIDE следует с осторожностью.  
  
 Инструкция RECONFIGURE выполняет динамическое обновление некоторых параметров; для обновления других параметров необходимо остановить и перезапустить сервер. Например, параметры **min server memory** и **max server memory** Server динамически обновляются в, [!INCLUDE[ssDE](../../includes/ssde-md.md)] поэтому их можно изменить без перезапуска сервера. В отличие от этого, для повторной настройки значения, выполняемого для параметра **Коэффициент заполнения** , необходимо перезапустить [!INCLUDE[ssDE](../../includes/ssde-md.md)] .  
  
 После выполнения команды "изменить конфигурацию" в конфигурации можно увидеть, что параметр был динамически обновлен путем выполнения **sp_configure "***option_name***"**. Значения в столбцах **run_value** и **config_value** должны соответствовать динамически обновляемым параметрам. Можно также проверить, какие параметры являются динамическими, просмотрев столбец **is_dynamic** представления каталога **sys. Configurations** .  
 
 Это изменение также записывается в SQL Server журнал ошибок.
  
> [!NOTE]  
>  Если указанное *значение* слишком велико для параметра, то столбец **run_value** отражает тот факт, что [!INCLUDE[ssDE](../../includes/ssde-md.md)] по умолчанию использует динамическую память, а не недопустимый параметр.  
  
 Дополнительные сведения см. в статье [перенастройка &#40;&#41;Transact-SQL ](../../t-sql/language-elements/reconfigure-transact-sql.md).  
  
## <a name="advanced-options"></a>Дополнительные параметры  
 Некоторые параметры конфигурации, такие как **маска сходства** и **интервал восстановления**, обозначены как дополнительные параметры. По умолчанию эти параметры недоступны для просмотра и изменения. Чтобы сделать их доступными, установите для параметра конфигурации **шовадванцедоптионс** значение 1.  
  
 Дополнительные сведения о параметрах конфигурации и их параметрах см. в разделе [Параметры конфигурации сервера &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Чтобы выполнить **sp_configure** с обоими параметрами для изменения параметра конфигурации или выполнения инструкции RECONFIGURE, необходимо обладать разрешением ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-listing-the-advanced-configuration-options"></a>A. Вывод списка дополнительных параметров конфигурации  
 В следующем примере демонстрируется, как установить и отобразить все параметры конфигурации. Дополнительные параметры конфигурации отображаются, если предварительно параметру `show advanced option` присвоить значение `1`. После изменения этого параметра выполнение хранимой процедуры `sp_configure` без аргументов выводит все параметры конфигурации.  
  
```sql  
USE master;  
GO  
EXEC sp_configure 'show advanced option', '1';  
```  
  
 Сообщение: "параметр конфигурации" Показывать дополнительные параметры "изменен с 0 на 1. Выполните инструкцию RECONFIGURE для установки.  
  
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
  
## <a name="examples-sspdw"></a>Примеры: [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-list-all-available-configuration-settings"></a>В. Список всех доступных параметров конфигурации.  
 В следующем примере демонстрируется, как создать список всех параметров конфигурации.  
  
```sql  
EXEC sp_configure;  
```  
  
 В результате возвращается имя параметра, за которым следуют его минимальное и максимальное значения. **Config_value** — это значение, которое [!INCLUDE[ssDW](../../includes/ssdw-md.md)] будет использоваться после завершения перенастройки. **run_value** — это значение, которое используется в настоящий момент. Значения **config_value** и **run_value** , как правило, совпадают, если не находятся в процессе изменения.  
  
### <a name="d-list-the-configuration-settings-for-one-configuration-name"></a>Г. Список параметров конфигурации для одного имени конфигурации.  
  
```sql  
EXEC sp_configure @configname='hadoop connectivity';  
```  
  
### <a name="e-set-hadoop-connectivity"></a>Д. Установка подключения к Hadoop.  
 Настройка подключения Hadoop требует выполнения еще нескольких действий в дополнение к запуску sp_configure. Полную процедуру см. в разделе [Создание внешнего источника данных &#40;&#41;Transact-SQL ](../../t-sql/statements/create-external-data-source-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys. Configurations &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-configurations-transact-sql.md)   
 [ИЗМЕНЕНИЕ конфигурации уровня базы данных &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-scoped-configuration-transact-sql.md)   
 [Архитектура Soft-NUMA (SQL Server)](../../database-engine/configure-windows/soft-numa-sql-server.md)  
  
  
