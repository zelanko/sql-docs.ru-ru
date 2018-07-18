---
title: Разработка пользовательских объектов для служб Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services]
- custom objects [Integration Services]
ms.assetid: ca1929a6-0ae6-47d7-b65f-08173b143720
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 41e255b2e5a7d66815b39e7fc1b44b5a87fae8cb
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35401376"
---
# <a name="developing-custom-objects-for-integration-services"></a>Разработка пользовательских объектов для служб Integration Services
  Если объекты потока управления и потока данных, поставляемые со службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], не отвечают потребностям пользователя, можно разработать множество типов собственных пользовательских объектов, в том числе:  
  
-   **Пользовательские задачи**.  
  
-   **Пользовательские диспетчеры соединений.** Соединение с внешними источниками данных, не поддерживаемыми в настоящее время.  
  
-   **Пользовательские регистраторы.** Регистрация событий пакета в форматах, не поддерживаемых в настоящее время.  
  
-   **Пользовательские перечислители.** Поддержка итерации по набору объектов или форматов значений, не поддерживаемых в настоящее время.  
  
-   **Пользовательские компоненты потока данных.** Могут быть настроены источники, преобразования или назначения.  
  
 Модель объектов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] поддерживает такую пользовательскую разработку с помощью базовых классов, формирующих согласованную надежную структуру для пользовательской реализации.  
  
 Если не требуется повторно использовать пользовательскую функциональность в нескольких пакетах, задача «Скрипт» и компонент скрипта предоставляют все возможности для использования языка программирования управляемого кода при значительно меньшем объеме необходимой для этого кода инфраструктуры. Дополнительные сведения см. в разделе [Сравнение решений со сценариями и пользовательских объектов](../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md).  
  
## <a name="steps-in-developing-a-custom-object-for-integration-services"></a>Шаги разработки пользовательского объекта для служб Integration Services  
 При разработке пользовательского объекта для использования в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] разрабатывается библиотека классов (DLL), которая затем загружается во время разработки и выполнения конструктором служб SSIS и средой времени выполнения служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Наиболее важными для реализации методами являются не те, которые вызываются из собственного пользовательского кода, а те, которые вызываются средой выполнения в соответствующие моменты для инициализации и проверки компонента и активации его функциональности.  
  
 Ниже перечислены шаги разработки пользовательского объекта:  
  
1.  Создайте новый проект типа библиотеки классов на предпочитаемом языке программирования управляемого кода.  
  
2.  Создайте класс, наследующий от соответствующего базового класса, как показано в следующей таблице.  
  
3.  Примените к новому классу соответствующий атрибут, как показано в следующей таблице.  
  
4.  Переопределите методы базового класса и напишите код для пользовательской функциональности своего объекта.  
  
5.  При необходимости создайте пользовательский интерфейс для своего компонента. Для упрощения развертывания пользовательский интерфейс можно разрабатывать как отдельный проект в рамках того же решения и построить его как отдельную сборку.  
  
6.  При необходимости можно отобразить ссылку на образцы кода и содержимое справки по пользовательскому объекту в **панели элементов служб SSIS**.  
  
7.  Выполните построение, развертывание и отладку нового пользовательского объекта, как описывается в разделе [Построение, развертывание и отладка пользовательских объектов](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md).  
  
## <a name="base-classes-attributes-and-important-methods"></a>Базовые классы, атрибуты и важные методы  
 В этой таблице содержатся справочные сведения о большинстве важных элементов объектной модели служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для каждого типа пользовательских объектов, доступных для разработки.  
  
|Пользовательский объект|Базовый класс|attribute|Важные методы|  
|-------------------|----------------|---------------|-----------------------|  
|Задача|<xref:Microsoft.SqlServer.Dts.Runtime.Task>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A>|  
|Диспетчер соединений|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A>|  
|Регистратор|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A>|  
|Перечислитель|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>|<xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A>|  
|Компонент потока данных|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>|<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>|<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>|  
  
## <a name="providing-links-to-samples-and-help-content"></a>Предоставление ссылок на образцы кода и содержимое справки  
 Для отображения в **панели элементов служб SSIS** ссылки на образцы кода и содержимое справки по пользовательскому объекту, использующему управляемый код, используются следующие свойства.  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Pipeline.DTSPipelineComponentAttribute.HelpKeyword%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.SamplesTag%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpCollection%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.DTSTaskAttribute.HelpKeyword%2A>  
  
 Чтобы отобразить ссылку на образцы кода и содержимое справки по пользовательскому объекту, использующему собственный код, добавьте в файл скрипта реестра (RGS-файл) записи SamplesTag, HelpKeyword и HelpCollection. Пример приведен ниже.  
  
 `val HelpKeyword = s 'sql11.dts.designer.executepackagetask.F1'`  
  
 `val SamplesTag = s 'ExecutePackageTask'`  
  
## <a name="providing-a-custom-user-interface"></a>Создание настраиваемого пользовательского интерфейса  
 Чтобы предоставить пользователям возможность настраивать свойства пользовательского объекта, потребуется также создать настраиваемый пользовательский интерфейс. В случаях, когда создание пользовательского интерфейса необязательно, возможно, окажется целесообразным создать его, чтобы предоставить пользователю дружественный интерфейс, более удобный, чем редактор по умолчанию.  
  
 В проекте или сборке пользовательского интерфейса обычно используются два класса — класс, реализующий интерфейс служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] для пользовательских интерфейсов определенного типа пользовательского объекта, и форма Windows, отображаемая им для получения сведений от пользователя. Интерфейсы, реализуемые пользователем, имеют лишь несколько методов, и разработка пользовательского интерфейса не представляет особой сложности.  
  
> [!NOTE]  
>  Многие регистраторы служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] имеют пользовательский интерфейс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> и заменяющий текстовое поле **Конфигурация** отфильтрованным раскрывающимся списком доступных диспетчеров соединений. Однако пользовательские интерфейсы для пользовательских регистраторов в этом выпуске служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] не реализованы. Указание значения для свойства <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> не имеет никакого эффекта.  
  
 В следующей таблице содержатся справочные сведения об интерфейсах, которые необходимо реализовать при разработке пользовательского интерфейса для каждого типа пользовательского объекта. В ней также поясняется, как выглядит результат работы для пользователя в случае, если для объекта не был разработан пользовательский интерфейс или если не удалось связать объект с пользовательским интерфейсом при помощи свойства **UITypeName** в атрибуте объекта. Хотя возможностей расширенного редактора может быть достаточно для компонента потока данных, окно «Свойства» является менее удобным для пользователя решением для задач и диспетчеров соединений, а пользовательский перечислитель Foreach и вовсе невозможно настроить без пользовательской формы.  
  
|Пользовательский объект|Базовый класс для пользовательского интерфейса|Редактор по умолчанию при отсутствии пользовательского интерфейса|  
|-------------------|-----------------------------------|----------------------------------------------------------------------|  
|Задача|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|Только окно свойств|  
|Диспетчер соединений|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI>|Только окно свойств|  
|Регистратор|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI><br /><br /> (Не реализовано в службах [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)])|Текстовое поле в столбце **Конфигурация**|  
|Перечислитель|<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>|Только окно «Свойства». Область «Конфигурация перечислителя» редактора остается пустой.|  
|Компонент потока данных|<xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>|Расширенный редактор|  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [Процесс построения решения Visual Studio выдает предупреждение о косвенной зависимости от сборки .NET Framework из-за ссылок служб SSIS](http://go.microsoft.com/fwlink/?LinkId=215662) на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение пользовательских объектов](../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)   
 [Сборка, развертывание и отладка пользовательских объектов](../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
  
  
