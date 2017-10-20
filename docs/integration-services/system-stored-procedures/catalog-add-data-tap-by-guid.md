---
title: "Catalog.add_data_tap_by_guid | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ed9d7fa3-61a1-4e21-ba43-1ead7dfc74eb
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9bd4ecb4a6a419f1965a349d46d16d764dd83708
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatapbyguid"></a>catalog.add_data_tap_by_guid
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет отвод данных к определенному пути потока данных в потоке данных пакета для экземпляра выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog add_data_tap_by_guid [ @execution_id = ] execution_id  
, [ @dataflow_task_guid = ] dataflow_task_guid   
, [ @dataflow_path_id_string = ] dataflow_path_id_string  
, [ @data_filename = ] data_filename  
, [ @max_rows = ] max_rows  
, [ @data_tap_id = ] data_tap_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Идентификатор выполнения для выполнения, содержащего пакет. *Execution_id* — **bigint**.  
  
 [ @dataflow_task_guid =] *dataflow_task_guid*  
 Идентификатор задачи потока данных в пакете, который содержит путь потока данных для отвода. *Dataflow_task_guid* —**uniqueidentifier**.  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 Строка идентификации для пути потока данных. Путь соединяет два компонента потока данных. **IdentificationString** для пути определяет строку.  
  
 Чтобы найти строку идентификации, в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] щелкните правой кнопкой мыши путь между двумя компонентами потока данных, а затем нажмите кнопку **свойства**. **IdentificationString** свойство появляется в **свойства** окна.  
  
 *Dataflow_path_id_string* — **nvarchar(4000)**.  
  
 [ @data_filename =] *data_filename*  
 Имя файла, в котором хранятся полученные данные. Если задача потока данных выполняется внутри контейнера «цикл по каждому элементу» или «цикл по элементам», то полученные данные для каждого прохода цикла хранятся в отдельных файлах. Каждому файлу добавляется префикс с номером, соответствующим итерации. Файлы отвода данных записываются в папку «*\<папку установки SQL Server >*\130\DTS\\». *Data_filename* — **nvarchar(4000)**.  
  
 [ @max_rows =] max_rows  
 Количество строк, полученных при отводе данных. Если это значение не задано, фиксируются все строки. Параметр max_rows имеет **int**.  
  
 [ @data_tap_id =] *data_tap_id*  
 Идентификатор отвода данных. *Data_tap_id* — **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере отвод данных создается на пути потока данных, `Paths[SRC DimDCVentor.OLE DB Source Output]`в задаче потока данных `{D978A2E4-E05D-4374-9B05-50178A8817E8}`. Полученные данные хранятся в файле DCVendorOutput.csv.  
  
```sql
exec catalog.add_data_tap_by_guid   @execution_id,   
'{D978A2E4-E05D-4374-9B05-50178A8817E8}',   
'Paths[SRC DimDCVentor.OLE DB Source Output]',   
'D:\demos\datafiles\DCVendorOutput.csv'  
```  
  
## <a name="remarks"></a>Замечания  
 Чтобы добавить отводы данных, экземпляр выполнения должен быть создан (значение 1 в **состояние** столбец [catalog.operations &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)представления). Значения состояния изменяются после запуска выполнения. Выполнение можно создать путем вызова [catalog.create_execution &#40; База данных SSISDB &#41; ](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 Далее приведены замечания по использованию хранимой процедуры add_data_tap_by_guid.  
  
-   Добавленный отвод данных не проверяется перед запуском пакета.  
  
-   Рекомендуется ограничить число строк, полученных во время прослушивания данных, чтобы избежать формирования больших файлов данных. Если на компьютере, на котором выполняется хранимая процедура, не хватает места для хранения файлов данных, выполнение хранимой процедуры прекращается.  
  
-   Выполнение хранимой процедуры add_data_tap_by_guid влияет на производительность пакета. Поэтому рекомендуется запускать эту хранимую процедуру только для диагностики проблем с данными.  
  
-   Чтобы открыть файл, в котором хранятся отведенные данные, требуются разрешения администратора на том компьютере, где выполняется хранимая процедура, либо нужно быть пользователем, запустившим выполнение, которое содержит пакет с отводом данных.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY на экземпляр выполнения  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет разрешений MODIFY.  
  
-   Отвод данных для указанного компонента, в указанном пакете, уже был добавлен.  
  
-   Указано неправильное число получаемых строк.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также:  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
  
  
