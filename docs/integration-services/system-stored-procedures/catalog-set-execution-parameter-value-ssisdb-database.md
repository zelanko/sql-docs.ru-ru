---
title: "Catalog.set_execution_parameter_value (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 055d86c9-befd-4e63-acb1-6dfe833549d2
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 7b13e7b1c28bad6e573e829183372da4bb62f92d
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogsetexecutionparametervalue-ssisdb-database"></a>catalog.set_execution_parameter_value (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает значение параметра для экземпляра выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Значение параметра нельзя изменить после запуска выполнения экземпляра.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_execution_parameter_value [ @execution_id = execution_id  
    , [ @object_type = ] object_type  
    , [ @parameter_name = ] parameter_name  
    , [ @parameter_value = ] parameter_value  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. *Execution_id* — **bigint**.  
  
 [ @object_type =] *object_type*  
 Тип параметра.  
  
 Следующие параметры, задать *object_type* до 50  
  
-   LOGGING_LEVEL  
  
-   CUSTOMIZED_LOGGING_LEVEL  
  
-   DUMP_ON_ERROR  
  
-   DUMP_ON_EVENT  
  
-   DUMP_EVENT_CODE  
  
-   CALLER_INFO  
  
-   SYNCHRONIZED  
  
 Значение `20` указывает параметр проекта, значение `30` — параметр пакета.  
  
 *Object_type* — **smallint**.  
  
 [ @parameter_name =] *parameter_name*  
 Имя параметра. *Parameter_name* — **nvarchar(128)**.  
  
 [ @parameter_value =] *parameter_value*  
 Значение параметра. *Parameter_value* — **sql_variant**.  
  
## <a name="remarks"></a>Замечания  
 Чтобы выяснить значения параметров, использованные в ходе данного выполнения, выполните запрос к представлению catalog.execution_parameter_values.  
  
 Чтобы задать объем сведений, который регистрируется во время выполнения пакета, установите *parameter_name* LOGGING_LEVEL и установите *parameter_value* одно из следующих значений.  
  
 Задать *object_type* параметра до 50.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Нет<br /><br /> Ведение журнала выключено. Регистрируется только состояние выполнения пакета.|  
|1|Basic<br /><br /> Записываются все события, за исключением пользовательских и диагностических событий. Это значение по умолчанию.|  
|2|Производительность<br /><br /> Регистрируются только статистика производительности, а также события OnError и OnWarning.|  
|3|Подробно<br /><br /> Регистрируются все события, в том числе пользовательские и диагностические события. <br />К пользовательским относятся события, записываемые задачами служб Integration Services. Дополнительные сведения см. в разделе [пользовательские сообщения для ведения журнала](../../integration-services/performance/integration-services-ssis-logging.md#custom_messages)|  
|4|Среда выполнения журнала обращений и преобразований<br /><br /> Собирает данные, необходимые для отслеживания журнала обращений и преобразований в потоке данных.|  
|100|Настраиваемый уровень ведения журнала<br /><br /> Укажите параметры в параметре CUSTOMIZED_LOGGING_LEVEL. Дополнительные сведения о значениях, которые можно указать в разделе [catalog.create_customized_logging_level](../../integration-services/system-stored-procedures/catalog-create-customized-logging-level.md).<br /><br /> Дополнительные сведения о пользовательских уровней ведения журнала см. в разделе [Enable Logging for Package Execution on the SSIS Server](../../integration-services/performance/integration-services-ssis-logging.md#server_logging).|  
  
 Чтобы указать, что сервер служб Integration Services создает файлы дампа при возникновении любой ошибки в ходе выполнения пакета, установите следующие значения параметров для экземпляра выполнения, который не запускался.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*имя_параметра*|‘DUMP_ON_ERROR|  
|*parameter_value*|1|  
  
 Чтобы указать, что сервер служб Integration Services создает файлы дампа при возникновении событий в ходе выполнения пакета, установите следующие значения параметров для экземпляра выполнения, который не запускался.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*имя_параметра*|‘DUMP_ON_EVENT|  
|*parameter_value*|1|  
  
 Чтобы указать события в ходе выполнения пакета, в результате которых сервер служб Integration Services создает файлы дампа, установите следующие значения параметров для экземпляра выполнения, который не запускался. Разделите несколько кодов событий, используя точку с запятой.  
  
|Параметр|Значение|  
|---------------|-----------|  
|*execution_id*|Уникальный идентификатор для экземпляра выполнения|  
|*object_type*|50|  
|*имя_параметра*|DUMP_EVENT_CODE|  
|*parameter_value*|Один или несколько кодов событий|  
  
## <a name="example"></a>Пример  
 В следующем примере задано, что сервер служб Integration Services создает файлы дампа при возникновении любой ошибки в ходе выполнения пакета.  
  
```sql
exec catalog.create_execution  'TR2','Recurring ETL', 'Dim_DCVendor.dtsx',NULL, 0,@execution_id out  
exec catalog.set_execution_parameter_value  @execution_id, 50, 'DUMP_ON_ERROR',1  
```  
  
## <a name="example"></a>Пример  
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
 Нет  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и MODIFY на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор выполнения  
  
-   Имя параметра недопустимо  
  
-   Тип данных значения параметра не соответствует типу данных параметра  
  
## <a name="see-also"></a>См. также:  
 [Catalog.execution_parameter_values &#40; База данных SSISDB &#41;](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md)   
 [Создание файлов дампа для выполнения пакетов](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  

