---
title: "Catalog.add_data_tap | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a25ebcc7-535e-4619-adf6-4e2b5a62ba37
caps.latest.revision: 23
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 686b40e7e1ad7f7843bee5af3295fdf394538f63
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogadddatatap"></a>catalog.add_data_tap
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Добавляет отвод данных на выходе компонента в потоке данных пакета для экземпляра выполнения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
add_data_tap [ @execution_id = ] execution_id  
[ @task_package_path = ] task_package_path  
[ @dataflow_path_id_string = ] dataflow_path_id_string  
[ @data_filename = ] data_filename  
[ @max_rows = ] max_rows  
[ @data_tap_id = ] data_tap_id  
OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Идентификатор выполнения для выполнения, содержащего пакет. *Execution_id* — **bigint**.  
  
 [ @task_package_path =] *task_package_path*  
 Путь пакета для задачи потока данных. **PackagePath** путь свойства для задачи потока данных. Путь учитывает регистр. Чтобы найти путь к пакету в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] правой кнопкой мыши задачу потока данных затем **свойства**. **PackagePath** свойство появляется в **свойства** окна.  
  
 *Task_package_path* — **nvarchar(max)**.  
  
 [ @dataflow_path_id_string =] *dataflow_path_id_string*  
 Строка идентификации для пути потока данных. Путь соединяет два компонента потока данных. **IdentificationString** для пути определяет строку.  
  
 Чтобы найти строку идентификации, в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] щелкните правой кнопкой мыши путь между двумя компонентами потока данных, а затем нажмите кнопку **свойства**. **IdentificationString** свойство появляется в **свойства** окна.  
  
 *Dataflow_path_id_string* — **nvarchar(4000)**.  
  
 [ @data_filename =] *data_filename*  
 Имя файла, в котором хранятся полученные данные. Если задача потока данных выполняется внутри контейнера «цикл по каждому элементу» или «цикл по элементам», то полученные данные для каждого прохода цикла хранятся в отдельных файлах. Каждому файлу добавляется префикс с номером, соответствующим итерации.  
  
 По умолчанию файл хранится в \< *диск*>: папка \Program Files\Microsoft SQL Server\130\DTS\DataDumps.  
  
 *Data_filename* — **nvarchar(4000)**.  
  
 [ @max_rows =] *max_rows*  
 Количество строк, полученных при отводе данных. Если это значение не задано, фиксируются все строки. *Max_rows* — **int**.  
  
 [ @data_tap_id =] *data_tap_id*  
 Возвращает идентификатор отвода данных. *Data_tap_id* — **bigint**.  
  
## <a name="example"></a>Пример  
 В следующем примере отвод данных создается в пути потока данных `'Paths[OLE DB Source.OLE DB Source Output]`, в задаче потока данных `\Package\Data Flow Task`. Полученные данные хранятся в `output0.txt` файл в папке DataDumps (\<*диск*>: \Program Files\Microsoft SQL Server\130\DTS\DataDumps).  
  
```  
Declare @execution_id bigint  
Exec SSISDB.Catalog.create_execution @folder_name='Packages',@project_name='SSISPackages', @package_name='Package.dtsx',@reference_id=Null, @use32bitruntime=False, @execution_id=@execution_id OUTPUT  
  
Exec SSISDB.Catalog.set_execution_parameter_value @execution_id,50, 'LOGGING_LEVEL', 0  
  
Exec SSISDB.Catalog.add_data_tap @execution_id, @task_package_path='\Package\Data Flow Task', @dataflow_path_id_string = 'Paths[OLE DB Source.OLE DB Source Output]', @data_filename = 'output0.txt'  
  
Exec SSISDB.Catalog.start_execution @execution_id  
  
```  
  
## <a name="remarks"></a>Замечания  
 Чтобы добавить отводы данных, экземпляр выполнения должен быть создан (значение 1 в **состояние** столбец [catalog.operations &#40; База данных SSISDB &#41; ](../../integration-services/system-views/catalog-operations-ssisdb-database.md)представления). Значения состояния изменяются после запуска выполнения. Выполнение можно создать путем вызова [catalog.create_execution &#40; База данных SSISDB &#41; ](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md).  
  
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
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [службы SSIS 2012: взгляд на отвод данных](http://go.microsoft.com/fwlink/?LinkId=239983), на сайте rafael-salas.com.  
  
## <a name="see-also"></a>См. также:  
 [catalog.add_data_tap_by_guid](../../integration-services/system-stored-procedures/catalog-add-data-tap-by-guid.md)  
  
  
