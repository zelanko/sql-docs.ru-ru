---
description: Кодирование и отладка компонента скрипта
title: Кодирование и отладка компонента скрипта | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- SSIS Script task, development environment
- Script component [Integration Services], debugging
- Script component [Integration Services], coding
- SSIS Script component, debugging
- Script component [Integration Services], development environment
- debugging [Integration Services], scripts
- SSIS Script component, coding
- VSTA
ms.assetid: c3913c15-66aa-4b61-89b5-68488fa5f0a4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ef340421dc6d4075a40f78f782cda3273a05900b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430336"
---
# <a name="coding-and-debugging-the-script-component"></a>Кодирование и отладка компонента скрипта

[!INCLUDE[sqlserver-ssis](../../../includes/applies-to-version/sqlserver-ssis.md)]


  В конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] у компонента Script есть два режима: режим конструирования метаданных и режим конструирования кода. Когда открывается **редактор преобразования "Скрипт"** , компонент переключается в режим конструктора метаданных, в котором настраиваются метаданные и задаются свойства компонентов. После того как будут заданы свойства компонента скрипта и настроены входы и выходы в режиме конструктора метаданных, можно переключиться в режим редактирования кода для составления пользовательского скрипта. Дополнительные сведения о режимах конструктора метаданных и кода см. в разделе [Настройка компонента скрипта в редакторе компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
## <a name="writing-the-script-in-code-design-mode"></a>Разработка скрипта в режиме конструктора кода  
  
### <a name="script-component-development-environment"></a>Среда разработки компонента скрипта  
 Для подготовки скрипта нажмите кнопку **Изменить скрипт** на странице **Скрипт** в окне **Редактор преобразования "Скрипт"** . Откроется среда разработки скриптов средств [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для приложений (VSTA). В среде разработки VSTA предусмотрены все стандартные возможности среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET, в том числе редактор [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] с цветовым выделением, технологией IntelliSense и браузером объектов.  
  
 Код скрипта пишется на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Пользователь указывает язык скриптов, задавая значение свойства **ScriptLanguage** в окне **Редактор преобразования "Скрипт"** . Если разработчик предпочитает пользоваться другим языком программирования, то можно разработать пользовательскую сборку на выбранном языке и вызвать его функциональные возможности из кода в компоненте скрипта.  
  
 Скрипт, созданный в компоненте скрипта, хранится в определении пакета. Отдельного файла скрипта не существует. Поэтому использование компонента скрипта не влияет на развертывание пакета.  
  
> [!NOTE]  
>  При проектировании пакета код скрипта временно записывается в файл проекта. Хранение конфиденциальных сведений в файле представляет потенциальный риск для безопасности, поэтому в код скрипта не рекомендуется включать конфиденциальные сведения, например пароли.  
  
 По умолчанию параметр **Option Strict** в интегрированной среде разработки отключен.  
  
### <a name="script-component-project-structure"></a>Структура проекта компонента скрипта  
 Преимущество компонента скрипта заключается в возможности создавать код инфраструктуры, что уменьшает объем кода, который приходится писать вручную. В основе этой возможности лежит тот факт, что входы и выходы, а также их столбцы и свойства являются фиксированными и известны заранее. Поэтому любые последующие изменения, внесенные в метаданные компонента, могут сделать подготовленный код неработоспособным. Это приводит к ошибке при выполнении пакета.  
  
#### <a name="project-items-and-classes-in-the-script-component-project"></a>Элементы и классы проекта в проекте компонента скрипта  
 При переключении в режим конструктора кода открывается среда разработки VSTA, где отображается элемент проекта **ScriptMain**. Элемент проекта **ScriptMain** содержит редактируемый класс **ScriptMain**, который служит точкой входа в скрипт и в котором проектируется код. Элементы кода в классе изменяются в зависимости от языка программирования, выбранного для задачи «Скрипт».  
  
 Проект скрипта содержит два дополнительных автоматически созданных элемента проекта, доступных только для чтения.  
  
-   Элемент проекта **ComponentWrapper** содержит три класса:  
  
    -   Класс **UserComponent**, который наследуется от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> и содержит методы и свойства для обработки данных и взаимодействия с пакетами. Класс **ScriptMain** наследуется от класса **UserComponent**.  
  
    -   Коллекция классов **Connections**, которая содержит ссылки на подключения, выбранные на странице "Диспетчер подключений" в редакторе преобразования "Скрипт".  
  
    -   Коллекция классов **Variables**, которая содержит ссылки на переменные, введенные в свойства **ReadOnlyVariable** и **ReadWriteVariables** на странице **Скрипт** в **редакторе преобразования "Скрипт"** .  
  
-   Элемент проекта **BufferWrapper** содержит класс, который наследует от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> для каждого входа и выхода, настроенного на странице **Входы и выходы** в **редакторе преобразования "Скрипт"** . Каждый из этих классов содержит типизированные свойства метода доступа, которые соответствуют настроенным входным и выходным столбцам, а также буферы потока данных, содержащие столбцы.  
  
 Дополнительные сведения об использовании этих объектов, методов и свойств см. в разделе [Основные сведения о модели объектов компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md). Сведения об использовании методов и свойств этих классов в компоненте скрипта определенного типа см. в разделе [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). В разделах примеров также приведен полный образец кода.  
  
 Если настроить компонент "Скрипт" в качестве преобразования, элемент проекта **ScriptMain** будет содержать следующий автоматически сформированный код. В шаблоне кода также имеется обзор компонента «Скрипт» и дополнительные сведения о получении и управлении такими объектами служб SSIS, как переменные, события и соединения.  
  
```vb  
' Microsoft SQL Server Integration Services Script Component  
' Write scripts using Microsoft Visual Basic 2008.  
' ScriptMain is the entry point class of the script.  
  
Imports System  
Imports System.Data  
Imports System.Math  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
  
<Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute> _  
<CLSCompliant(False)> _  
Public Class ScriptMain  
    Inherits UserComponent  
  
    Public Overrides Sub PreExecute()  
        MyBase.PreExecute()  
        '  
        ' Add your code here for preprocessing or remove if not needed  
        '  
    End Sub  
  
    Public Overrides Sub PostExecute()  
        MyBase.PostExecute()  
        '  
        ' Add your code here for postprocessing or remove if not needed  
        ' You can set read/write variables here, for example:  
        ' Me.Variables.MyIntVar = 100  
        '  
    End Sub  
  
    Public Overrides Sub Input0_ProcessInputRow(ByVal Row As Input0Buffer)  
        '  
        ' Add your code here  
        '  
    End Sub  
  
End Class  
```  
  
```csharp  
/* Microsoft SQL Server Integration Services user script component  
*  Write scripts using Microsoft Visual C# 2008.  
*  ScriptMain is the entry point class of the script.*/  
  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
  
[Microsoft.SqlServer.Dts.Pipeline.SSISScriptComponentEntryPointAttribute]  
public class ScriptMain : UserComponent  
{  
  
    public override void PreExecute()  
    {  
        base.PreExecute();  
        /*  
          Add your code here for preprocessing or remove if not needed  
        */  
    }  
  
    public override void PostExecute()  
    {  
        base.PostExecute();  
        /*  
          Add your code here for postprocessing or remove if not needed  
          You can set read/write variables here, for example:  
          Variables.MyIntVar = 100  
        */  
    }  
  
    public override void Input0_ProcessInputRow(Input0Buffer Row)  
    {  
        /*  
          Add your code here  
        */  
    }  
  
}  
```  
  
#### <a name="additional-project-items-in-the-script-component-project"></a>Дополнительные элементы проекта в проекте компонента скрипта  
 Проект компонента скрипта может содержать элементы, отличные от элемента **ScriptMain** по умолчанию. Можно добавлять в проект классы, модули, файлы кода и папки, а также можно упорядочивать группы элементов с помощью папок.  
  
 Все добавляемые элементы сохраняются внутри пакета.  
  
#### <a name="references-in-the-script-component-project"></a>Ссылки в проекте компонента скрипта  
 Чтобы добавить ссылки в управляемые сборки, щелкните правой кнопкой мыши проект задачи "Скрипт" в **Обозревателе проектов**, затем выберите **Добавить ссылку**. Дополнительные сведения см. в разделе [Ссылки на другие сборки в решениях со сценариями](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  Ссылки проекта можно просмотреть в среде разработки VSTA в **представлении классов** или в **обозревателе проектов**. Любое из этих окон можно открыть из меню **Вид**. Можно добавить новую ссылку из меню **Проект**, из **обозревателя проектов** или из **представления классов**.  
  
## <a name="interacting-with-the-package-in-the-script-component"></a>Взаимодействие с пакетом в компоненте скрипта  
 Пользовательский скрипт, составленный в компоненте скрипта, может обращаться к переменным и диспетчерам соединений из объемлющего пакета и использовать их через строго типизированные методы доступа в автоматически формируемых основных классах. Однако перед входом в режим конструктора кода необходимо настроить как переменные, так и диспетчеры соединений, если нужно сделать их доступными для скрипта. Кроме того, из кода компонента скрипта можно создавать события и вести журналы.  
  
 Автоматически созданные элементы проекта в проекте компонента скрипта предоставляют следующие объекты, методы и свойства для взаимодействия с пакетом.  
  
|Компонент пакета|Метод доступа|  
|---------------------|-------------------|  
|Переменные|Использование именованных и типизированных свойств метода доступа класса коллекции **Variables** в элементе проекта **ComponentWrapper**, отображенном в свойстве **Variables** класса **ScriptMain**.<br /><br /> Метод **PreExecute** может обращаться только к переменным, доступным только для чтения. Метод **PostExecute** может обращаться как к переменным, доступным только для чтения, так и к переменным, доступным для чтения и записи.|  
|Соединения|Использование именованных и типизированных свойств метода доступа класса коллекции **Connections** в элементе проекта **ComponentWrapper**, отображенном в свойстве **Connections** класса **ScriptMain**.|  
|События|Создание событий с помощью свойства <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> класса **ScriptMain** и методов **Fire\<X>** интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>.|  
|Logging|Ведение журнала с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> класса **ScriptMain**.|  
  
## <a name="debugging-the-script-component"></a>Отладка компонента скрипта  
 Для отладки кода в компоненте «Скрипт» установите в коде по крайней мере одну точку останова, а затем закройте среду разработки VSTA IDE, чтобы запустить пакет в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Когда выполнение пакета входит в компонент «Скрипт», среда разработки VSTA IDE открывается повторно и отображает код в режиме только для чтения. После того как выполнение достигает точку останова, можно проверить значения переменных и выполнить оставшийся код в режиме пошагового выполнения.  
  
> [!NOTE]  
>  Однако нельзя выполнять отладку компонента «Скрипт», если этот компонент запускается как часть дочернего пакета, вызываемого задачей «Выполнение пакета». В этом случае точки останова, установленные в компоненте «Скрипт» в дочернем пакете, пропускаются. Дочерний пакет можно нормально отладить, запустив его отдельно.  
  
> [!NOTE]  
>  Во время отладки пакета, содержащего несколько компонентов «Скрипт», отладчик выполняет отладку одного компонента «Скрипт». Затем система может выполнять отладку другого компонента «Скрипт», если отладчик завершает работу, как в случае контейнера «цикл по элементам» или «цикл по каждому элементу».  
  
 Наблюдать за выполнением компонента «Скрипт» также можно следующими способами.  
  
-   Прерывать выполнение и выводить на экран модальное сообщение с помощью метода **MessageBox.Show** в пространстве имен **System.Windows.Forms**. (После завершения процесса отладки этот код следует удалить.)  
  
-   Создавать события для информационных сообщений, предупреждений и ошибок. Методы FireInformation, FireWarning и FireError отображают описание события в окне **Вывод** Visual Studio. Тем не менее методы FireProgress, Console.Write и Console.WriteLine не отображают никакие сведения в окне **Вывод**. Сообщения из события FireProgress отображаются на вкладке **Ход выполнения** конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Дополнительные сведения см. в разделе [Вызов событий в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md).  
  
-   Протоколировать события или пользовательские сообщения на включенных регистраторах. Дополнительные сведения см. в разделе [Ведение журнала в задаче скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md).  
  
 Если нужно только проанализировать выход компонента скрипта, настроенного в качестве источника или преобразования, без сохранения данных в месте назначения, то можно остановить поток данных с помощью [преобразования "Подсчет строк"](../../../integration-services/data-flow/transformations/row-count-transformation.md) и присоединить средство просмотра данных к выходу компонента скрипта. Дополнительные сведения о средствах просмотра данных см. в разделе [Отладка потока данных](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 Дополнительные сведения о написании кода компонента скрипта см. в следующих подразделах в этом разделе.  
  
 [Основные сведения о модели объектов компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Использование объектов, методов и свойств, доступных в компоненте скрипта.  
  
 [Ссылки на другие сборки в решениях со сценариями](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Способы назначения ссылок на объекты из библиотеки классов [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] в компоненте скрипта.  
  
 [Имитация вывода ошибок для компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Способы имитации вывода ошибок для строк, которые вызвали ошибки в ходе обработки компонентом скрипта.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [Затруднения при установке и настройке VSTA для установок SSIS 2008 и R2](https://go.microsoft.com/fwlink/?LinkId=215661) на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента скрипта в редакторе компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
  
  
