---
title: Поддержка многоплатформенного нацеливания в пользовательских компонентах | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: ec611374-16bf-4a56-8fd9-45d3ddd7befc
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 91524408998df8be0df4ee5d4ede0b641dbaa2a4
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71287228"
---
# <a name="support-multi-targeting-in-your-custom-components"></a>Поддержка многоплатформенного нацеливания в пользовательских компонентах

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 Теперь можно использовать конструктор SSIS в SQL Server Data Tools (SSDT), чтобы создавать, обслуживать и выполнять пакеты, ориентированные на SQL Server 2014, SQL Server 2012 или SQL Server 2012. Процедуру получения SSDT для Visual Studio 2015 см. в разделе [Скачивание последней версии SQL Server Data Tools](../../ssdt/download-sql-server-data-tools-ssdt.md). 

 В обозревателе решений щелкните правой кнопкой мыши проект служб Integration Services и выберите пункт **Свойства**, чтобы открыть страницу свойств проекта. На вкладке **Общие** окна **Свойства конфигурации** выберите свойство **TargetServerVersion** и затем SQL Server 2016, SQL Server 2014 или SQL Server 2012.  
   
 ![Свойство TargetServerVersion в диалоговом окне свойств проекта](../../integration-services/media/targetserverversion2.png "Свойство TargetServerVersion в диалоговом окне свойств проекта")  
 
 ## <a name="multiple-version-support-and-multi-targeting-for-custom-components"></a>Поддержка нескольких версий и многоплатформенного нацеливания в пользовательских компонентах
 
Все пять типов настраиваемых расширений служб SSIS поддерживают многоплатформенное нацеливание.
-   Диспетчеры соединений
-   Задания
-   Enumerators
-   Регистраторы
-   Компоненты потока данных

При работе с управляемыми расширениями конструктор служб SSIS загружает версию расширения для заданной целевой версии. Пример:
-   Если целевая версия — SQL Server 2012, конструктор загружает расширение версии 2012.
-   Если целевая версия — SQL Server 2016, конструктор загружает расширение версии 2016.

Расширения COM не поддерживают многоплатформенное нацеливание. Конструктор служб SSIS всегда загружает расширение COM для текущей версии SQL Server, независимо от указанной целевой версии.

## <a name="add-basic-support-for-multiple-versions-and-multi-targeting"></a>Добавление базовой поддержки нескольких версий и многоплатформенного нацеливания

Общие сведения см. в разделе [Получение пользовательских расширений служб SSIS, поддерживаемых несколькими версиями SSDT 2015 для SQL Server 2016](https://blogs.msdn.microsoft.com/ssis/2016/04/19/getting-your-ssis-custom-extensions-to-be-supported-by-the-multi-version-support-of-ssdt-2015-for-sql-server-2016/) Эта запись блога описывает следующие шаги или требования:

-   Развертывание сборок в соответствующие папки.

-   Создание файла карты расширения для SQL Server 2014 и более поздних версий.

## <a name="add-code-to-switch-versions"></a>Добавление кода для переключения версий

### <a name="switch-versions-in-a-custom-connection-manager-task-enumerator-or-log-provider"></a>Переключение версий в пользовательском диспетчере подключений, задаче, перечислителе или регистраторе

Для пользовательского диспетчера подключений, задачи, перечислителя или регистратора добавьте логику для использования более ранней версии в метод **SaveToXML**.

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

### <a name="switch-versions-in-a-custom-data-flow-component"></a>Переключение версий в пользовательском компоненте потока данных

Для пользовательского диспетчера подключений, задачи, перечислителя или регистратора добавьте логику для использования более ранней версии в новый метод **PerformDowngrade**.

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

**Сообщение об ошибке.** Невозможно привести COM-объект типа "System.__ComObject" к интерфейсному типу "Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100". Операция завершилась со сбоем, так как вызов QueryInterface COM-компонента для интерфейса с IID "{BE8C48A3-155B-4810-BA5C-BDF68A659E9E}" возвратил ошибку: "Интерфейс не поддерживается (Исключение из HRESULT: 0x80004002 (E_NOINTERFACE))". (Microsoft.SqlServer.DTSPipelineWrap).

**Решение.** Если ваше настраиваемое расширение ссылается на сборки взаимодействия служб SSIS, такие как Microsoft.SqlServer.DTSPipelineWrap или Microsoft.SqlServer.DTSRuntimeWrap, задайте для свойства **Внедрить типы взаимодействия** значение **False**.

![Внедрить типы взаимодействия](../../integration-services/extending-packages-custom-objects/media/embed-interop-types.png)

### <a name="unable-to-load-some-types-when-target-version-is-sql-server-2012"></a>Не удается загрузить некоторые типы, когда целевой версией является SQL Server 2012

Эта проблема затрагивает определенные типы, например IErrorReportingService или IUserPromptService.

**Сообщение об ошибке (пример).** Не удалось загрузить тип "Microsoft.DataWarehouse.Design.IErrorReportingService" из сборки "Microsoft.DataWarehouse, Version=13.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91".

**Обходной путь**. Если целевой версией является SQL Server 2012, используйте MessageBox вместо этих интерфейсов.

