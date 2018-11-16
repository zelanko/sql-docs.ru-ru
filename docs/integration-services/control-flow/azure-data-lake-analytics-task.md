---
title: Задача Azure Data Lake Analytics | Документация Майкрософт
description: Вы можете отправлять задания U-SQL в службу Azure Data Lake Analytics с помощью задачи Data Lake Analytics.
ms.custom: ''
ms.date: 05/18/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: douglasl
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPADLSTASK.F1
- SQL14.DTS.DESIGNER.AFPADLSTASK.F1
author: yanancai
ms.author: yanacai
manager: craigg
ms.openlocfilehash: 3060dd1fa3a46f64b34658a1c8ebccbc4155526c
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641751"
---
# <a name="azure-data-lake-analytics-task"></a>Задача Azure Data Lake Analytics

Вы можете отправлять задания U-SQL в службу Azure Data Lake Analytics с помощью задачи Data Lake Analytics. Эта задача включена в [пакет дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

См. общие сведения об [Azure Data Lake Analytics](https://azure.microsoft.com/services/data-lake-analytics/).

## <a name="configure-the-task"></a>Настройка задачи

Чтобы добавить в пакет задачу Data Lake Analytics, перетащите ее с панели элементов SSIS на панель холста конструктора. Затем дважды щелкните задачу или щелкните ее правой кнопкой мыши и выберите **Изменить**. Откроется диалоговое окно **редактора задач Azure Data Lake Analytics**. Свойства можно задать с помощью конструктора SSIS или программным путем.

## <a name="general-page-configuration"></a>Конфигурация страницы "Общие"

Используйте страницу **Общие**, чтобы настроить задачу и указать скрипт U-SQL, который отправляет эта задача. См. дополнительные сведения о [языке U-SQL](https://msdn.microsoft.com/azure/data-lake-analytics/u-sql/u-sql-language-reference).

### <a name="basic-configuration"></a>Основная конфигурация

Задайте имя и описание задачи.

### <a name="u-sql-configuration"></a>Конфигурация U-SQL

Конфигурация U-SQL включает два типа параметров: **SourceType** и динамические параметры на основе значения **SourceType**. 

**SourceType** — указывает источник скрипта U-SQL. Этот скрипт отправляется в учетную запись Data Lake Analytics в процессе выполнения пакета SSI. Доступны следующие параметры для этого свойства:

|Значение|Описание|  
|-----------|-----------------|  
|**DirectInput**|Определяет скрипт U-SQL с использованием встроенного редактора. При выборе этого значения отображается динамический параметр **USQLStatement**.|  
|**FileConnection**|Указывает локальный USQL-файл, содержащий скрипт U-SQL. При выборе этого значения отображается динамический параметр **FileConnection**.|  
|**Переменная**|Указывает переменную SSI, содержащую скрипт U-SQL. При выборе этого значения отображается динамический параметр **SourceVariable**.|

**SourceType Dynamic Options.** Указывает содержимое скрипта для запроса U-SQL. 

|Тип источника|Динамические параметры|  
|-----------|-----------------|  
|**SourceType = DirectInput**|Введите отправляемый запрос U-SQL непосредственно в окно параметров или нажмите кнопку обзора (...), чтобы ввести запрос U-SQL в диалоговое окно **Ввод запроса U-SQL**.|  
|**SourceType = FileConnection**|Выберите существующий диспетчер подключений файлов или щелкните <**Новое подключение**>, чтобы создать подключение файла. См. дополнительные сведения о [диспетчере подключения файлов](../../integration-services/connection-manager/file-connection-manager.md) и [редакторе диспетчера подключения файлов](../../integration-services/connection-manager/file-connection-manager-editor.md).|  
|**SourceType = Variable**|Выберите существующую переменную или щелкните \<**Создать переменную**>, чтобы создать новую. См. дополнительные сведения о [переменных Integration Services](../../integration-services/integration-services-ssis-variables.md) и [добавлении переменной](https://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5).|


### <a name="job-configuration"></a>Конфигурация задания
Конфигурация задания определяет свойства отправляемого задания U-SQL.

- **AzureDataLakeAnalyticsConnection** — указывает учетную запись Data Lake Analytics, в которую отправляется скрипт U-SQL. Выберите соединение из списка определенных диспетчеров соединений. Чтобы создать новое подключение, выберите <**Новое подключение**>. См. дополнительные сведения о [диспетчере подключений Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md).

- **JobName** — указывает имя задания U-SQL. 
- **AnalyticsUnits** — содержит счетчик единиц использования аналитики для задания U-SQL.
- **Priority** — указывает приоритет для задания U-SQL. Можно задать значение от 0 до 1000. Чем меньше число, тем выше приоритет.
- **RuntimeVersion** — указывает версию среды выполнения Data Lake Analytics для задания U-SQL. По умолчанию этот параметр имеет значение default. В большинстве случаев это свойство изменять не нужно.
- **Synchronous** — логическое значение, которое определяет, будет ли задача ожидать выполнения задания. Если установлено значение true, по завершении задания задача отмечается как **успешно выполненная**. Если установлено значение false, задача отмечается как **успешно выполненная** после перехода задания в состояние подготовки.

  |Значение|Описание|
  |-----------|-----------------|
  |True|Результат задачи определяется по результату выполнения задания U-SQL. Успешное выполнение задания > успешное выполнение задачи. Сбой задания > сбой задачи. Успешное выполнение или сбой задания > завершение задачи.|
  |False|Результат задачи определяется по результату отправки и подготовки задания U-SQL. Успешная отправка задания и прохождение этапа подготовки > успешное выполнение задачи. Сбой отправки задания или сбой задания на этапе подготовки > сбой задачи. Успешное выполнение или сбой задания > завершение задачи.|

- **TimeOut** — указывает время ожидания для выполнения задания (в секундах). Если время ожидания выполнения задания истекает, оно отменяется и отмечается как неудачное. Это свойство недоступно, если **Synchronous** имеет значение false.

## <a name="parameter-mapping-page-configuration"></a>Конфигурация страницы "Сопоставление параметров"

Используйте страницу **Сопоставление параметров** в диалоговом окне **Редактор задач Azure Data Lake Analytics**, чтобы сопоставить переменные с параметрами (переменными U-SQL) в скрипте U-SQL.

- **Имя переменной.** Когда вы добавите сопоставление параметра, выбрав **Добавить**, выберите определенную системой или пользователем переменную в списке. Кроме того, вы можете выбрать <**Новая переменная**>, чтобы добавить новую переменную с помощью диалогового окна **Добавление переменной**. См. дополнительные сведения о [переменных в службах Integration Services (SSIS)](../../integration-services/integration-services-ssis-variables.md).  

- **Имя параметра** — укажите имя параметра или переменной в скрипте U-SQL. Имя параметра должно начинаться с символа \@, например \@Param1. 

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

Обратите внимание, что пути ввода и вывода определены в параметрах **\@in** и **\@out**. Значения для параметров **\@in** и **\@out** в скрипте U-SQL передаются динамически, как настроено в конфигурации сопоставления параметров.

|Имя переменной|Имя параметра|
|-------------|--------------|
|User: Variable1|\@in|
|User: Variable2|\@out| 

## <a name="expression-page-configuration"></a>Конфигурация страницы "Выражения"

Вы можете назначить все свойства в конфигурации страницы "Общие" в качестве выражений свойств, чтобы организовать динамическое обновление свойств во время выполнения. См. дополнительные сведения об [использовании выражений свойств в пакетах](../../integration-services/expressions/use-property-expressions-in-packages.md).

## <a name="see-also"></a>См. также раздел
- [Диспетчер подключений Azure Data Lake Analytics](../../integration-services/connection-manager/azure-data-lake-analytics-connection-manager.md)
- [Задача «Файловая система» для Azure Data Lake](../../integration-services/control-flow/azure-data-lake-store-file-system-task.md)
- [Диспетчер подключений Azure Data Lake Store](../../integration-services/connection-manager/azure-data-lake-store-connection-manager.md)

