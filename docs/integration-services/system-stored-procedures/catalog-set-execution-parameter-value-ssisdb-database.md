---
description: catalog.set_execution_parameter_value (база данных SSISDB)
title: catalog.set_execution_parameter_value (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 055d86c9-befd-4e63-acb1-6dfe833549d2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5775b87b13fc126907dfc0f121e9838c2d490fd0
ms.sourcegitcommit: 192f6a99e19e66f0f817fdb1977f564b2aaa133b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/25/2020
ms.locfileid: "96129663"
---
# <a name="catalogset_execution_parameter_value-ssisdb-database"></a>catalog.set_execution_parameter_value (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Задает значение параметра для экземпляра выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Значение параметра нельзя изменить после запуска выполнения экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_execution_parameter_value [ @execution_id = execution_id  
    , [ @object_type = ] object_type  
    , [ @parameter_name = ] parameter_name  
    , [ @parameter_value = ] parameter_value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id = ] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. Параметр *execution_id* имеет тип **bigint**.  
  
 [ @object_type = ] *object_type*  
 Тип параметра.  
  
 Для следующих параметров установите *object_type* в значение 50  
  
-   LOGGING_LEVEL  
  
-   CUSTOMIZED_LOGGING_LEVEL  
  
-   DUMP_ON_ERROR  
  
-   DUMP_ON_EVENT  
  
-   DUMP_EVENT_CODE  
  
-   CALLER_INFO  
  
-   SYNCHRONIZED  
  
 Значение `20` указывает параметр проекта, значение `30` — параметр пакета.  
  
 Параметр *object_type* имеет тип **smallint**.  
  
 [ @parameter_name = ] *parameter_name*  
 Имя параметра. Параметр *parameter_name* имеет тип **nvarchar(128)**.  
  
 [ @parameter_value = ] *parameter_value*  
 Значение параметра. Параметр *parameter_value* имеет тип **sql_variant**.  
  
## <a name="remarks"></a>Комментарии  
 Чтобы выяснить значения параметров, использованные в ходе данного выполнения, выполните запрос к представлению catalog.execution_parameter_values.  
  
 Чтобы задать диапазон информации, регистрируемой в ходе выполнения пакета, присвойте параметру *parameter_name* значение LOGGING_LEVEL, а параметру *parameter_value* — одно из указанных ниже значений.  
  
 Присвойте параметру *object_type* значение 50.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|None<br /><br /> Ведение журнала выключено. Регистрируется только состояние выполнения пакета.|  
|1|Basic<br /><br /> Записываются все события, за исключением пользовательских и диагностических событий. Это значение по умолчанию.|  
|2|Производительность<br /><br /> Регистрируются только статистика производительности, а также события OnError и OnWarning.|  
|3|Подробный<br /><br /> Регистрируются все события, в том числе пользовательские и диагностические события. <br />К пользовательским относятся события, записываемые задачами служб Integration Services. Дополнительные сведения см. в разделе [Пользовательские сообщения для ведения журнала](../../integration-services/performance/integration-services-ssis-logging.md#custom_messages).|  
|4|Журнал преобразований в среде выполнения<br /><br /> Собирает данные, необходимые для отслеживания журнала преобразований в потоке данных.|  
|100|Пользовательский уровень ведения журнала<br /><br /> Укажите значения в параметре CUSTOMIZED_LOGGING_LEVEL. Дополнительные сведения о возможных значениях см. в разделе [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).<br /><br /> Дополнительные сведения о настраиваемых уровнях ведения журнала см. в разделе [Включение ведения журналов при выполнении пакета на сервере служб SSIS](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).|  
  
 Чтобы указать, что сервер служб Integration Services создает файлы дампа при возникновении любой ошибки в ходе выполнения пакета, установите следующие значения параметров для экземпляра выполнения, который не запускался.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*parameter_name*|'DUMP_ON_ERROR|  
|*parameter_value*|1|  
  
 Чтобы указать, что сервер служб Integration Services создает файлы дампа при возникновении событий в ходе выполнения пакета, установите следующие значения параметров для экземпляра выполнения, который не запускался.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*parameter_name*|'DUMP_ON_EVENT|  
|*parameter_value*|1|  
  
 Чтобы указать события в ходе выполнения пакета, в результате которых сервер служб Integration Services создает файлы дампа, установите следующие значения параметров для экземпляра выполнения, который не запускался. Разделите несколько кодов событий, используя точку с запятой.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*parameter_name*|DUMP_EVENT_CODE|  
|*parameter_value*|Один или несколько кодов событий|  
  
## <a name="examples"></a>Примеры  

### <a name="a-generate-dump-files-for-errors"></a>A. Создание файлов дампа для ошибок

 В следующем примере задано, что сервер служб Integration Services создает файлы дампа при возникновении любой ошибки в ходе выполнения пакета.  
  
```sql
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_ERROR',1  
```  
  
### <a name="b-generate-dump-files-for-events"></a>Б. Создание файлов дампа для событий

 В следующем примере задано, что сервер служб Integration Services создает файлы дампа при возникновении событий в ходе выполнения пакета, и указано событие, в результате которого сервер создает файлы.  
  
```sql
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_EVENT',1  
  
declare @event_code nvarchar(50)  
set @event_code = '0xC020801C'  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_EVENT_CODE', @event_code  
```  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и MODIFY на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор выполнения  
  
-   Имя параметра недопустимо  
  
-   Тип данных значения параметра не соответствует типу данных параметра  
  
## <a name="see-also"></a>См. также  
 [catalog.execution_parameter_values (база данных SSISDB)](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)   
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
