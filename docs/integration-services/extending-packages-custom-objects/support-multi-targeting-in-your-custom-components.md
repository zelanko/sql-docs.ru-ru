---
title: "Поддержка нескольких версий в пользовательские компоненты | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server (starting with 2016)
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 96ec352784f060f444b8adcae6005dd454b3b460
ms.openlocfilehash: dc111f1d884a3553156b55ab490afef2f8df9d61
ms.contentlocale: ru-ru
ms.lasthandoff: 09/27/2017

---
# <a name="support-multi-targeting-in-your-custom-components"></a>Поддержка нескольких версий в пользовательские компоненты
 Теперь можно использовать конструктор служб SSIS в SQL Server Data Tools (SSDT) для создания, поддержания и запускать пакеты, предназначенные для SQL Server 2016, SQL Server 2014 или SQL Server 2012. Процедуру получения SSDT для Visual Studio 2015 см. в разделе [загрузить последние SQL Server Data Tools](../../ssdt/download-sql-server-data-tools-ssdt.md). 

 В обозревателе решений щелкните правой кнопкой мыши проект служб Integration Services и выберите пункт **Свойства** , чтобы открыть страницу свойств проекта. На вкладке **Общие** окна **Свойства конфигурации**выберите свойство **TargetServerVersion** и затем SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
   
 ![Свойство TargetServerVersion, в диалоговом окне свойств проекта](../../integration-services/media/targetserverversion2.png "свойство TargetServerVersion, в диалоговом окне свойств проекта")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>Несколько поддерживаемые версии и многоплатформенного нацеливания пользовательских компонентов
 
Все пять типов пользовательских расширений служб SSIS поддерживают многоплатформенного нацеливания.
-   Диспетчеры соединений
-   Задания
-   Перечислители
-   Регистраторы
-   Компоненты потока данных

Для управляемых расширений конструктора служб SSIS загружает версию расширений для заданной целевой версии. Например:
-   Если целевая версия SQL Server 2012, конструктор загружает 2012 г. версия расширения.
-   Если целевая версия SQL Server 2016, конструктор загружает версию 2016 расширения.

Расширения COM не поддерживают многоплатформенного нацеливания. Конструктор служб SSIS всегда загружает расширение COM для текущей версии SQL Server, независимо от версии указанный целевой объект.

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>Добавить базовую поддержку нескольких версий и для различных версий

Основные рекомендации в разделе [начало пользовательских расширений служб SSIS для поддержки поддержка нескольких версий 2015 SSDT для SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/). В этой записи блога описывает следующие действия или требования.

-   Развертывание сборок в соответствующие папки.

-   Создание файла карты расширения для SQL Server 2014 и высокой версии.

## <a name="add-code-to-switch-versions"></a>Добавьте код для переключения версии

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>Переключение версий в пользовательский диспетчер соединений, задачи, перечислителя или регистратор

Для пользовательского диспетчера соединений, задачи, перечислителя или РЕГИСТРАТОР, добавьте логику возврат к предыдущей версии в **функции SaveToXML** метод.

```csharp
public void SaveToXML(XmlDocument doc, IDTSInfoEvents events)
{
    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
    }

    if (TargetServerVersion == DTSTargetServerVersion.SQLServer2012)
    {
         // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
    }
}
```

### <a name="switch-versions-in-a-custom-data-flow-component"></a>Переключить версии пользовательского компонента потока данных

Для пользовательского диспетчера соединений, задачи, перечислителя или РЕГИСТРАТОР, добавить логику возврат к предыдущей версии в новом **PerformDowngrade** метод.

```csharp
public override void PerformDowngrade(int pipelineVersion, DTSTargetServerVersion targetServerVersion)
{
    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2014)
    {
        // Add logic to downgrade from SQL Server 2016 to SQL Server 2014.
        ComponentMetaData.Version = 8;
    }

    if (targetServerVersion == DTSTargetServerVersion.DTSTSV_SQLSERVER2012)
    {
          // Add logic to downgrade from SQL Server 2016 to SQL Server 2012.
        ComponentMetaData.Version = 6;
    }
}
```

## <a name="common-errors"></a>Распространенные ошибки

### <a name="invalidcastexception"></a>InvalidCastException

**Сообщение об ошибке.** Невозможно привести COM-объект типа «System.__ComObject» для интерфейса типа «Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100». Сбой операции из-за вызов QueryInterface COM-компонента для интерфейса с IID «{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}» из-за следующей ошибки: интерфейс не поддерживается (исключение из HRESULT: 0x80004002 (E_NOINTERFACE)). (Microsoft.SqlServer.DTSPipelineWrap).

**Решение.** Если ваш пользовательский модуль ссылается на сборки взаимодействия служб SSIS, например Microsoft.SqlServer.DTSPipelineWrap или Microsoft.SqlServer.DTSRuntimeWrap, установите для параметра **внедрить типы взаимодействия** свойства ** False».

![Внедрение типов взаимодействия](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>Не удалось загрузить некоторые типы, если целевая версия SQL Server 2012

Эта проблема затрагивает определенных типов, например IErrorReportingService или IUserPromptService.

**Сообщение об ошибке (например,).** Не удалось загрузить тип «Microsoft.DataWarehouse.Design.IErrorReportingService» из сборки "Microsoft.DataWarehouse, версия = 13.0.0.0, Culture = neutral, PublicKeyToken = 89845dcd8080cc91".

**Обходной путь.** Если целевая версия SQL Server 2012, используйте MessageBox вместо этих интерфейсов.


