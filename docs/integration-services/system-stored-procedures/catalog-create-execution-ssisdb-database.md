---
title: "Catalog.create_execution (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 45d0c2f6-1f38-445f-ac06-e2a01f6ac600
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95c07e2550330ff9a2ac1cc70107d11147ae53dd
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="catalogcreateexecution-ssisdb-database"></a>catalog.create_execution (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Создает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Эта хранимая процедура использует уровень ведения журнала по умолчанию на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
create_execution [ @folder_name = folder_name  
     , [ @project_name = ] project_name  
     , [ @package_name = ] package_name  
  [  , [ @reference_id = ] reference_id ]  
  [  , [ @use32bitruntime = ] use32bitruntime ] 
  [  , [ @runinscaleout = ] runinscaleout ]
  [  , [ @useanyworker = ] useanyworker ] 
     , [ @execution_id = ] execution_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, содержащей пакет, который необходимо выполнить. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя проекта, содержащего пакет, который необходимо выполнить. *Project_name* — **nvarchar(128)**.  
  
 [ @package_name =] *имя_пакета*  
 Имя пакета, который необходимо выполнить. *Имя_пакета* — **nvarchar(260)**.  
  
 [ @reference_id =] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является необязательным. *Reference_id* — **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Указывает, должна ли использоваться 32-разрядная среда выполнения для запуска этого пакета в 64-разрядной операционной системе. Используйте значение 1 для запуска пакета в 32-разрядной средой выполнения при запуске в 64-разрядной операционной системе. Используйте значение 0, чтобы выполнить пакет в 64-разрядной среде выполнения при прогоне в 64-разрядной операционной системе. Этот параметр является необязательным. *Use32bitruntime* — **бит**.  
 
 [ @runinscaleout =] *runinscaleout*  
 Укажите, является ли выполнение в масштабное развертывание. Используйте значение 1 для выполнения пакета в масштабное развертывание. Используйте значение 0 для выполнения пакета без масштабное развертывание. Этот параметр является необязательным. Ему присваивается DEFAULT_EXECUTION_MODE в [SSISDB]. [catalog]. [catalog_properties], если не указан. *Runinscaleout* — **бит**. 
 
 [ @useanyworker =] *useanyworker*  
  Указывает, разрешено ли рабочие Out шкалы для выполнения. Используйте значение 1 для выполнения пакета с любого масштаба Out работника. Используйте значение 0, чтобы показать, что не все ожидания работников для масштабирования для выполнения пакета. Этот параметр является необязательным. Оно присвоено значение 1, если не указано. *Useanyworker* — **бит**. 
  
 [ @execution_id =] *execution_id*  
 Возвращает уникальный идентификатор для экземпляра выполнения. *Execution_id* — **bigint**.  

  
## <a name="remarks"></a>Замечания  
 Выполнение применяется для задания значений параметров, которые будут использоваться пакетом во время выполнения одного экземпляра пакета.  
  
 Если указано ссылку на среду с *reference_id* параметра, хранимая процедура заполняет параметры проекта и пакета литеральными значениями или ссылочными значениями из соответствующих переменных среды. Если указана ссылка на среду, при выполнении пакета используются значения параметров по умолчанию. Чтобы определить точно значения, которые используются в определенном экземпляре выполнения, используйте *execution_id* значение выходного параметра из этой хранимой процедуры и запроса [execution_parameter_values](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md) представления.  
  
 В выполнении могут указываться только пакеты, отмеченные как пакеты точек входа. В случае указания пакета, который не является пакетом точки входа, происходит сбой выполнения.  
  
## <a name="example"></a>Пример  
 В следующем примере вызов catalog.create_execution для создания экземпляра выполнения пакета Child1.dtsx, который не находится в масштабное развертывание. Проект Project1 служб Integration Services содержит пакет. В этом примере выполняется вызов catalog.set_execution_parameter_value для задания значений для параметров Parameter1, Parameter2 и LOGGING_LEVEL. В этом примере выполняется вызов catalog.start_execution для запуска экземпляра выполнения.  
  
```  
Declare @execution_id bigint  
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Child1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'TestDeply4', @project_name=N'Integration Services Project1', @use32bitruntime=False, @reference_id=Null  
Select @execution_id  
DECLARE @var0 sql_variant = N'Child1.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter1', @parameter_value=@var0  
DECLARE @var1 sql_variant = N'Child2.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter2', @parameter_value=@var1  
DECLARE @var2 smallint = 1  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var2  
EXEC [SSISDB].[catalog].[start_execution] @execution_id  
GO  
  
```  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и EXECUTE на проект, а также, если применимо, разрешение READ на среду, указанную в ссылке  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  

 Если @runinscaleout имеет значение 1, хранимая процедура требует один из следующих разрешений:
 
-   Членство в **ssis_admin** роли базы данных

-   Членство в **ssis_cluster_executor** роли базы данных

-   Членство в **sysadmin** роли сервера
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пакет не существует.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Ссылки на среду *reference_id*, является недопустимым.  
  
-   Указанный пакет не является пакетом точки входа.  
  
-   Тип данных в переменной среды, на которую указывает ссылка, отличается от типа данных параметра проекта или пакета.  
  
-   Проект или пакет содержит параметры, которым требуются значения, но значения не назначены.  
  
-   Не удается найти переменные среды, на которые имеются ссылки в среде, указанной ссылкой, *reference_id*, указывает.  
  
## <a name="see-also"></a>См. также:  
 [Catalog.start_execution &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)   
 [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [Catalog.add_execution_worker &#40; База данных SSISDB &#41;](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)  
  

