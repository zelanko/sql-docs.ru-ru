---
title: catalog.add_data_tap | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: a25ebcc7-535e-4619-adf6-4e2b5a62ba37
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 4d9c2725fbb4e237e065a7cfdd7c79ffe83d968a
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51642121"
---
# <a name="catalogadddatatap"></a>catalog.add_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет отвод данных на выходе компонента в потоке данных пакета для экземпляра выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.add_data_tap [ @execution_id = ] execution_id  
, [ @task_package_path = ] task_package_path  
, [ @dataflow_path_id_string = ] dataflow_path_id_string  
, [ @data_filename = ] data_filename  
, [ @max_rows = ] max_rows  
, [ @data_tap_id = ] data_tap_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id = ] *execution_id*  
 Идентификатор выполнения для выполнения, содержащего пакет. Параметр *execution_id* имеет тип **bigint**.  
  
 [ @task_package_path = ] *task_package_path*  
 Путь пакета для задачи потока данных. Свойство **PackagePath** задает путь для задачи потока данных. Путь учитывает регистр. Чтобы найти путь к пакету, в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] щелкните правой кнопкой мыши задачу "Поток данных", а затем выберите пункт **Свойства**. Свойство **PackagePath** отображается в окне **Свойства**.  
  
 Параметр *task_package_path* имеет тип **nvarchar(max)**.  
  
 [ @dataflow_path_id_string = ] *dataflow_path_id_string*  
 Строка идентификации для пути потока данных. Путь соединяет два компонента потока данных. Свойство **IdentificationString** для пути определяет строку.  
  
 Чтобы найти строку идентификации, в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] щелкните правой кнопкой мыши путь между двумя компонентами потока данных, а затем выберите пункт **Свойства**. Свойство **IdentificationString** отображается в окне **Свойства**.  
  
 Параметр *dataflow_path_id_string* имеет тип **nvarchar(4000)**.  
  
 [ @data_filename = ] *data_filename*  
 Имя файла, в котором хранятся полученные данные. Если задача потока данных выполняется внутри контейнера «цикл по каждому элементу» или «цикл по элементам», то полученные данные для каждого прохода цикла хранятся в отдельных файлах. Каждому файлу добавляется префикс с номером, соответствующим итерации.  
  
 По умолчанию файл хранится в папке \<*диск*>:\Program Files\Microsoft SQL Server\130\DTS\DataDumps.  
  
 Параметр *data_filename* имеет тип **nvarchar(4000)**.  
  
 [ @max_rows = ] *max_rows*  
 Количество строк, полученных при отводе данных. Если это значение не задано, фиксируются все строки. Параметр *max_rows* имеет тип **int**.  
  
 [ @data_tap_id = ] *data_tap_id*  
 Возвращает идентификатор отвода данных. Параметр *data_tap_id* имеет тип **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере отвод данных создается в пути потока данных `'Paths[OLE DB Source.OLE DB Source Output]`, в задаче потока данных `\Package\Data Flow Task`. Полученные данные сохраняются в файл `output0.txt` в папке DataDumps (\<*диск*>:\Program Files\Microsoft SQL Server\130\DTS\DataDumps).  
  
```sql
Declare @execution_id bigint  
Exec SSISDB.Catalog.create_execution @folder_name='Packages',@project_name='SSISPackages', @package_name='Package.dtsx',@reference_id=Null, @use32bitruntime=False, @execution_id=@execution_id OUTPUT  
  
Exec SSISDB.Catalog.set_execution_parameter_value @execution_id,50, 'LOGGING_LEVEL', 0  
  
Exec SSISDB.Catalog.add_data_tap @execution_id, @task_package_path='\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[OLE DB Source.OLE DB Source Output]', @data_filename = 'output0.txt'  
  
Exec SSISDB.Catalog.start_execution @execution_id  
```  
  
## <a name="remarks"></a>Remarks  
 Чтобы добавить отводы данных, экземпляр выполнения должен быть создан (значение 1 в столбце **status** представления [catalog.operations &#40;база данных SSISDB&#41;](../../integration-services/system-views/catalog-operations-ssisdb-database.md)). Значения состояния изменяются после запуска выполнения. Выполнение можно создать путем вызова [catalog.create_execution &#40;база данных SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
 Ниже приведены замечания по использованию хранимой процедуры add_data_tap.  
  
-   Если выполнение содержит родительский пакет и один или более дочерних пакетов, необходимо добавить отвод данных для каждого пакета, для которого нужно отводить данные.  
  
-   Если пакет содержит более одной задачи потока данных с одинаковым именем, task_package_path уникально определяет задачу потока данных, которая содержит отводимый выход компонента.  
  
-   Добавленный отвод данных не проверяется перед запуском пакета.  
  
-   Рекомендуется ограничить число строк, полученных во время прослушивания данных, чтобы избежать формирования больших файлов данных. Если на компьютере, на котором выполняется хранимая процедура, не хватает места для хранения файлов данных, выполнение пакета прекращается и в журнал записывается сообщение об ошибке.  
  
-   Запуск хранимой процедуры add_data_tap влияет на производительность пакета. Поэтому рекомендуется запускать эту хранимую процедуру только для диагностики проблем с данными.  
  
-   Для доступа к файлу, в котором хранятся полученные данные, необходимо иметь права администратора на компьютере, на котором запускается хранимая процедура. Вы также должны быть пользователем, запустившим выполнение, содержащее пакет с отводом данных.  
  
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
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись [Службы SSIS 2012. Взгляд на отвод данных](https://go.microsoft.com/fwlink/?LinkId=239983) в блоге rafael-salas.com.  
  
## <a name="see-also"></a>См. также:  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
