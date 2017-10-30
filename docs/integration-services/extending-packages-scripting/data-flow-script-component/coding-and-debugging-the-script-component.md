---
title: "Кодирование и отладка компонента скрипта | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
caps.latest.revision: 66
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: ff6c9814547a83439717f8a88d3bd52be80c4ca5
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="coding-and-debugging-the-script-component"></a>Кодирование и отладка компонента скрипта
  В конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)] у компонента Script есть два режима: режим конструирования метаданных и режим конструирования кода. При открытии **редактор преобразования «скрипт»**, компонент перейдет в режим конструктора метаданных, в котором настраиваются метаданные и свойства компонентов. После того как будут заданы свойства компонента скрипта и настроены входы и выходы в режиме конструктора метаданных, можно переключиться в режим редактирования кода для составления пользовательского скрипта. Дополнительные сведения о режиме конструктора метаданных и режим конструктора кода см. в разделе [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md).  
  
## <a name="writing-the-script-in-code-design-mode"></a>Разработка скрипта в режиме конструктора кода  
  
### <a name="script-component-development-environment"></a>Среда разработки компонента скрипта  
 Создайте сценарий, нажмите кнопку **изменить скрипт** на **сценарий** страница **редактор преобразования «скрипт»** Открытие [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) интегрированной среды разработки. В среде разработки VSTA предусмотрены все стандартные возможности среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] .NET, в том числе редактор [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] с цветовым выделением, технологией IntelliSense и браузером объектов.  
  
 Код скрипта пишется на языке [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#. Укажите язык скриптов, задав **ScriptLanguage** свойство в **редактор преобразования «скрипт»**. Если разработчик предпочитает пользоваться другим языком программирования, то можно разработать пользовательскую сборку на выбранном языке и вызвать его функциональные возможности из кода в компоненте скрипта.  
  
 Скрипт, созданный в компоненте скрипта, хранится в определении пакета. Отдельного файла скрипта не существует. Поэтому использование компонента скрипта не влияет на развертывание пакета.  
  
> [!NOTE]  
>  При проектировании пакета код скрипта временно записывается в файл проекта. Хранение конфиденциальных сведений в файле представляет потенциальный риск для безопасности, поэтому в код скрипта не рекомендуется включать конфиденциальные сведения, например пароли.  
  
 По умолчанию **Option Strict** в Интегрированной среде разработки отключена.  
  
### <a name="script-component-project-structure"></a>Структура проекта компонента скрипта  
 Преимущество компонента скрипта заключается в возможности создавать код инфраструктуры, что уменьшает объем кода, который приходится писать вручную. В основе этой возможности лежит тот факт, что входы и выходы, а также их столбцы и свойства являются фиксированными и известны заранее. Поэтому любые последующие изменения, внесенные в метаданные компонента, могут сделать подготовленный код неработоспособным. Это приводит к ошибке при выполнении пакета.  
  
#### <a name="project-items-and-classes-in-the-script-component-project"></a>Элементы и классы проекта в проекте компонента скрипта  
 При переключении в режим конструктора кода интегрированной среды разработки VSTA открывает и отображает **ScriptMain** элемент проекта. **ScriptMain** элемент проекта содержит редактируемый **ScriptMain** класс, который служит запись точки для скрипта и который пишется код. Элементы кода в классе изменяются в зависимости от языка программирования, выбранного для задачи «Скрипт».  
  
 Проект скрипта содержит два дополнительных автоматически созданных элемента проекта, доступных только для чтения.  
  
-   **ComponentWrapper** элемент проекта содержит три класса:  
  
    -   **UserComponent** класс, унаследованный от класса <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> и содержит методы и свойства, которые будут использоваться для обработки данных и взаимодействия с пакетом. **ScriptMain** класс наследует от **UserComponent** класса.  
  
    -   Объект **подключений** класс коллекции, содержащей ссылки на подключения, выбранные на странице диспетчер соединений редактор сценариев преобразования.  
  
    -   Объект **переменных** класс коллекции, содержащей ссылки на переменные, введенные в **ReadOnlyVariable** и **ReadWriteVariables** свойства **сценария** страница **редактор преобразования «скрипт»**.  
  
-   **BufferWrapper** элемент проекта содержит класс, который наследует от <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> для каждого входа и выхода, настроенного на **входы и выходы** страница **редактор преобразования «скрипт»**. Каждый из этих классов содержит типизированные свойства метода доступа, которые соответствуют настроенным входным и выходным столбцам, а также буферы потока данных, содержащие столбцы.  
  
 Сведения о том, как использовать эти объекты, методы и свойства в разделе [основные сведения об объектной модели скриптов компонента](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md). Сведения о том, как использовать методы и свойства этих классов в компоненте скрипта определенного типа, обратитесь к разделу [Дополнительные примеры компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md). В разделах примеров также приведен полный образец кода.  
  
 При настройке компонента скрипта как преобразования, **ScriptMain** элемент проекта содержит следующий автоматически формируемый код. В шаблоне кода также имеется обзор компонента «Скрипт» и дополнительные сведения о получении и управлении такими объектами служб SSIS, как переменные, события и соединения.  
  
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
 Проект компонента скрипта может содержать такие элементы, используемый по умолчанию **ScriptMain** элемента. Можно добавлять в проект классы, модули, файлы кода и папки, а также можно упорядочивать группы элементов с помощью папок.  
  
 Все добавляемые элементы сохраняются внутри пакета.  
  
#### <a name="references-in-the-script-component-project"></a>Ссылки в проекте компонента скрипта  
 Можно добавить ссылки на управляемые сборки, щелкнув правой кнопкой мыши проект задачи скрипта в **обозревателя проектов**и выбрав **добавить ссылку**. Дополнительные сведения см. в разделе [ссылки на другие сборки в решениях сценариев](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md).  
  
> [!NOTE]  
>  Ссылки проекта можно просмотреть в среде разработки VSTA в **представление классов** или в **обозревателя проектов**. Можно открыть из этих окон **представление** меню. Можно добавить новую ссылку из **проекта** меню из **обозревателя проектов**, или из **представление классов**.  
  
## <a name="interacting-with-the-package-in-the-script-component"></a>Взаимодействие с пакетом в компоненте скрипта  
 Пользовательский скрипт, составленный в компоненте скрипта, может обращаться к переменным и диспетчерам соединений из объемлющего пакета и использовать их через строго типизированные методы доступа в автоматически формируемых основных классах. Однако перед входом в режим конструктора кода необходимо настроить как переменные, так и диспетчеры соединений, если нужно сделать их доступными для скрипта. Кроме того, из кода компонента скрипта можно создавать события и вести журналы.  
  
 Автоматически созданные элементы проекта в проекте компонента скрипта предоставляют следующие объекты, методы и свойства для взаимодействия с пакетом.  
  
|Компонент пакета|Метод доступа|  
|---------------------|-------------------|  
|Переменные|Использование именованных и типизированных методов доступа свойства в **переменных** класс коллекции в **ComponentWrapper** элемента проекта, предоставляются через **переменных** свойство **ScriptMain** класса.<br /><br /> **PreExecute** метод может открывать только переменным, доступным только для чтения. **PostExecute** метод может доступа только для чтения и чтения и записи переменных.|  
|Соединения|Использование именованных и типизированных методов доступа свойства в **подключений** класс коллекции в **ComponentWrapper** элемента проекта, предоставляются через **подключений** свойство **ScriptMain** класса.|  
|События|Вызывать события с помощью <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> свойство **ScriptMain** класса и **пожара\<X >** методы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> интерфейса.|  
|Ведение журнала|Ведение журнала с помощью <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> метод **ScriptMain** класса.|  
  
## <a name="debugging-the-script-component"></a>Отладка компонента скрипта  
 Для отладки кода в компоненте «Скрипт» установите в коде по крайней мере одну точку останова, а затем закройте среду разработки VSTA IDE, чтобы запустить пакет в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Когда выполнение пакета входит в компонент «Скрипт», среда разработки VSTA IDE открывается повторно и отображает код в режиме только для чтения. После того как выполнение достигает точку останова, можно проверить значения переменных и выполнить оставшийся код в режиме пошагового выполнения.  
  
> [!NOTE]  
>  Однако нельзя выполнять отладку компонента «Скрипт», если этот компонент запускается как часть дочернего пакета, вызываемого задачей «Выполнение пакета». В этом случае точки останова, установленные в компоненте «Скрипт» в дочернем пакете, пропускаются. Дочерний пакет можно нормально отладить, запустив его отдельно.  
  
> [!NOTE]  
>  Во время отладки пакета, содержащего несколько компонентов «Скрипт», отладчик выполняет отладку одного компонента «Скрипт». Затем система может выполнять отладку другого компонента «Скрипт», если отладчик завершает работу, как в случае контейнера «цикл по элементам» или «цикл по каждому элементу».  
  
 Наблюдать за выполнением компонента «Скрипт» также можно следующими способами.  
  
-   Прерывать выполнение и отображение модальное сообщение с помощью **MessageBox.Show** метод в **System.Windows.Forms** пространства имен. (После завершения процесса отладки этот код следует удалить.)  
  
-   Создавать события для информационных сообщений, предупреждений и ошибок. Методы FireInformation, FireWarning и FireError отображают описание события в Visual Studio **вывода** окна. Тем не менее, метод FireProgress, Console.Write-метод и метод не отображают никаких сведений в **вывода** окна. В событии FireProgress появляются на **выполняется** вкладка [!INCLUDE[ssIS](../../../includes/ssis-md.md)] конструктора. Дополнительные сведения см. в разделе [создание событий в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md).  
  
-   Протоколировать события или пользовательские сообщения на включенных регистраторах. Дополнительные сведения см. в разделе [ведения журнала в компоненте скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md).  
  
 Если требуется проверить результаты выполнения компонент скрипта, настроенный в качестве источника или преобразования, без сохранения данных в место назначения, можно остановить поток данных с [Row Count Transformation](../../../integration-services/data-flow/transformations/row-count-transformation.md) и присоединить средство просмотра данных к выходу компонента скрипта. Сведения о средствах просмотра данных см. в разделе [Debugging Data Flow](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 Дополнительные сведения о написании кода компонента скрипта см. в следующих подразделах в этом разделе.  
  
 [Основные сведения о модели объектов компонента скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 Использование объектов, методов и свойств, доступных в компоненте скрипта.  
  
 [Ссылки на другие сборки в решениях со сценариями](../../../integration-services/extending-packages-scripting/referencing-other-assemblies-in-scripting-solutions.md)  
 Способы назначения ссылок на объекты из библиотеки классов [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] в компоненте скрипта.  
  
 [Имитация вывода ошибок для компонента скрипта](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 Способы имитации вывода ошибок для строк, которые вызвали ошибки в ходе обработки компонентом скрипта.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Запись в блоге [VSTA установке и настройке VSTA для установок SSIS 2008 и R2](http://go.microsoft.com/fwlink/?LinkId=215661), на сайте blogs.msdn.com.  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента скрипта в редакторе компонентов скрипта](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
  
  

