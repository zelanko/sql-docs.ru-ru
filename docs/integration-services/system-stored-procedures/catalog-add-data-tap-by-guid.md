---
title: catalog.add_data_tap_by_guid | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: ed9d7fa3-61a1-4e21-ba43-1ead7dfc74eb
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 39d6e9d5fda554530f321e6887230812b6810ddc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="catalogadddatatapbyguid"></a>catalog.add_data_tap_by_guid
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
 [ @execution_id = ] *execution_id*  
 Идентификатор выполнения для выполнения, содержащего пакет. Параметр *execution_id* имеет тип **bigint**.  
  
 [ @dataflow_task_guid = ] *dataflow_task_guid*  
 Идентификатор задачи потока данных в пакете, который содержит путь потока данных для отвода. Параметр *dataflow_task_guid* имеет тип **uniqueidentifier**.  
  
 [ @dataflow_path_id_string = ] *dataflow_path_id_string*  
 Строка идентификации для пути потока данных. Путь соединяет два компонента потока данных. Свойство **IdentificationString** для пути определяет строку.  
  
 Чтобы найти строку идентификации, в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] щелкните правой кнопкой мыши путь между двумя компонентами потока данных, а затем выберите пункт **Свойства**. Свойство **IdentificationString** отображается в окне **Свойства**.  
  
 Параметр *dataflow_path_id_string* имеет тип **nvarchar(4000)**.  
  
 [ @data_filename = ] *data_filename*  
 Имя файла, в котором хранятся полученные данные. Если задача потока данных выполняется внутри контейнера «цикл по каждому элементу» или «цикл по элементам», то полученные данные для каждого прохода цикла хранятся в отдельных файлах. Каждому файлу добавляется префикс с номером, соответствующим итерации. Файлы отвода данных записываются в папку "*\<папка установки SQL Server>* \130\DTS\\". Параметр *data_filename* имеет тип **nvarchar(4000)**.  
  
 [ @max_rows = ] max_rows  
 Количество строк, полученных при отводе данных. Если это значение не задано, фиксируются все строки. Параметр max_rows имеет тип **int**.  
  
 [ @data_tap_id = ] *data_tap_id*  
 Идентификатор отвода данных. Параметр *data_tap_id* имеет тип **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере отвод данных создан в пути потока данных `Paths[SRC DimDCVentor.OLE DB Source Output]`, в задаче потока данных `{D978A2E4-E05D-4374-9B05-50178A8817E8}`. Полученные данные хранятся в файле DCVendorOutput.csv.  
  
```sql
exec catalog.add_data_tap_by_guid   @execution_id,   
'{D978A2E4-E05D-4374-9B05-50178A8817E8}',   
'Paths[SRC DimDCVentor.OLE DB Source Output]',   
'D:\demos\datafiles\DCVendorOutput.csv'  
```  
  
## <a name="remarks"></a>Remarks  
 Чтобы добавить отводы данных, экземпляр выполнения должен быть создан (значение 1 в столбце **status** представления [catalog.operations &#40;база данных SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)). Значения состояния изменяются после запуска выполнения. Выполнение можно создать путем вызова [catalog.create_execution &#40;база данных SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 Далее приведены замечания по использованию хранимой процедуры add_data_tap_by_guid.  
  
-   Добавленный отвод данных не проверяется перед запуском пакета.  
  
-   Рекомендуется ограничить число строк, полученных во время прослушивания данных, чтобы избежать формирования больших файлов данных. Если на компьютере, на котором выполняется хранимая процедура, не хватает места для хранения файлов данных, выполнение хранимой процедуры прекращается.  
  
-   Выполнение хранимой процедуры add_data_tap_by_guid влияет на производительность пакета. Поэтому рекомендуется запускать эту хранимую процедуру только для диагностики проблем с данными.  
  
-   Чтобы открыть файл, в котором хранятся отведенные данные, требуются разрешения администратора на том компьютере, где выполняется хранимая процедура, либо нужно быть пользователем, запустившим выполнение, которое содержит пакет с отводом данных.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY на экземпляр выполнения  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет разрешений MODIFY.  
  
-   Отвод данных для указанного компонента, в указанном пакете, уже был добавлен.  
  
-   Указано неправильное число получаемых строк.  
  
## <a name="requirements"></a>Требования  
  
## <a name="see-also"></a>См. также:  
 [catalog.add_data_tap](../../integration-services/system-stored-procedures/catalog-add-data-tap.md)  
  
  
