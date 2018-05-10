---
title: catalog.create_execution (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: 45d0c2f6-1f38-445f-ac06-e2a01f6ac600
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bb8d73d15fea799cc160920d5bbd92b903c21991
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="catalogcreateexecution-ssisdb-database"></a>catalog.create_execution (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Создает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
 Эта хранимая процедура использует уровень ведения журнала по умолчанию на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_execution [@folder_name = folder_name  
     , [@project_name =] project_name  
     , [@package_name =] package_name  
  [  , [@reference_id =] reference_id ]  
  [  , [@use32bitruntime =] use32bitruntime ] 
  [  , [@runinscaleout =] runinscaleout ]
  [  , [@useanyworker =] useanyworker ] 
     , [@execution_id =] execution_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [@folder_name =] *folder_name*  
 Имя папки, содержащей пакет, который необходимо выполнить. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [@project_name =] *project_name*  
 Имя проекта, содержащего пакет, который необходимо выполнить. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
 [@package_name =] *package_name*  
 Имя пакета, который необходимо выполнить. Параметр *package_name* имеет тип **nvarchar(260)**.  
  
 [@reference_id =] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является необязательным. Параметр *reference_id* имеет тип **bigint**.  
  
 [@use32bitruntime =] *use32bitruntime*  
 Указывает, должна ли использоваться 32-разрядная среда выполнения для запуска этого пакета в 64-разрядной операционной системе. Используйте значение 1, чтобы выполнить пакет в 32-разрядной среде выполнения при прогоне в 64-разрядной операционной системе. Используйте значение 0, чтобы выполнить пакет в 64-разрядной среде выполнения при прогоне в 64-разрядной операционной системе. Этот параметр является необязательным. Параметр *Use32bitruntime* имеет тип **bit**.  
 
 [@runinscaleout =] *runinscaleout*  
 Указывает, осуществляется ли выполнение в Scale Out. Используйте значение 1 для выполнения пакета в Scale Out. Используйте значение 0 для выполнения пакета вне Scale Out. Этот параметр является необязательным. Если этот параметр не указан, присваивается значение DEFAULT_EXECUTION_MODE в [SSISDB].[catalog].[catalog_properties]. Параметр *runinscaleout* имеет тип **bit**. 
 
[@useanyworker =] *useanyworker*  
Указывает, разрешено ли выполнение с помощью любой рабочей роли Scale Out.

-   Используйте значение 1 для выполнения пакета с помощью любой рабочей роли Scale Out. При задании `@useanyworker` значения "Истина" любая рабочая роль, максимальное количество задач которой (как указано в файле конфигурации рабочей роли) еще не достигнуто, может запускать пакет. Сведения о файле конфигурации рабочей роли см. в разделе [Рабочая роль масштабного развертывания служб Integration Services (SSIS)](../scale-out/integration-services-ssis-scale-out-worker.md).

-   Значение 0 указывает, что выполнение пакета с помощью любой рабочей роли Scale Out не разрешено. При задании `@useanyworker` значения "Ложь" вам нужно будет указать рабочие роли, которым разрешен запуск пакета, с помощью диспетчера Scale Out или вызова хранимой процедуры `[catalog].[add_execution_worker]`. Если указать рабочую роль, в которой уже запущен другой пакет, она завершает выполнение текущего пакета, прежде чем запросить другое выполнение.

Этот параметр является необязательным. Если параметр не задан, используется значение 1. Параметр *useanyworker* имеет тип **bit**. 
  
 [@execution_id =] *execution_id*  
 Возвращает уникальный идентификатор для экземпляра выполнения. Параметр *execution_id* имеет тип **bigint**.  

  
## <a name="remarks"></a>Remarks  
 Выполнение применяется для задания значений параметров, которые будут использоваться пакетом во время выполнения одного экземпляра пакета.  
  
 Если ссылка на среду задается параметром *reference_id*, хранимая процедура заполняет параметры проекта и пакета литеральными значениями или ссылочными значениями из соответствующих переменных среды. Если указана ссылка на среду, при выполнении пакета используются значения параметров по умолчанию. Чтобы определить, какие именно значения используются в конкретном экземпляре выполнения, воспользуйтесь значением выходного параметра *execution_id* из этой хранимой процедуры и выполните запрос к представлению [execution_parameter_values](../../integration-services/system-views/catalog-execution-parameter-values-ssisdb-database.md).  
  
 В выполнении могут указываться только пакеты, отмеченные как пакеты точек входа. В случае указания пакета, который не является пакетом точки входа, происходит сбой выполнения.  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется вызов catalog.create_execution для создания экземпляра выполнения пакета Child1.dtsx, не входящего в Scale Out. Проект Project1 служб Integration Services содержит пакет. В этом примере выполняется вызов catalog.set_execution_parameter_value для задания значений для параметров Parameter1, Parameter2 и LOGGING_LEVEL. В этом примере выполняется вызов catalog.start_execution для запуска экземпляра выполнения.  
  
```sql  
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
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешения READ и EXECUTE на проект, а также, если применимо, разрешение READ на среду, указанную в ссылке  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  

 Если параметр @runinscaleout имеет значение 1, эта хранимая процедура требует применения одного из следующих разрешений:
 
-   Членство в роли базы данных **ssis_admin**

-   Членство в роли базы данных **ssis_cluster_executor**

-   Членство в роли сервера **sysadmin**
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пакет не существует.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Ссылка на среду *reference_id* недопустима.  
  
-   Указанный пакет не является пакетом точки входа.  
  
-   Тип данных в переменной среды, на которую указывает ссылка, отличается от типа данных параметра проекта или пакета.  
  
-   Проект или пакет содержит параметры, которым требуются значения, но значения не назначены.  
  
-   Переменные среды, на которые имеется ссылка, не найдены в среде, указанной ссылкой *reference_id*.  
  
## <a name="see-also"></a>См. также:  
 [catalog.start_execution (база данных)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)   
 [catalog.set_execution_parameter_value (база данных SSISDB)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
 [catalog.add_execution_worker (база данных)](../../integration-services/system-stored-procedures/catalog-add-execution-worker-ssisdb-database.md)  
  
