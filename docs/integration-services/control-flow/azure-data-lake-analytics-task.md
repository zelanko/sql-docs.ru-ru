---
title: Задача Azure Data Lake Analytics | Документация Майкрософт
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.component: control-flow
ms.reviewer: douglasl
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 395d790069294aed541f9756fa7caefbb62f9a7b
ms.sourcegitcommit: 44e9bf62f2c75449c17753ed66bf85c43928dbd5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/05/2018
ms.locfileid: "37854432"
---
# <a name="azure-data-lake-analytics-task"></a>Задача Azure Data Lake Analytics

Задача Azure Data Lake Analytics позволяет отправлять задания U-SQL в службу Azure Data Lake Analytics. [Azure Data Lake Analytics (ADLA)](https://azure.microsoft.com/services/data-lake-analytics/).

Задача Azure Data Lake Analytics входит в [пакет дополнительных компонентов SQL Server Integration Services (SSI) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

## <a name="configure-the-azure-data-lake-analytics-task"></a>Настройка задачи Azure Data Lake Analytics

Чтобы добавить в пакет задачу Azure Data Lake Analytics, перетащите ее с панели элементов SSI на панель холста конструктора. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите **Изменить**, чтобы открыть диалоговое окно **редактора задачи Azure Data Lake Analytics**. Свойства могут быть заданы с помощью конструктора SSIS или программным путем.

## <a name="general-page-configuration"></a>Конфигурация страницы "Общие"

Используйте страницу **Общие**, чтобы настроить задачу Data Lake Analytics и указать скрипт U-SQL, который отправляет эта задача. См. дополнительные сведения о [языке U-SQL](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference).

### <a name="basic-configuration"></a>Основная конфигурация

- **Имя** — задает имя задачи Azure Data Lake Analytics.
- **Описание** — задает описание задачи Azure Data Lake Analytics.

### <a name="u-sql-configuration"></a>Конфигурация U-SQL

Конфигурация U-SQL включает два типа параметров: **SourceType** и динамические параметры на основе значения **SourceType**. 

- **SourceType** — указывает источник скрипта U-SQL. Этот скрипт будет отправлен в учетную запись Azure Data Lake Analytics в процессе выполнения пакета SSI. Три возможных значения этого свойства приведены в следующей таблице.

|Значение|Описание|  
|-----------|-----------------|  
|**DirectInput**|Определяет скрипт U-SQL с использованием встроенного редактора. При выборе этого значения отображается динамический параметр **USQLStatement**.|  
|**FileConnection**|Указывает локальный USQL-файл, содержащий скрипт U-SQL. При выборе этого значения отображается динамический параметр **FileConnection**.|  
|**Переменная**|Указывает переменную SSI, содержащую скрипт U-SQL. При выборе этого значения отображается динамический параметр **SourceVariable**.|

- **SourceType Dynamic Options.** Указывает содержимое скрипта для запроса U-SQL. 

|Тип источника|Динамические параметры|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Введите отправляемый запрос U-SQL прямо в окно параметров или нажмите кнопку обзора (...), чтобы ввести запрос U-SQL в диалоговое окно **Ввод запроса U-SQL**.|  
|**SourceType = FileConnection**|Выберите существующий диспетчер подключений файлов или щелкните <**Новое подключение**>, чтобы создать подключение файла. **См. дополнительные сведения о** [диспетчере подключений файлов](../../integration-services/connection-manager/file-connection-manager.md) и [редакторе диспетчера подключений файлов](../../integration-services/connection-manager/file-connection-manager-editor.md).|  
|**SourceType = Variable**|Выберите существующую переменную или щелкните \<**Создать переменную...**>, чтобы создать ее. **См. дополнительные сведения о** [переменных Integration Services (SSI)](../../integration-services/integration-services-ssis-variables.md) и [добавлении переменных](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).|


### <a name="job-configuration"></a>Конфигурация задания
Конфигурация задания определяет свойства отправляемого задания U-SQL.

- **AzureDataLakeAnalyticsConnection** — указывает учетную запись Azure Data Lake Analytics, в которую будет отправлен скрипт U-SQL. Выберите соединение из списка определенных диспетчеров соединений. Чтобы создать новое подключение, выберите <**Новое подключение**>. См. дополнительные сведения о [диспетчере подключений Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md).

- **JobName** — указывает имя задания U-SQL. 
- **AnalyticsUnits** — содержит счетчик единиц использования аналитики для задания U-SQL.
- **Priority** — указывает приоритет для задания U-SQL. Допускаются значения в диапазоне от 0 до 1000, где меньшее число означает более высокий приоритет.
- **RuntimeVersion** — указывает версию среды выполнения Azure Data Lake Analytics для задания U-SQL. По умолчанию этот параметр имеет значение default. В большинстве случаев это свойство изменять не нужно.
- **Synchronous** — логическое значение, которое определяет, будет ли задача ожидать выполнения задания. Установите значение True, чтобы задача отмечалась как успешно выполненная после завершения задания. Установите значение False, чтобы задача отмечалась как успешно выполненная после перехода задания в состояние подготовки.

|Значение|Описание|
|-----------|-----------------|
|True|Результат задачи определяется по результату выполнения задания U-SQL. Если задание завершилось успешно, задача также завершается успешно. Если задание завершается сбоем, задача также завершается сбоем. В любом случае выполнение задачи прекращается.|
|False|Результат задачи определяется по результату отправки и подготовки задания U-SQL. Если задание успешно отправлено и проходит этап подготовки, задача завершается успешно. Если задание завершается сбоем на этапе отправки или подготовки, задача завершается сбоем. В любом случае выполнение задачи прекращается.|

- **TimeOut** — указывает время ожидания для выполнения задания (в секундах). По истечении времени ожидания задание будет отменено, а задача отмечена как завершившаяся сбоем. Свойство TimeOut недоступно, если Synchronous имеет значение False. Свойство TimeOut недоступно, если **Synchronous** имеет значение **False**.

## <a name="parameter-mapping-page-configuration"></a>Конфигурация страницы "Сопоставление параметров"

Используйте страницу **Сопоставление параметров** в диалоговом окне **Редактор задач Azure Data Lake Analytics**, чтобы сопоставить переменные с параметрами (переменными U-SQL) в скрипте U-SQL.

- **Имя переменной** — добавив сопоставление параметров, щелкните **Добавить** и выберите системную или пользовательскую переменную в списке или щелкните \<**Создать переменную**>, чтобы добавить новую переменную в диалоговом окне **Добавление переменной**. **См. также:** [Переменные в службах Integration Services](../../integration-services/integration-services-ssis-variables.md)  

- **Имя параметра** — укажите имя параметра или переменной в скрипте U-SQL. Имя параметра должно начинаться с символа @, например @Param1. 

Вот пример, демонстрирующий передачу параметров скрипту U-SQL.

**Пример скрипта U-SQL**
```
@searchlog =
    EXTRACT UserId          int,
            Start           DateTime,
            Region          string,
            Query           string,
            Duration        int,
            Urls            string,
            ClickedUrls     string
    FROM @in
    USING Extractors.Tsv(nullEscape:"#NULL#");

@rs1 =
    SELECT Start, Region, Duration
    FROM @searchlog
WHERE Region == "en-gb";

@rs1 =
    SELECT Start, Region, Duration
    FROM @rs1
    WHERE Start <= DateTime.Parse("2012/02/19");

OUTPUT @rs1   
    TO @out
      USING Outputters.Tsv(quoting:false, dateTimeFormat:null);
```

В примере выше пути ввода и вывода определены в параметрах **@in** и **@out**. Значения для параметров **@in** и **@out** в скрипте U-SQL передаются динамически, как настроено в конфигурации сопоставления параметров.

|Имя переменной|Имя параметра|
|-------------|--------------|
|User: Variable1|@in|
|User: Variable2|@out| 

## <a name="expression-page-configuration"></a>Конфигурация страницы "Выражения"

Все свойства в конфигурации страницы "Общие" можно назначить в качестве выражений свойств, чтобы организовать динамическое обновление свойств во время выполнения. **См. дополнительные сведения об** [использовании выражений свойств в пакетах](../../integration-services/expressions/use-property-expressions-in-packages.md)

## <a name="see-also"></a>См. также:
- [Диспетчер подключений Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Задача «Файловая система» для Azure Data Lake](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Диспетчер подключений Azure Data Lake Store](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

