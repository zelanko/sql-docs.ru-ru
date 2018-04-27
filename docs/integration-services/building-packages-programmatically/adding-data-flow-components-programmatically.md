---
title: Добавление компонентов потока данных программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: building-packages-programmatically
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow task [Integration Services], components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: c06065cf-43e5-4b6b-9824-7309d7f5e35e
caps.latest.revision: 61
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e0468d1fe76619f91a9d1fe73f7216962c4f5f0d
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="adding-data-flow-components-programmatically"></a>Добавление компонентов потока данных программным образом
  Построение потока данных начинается с добавления компонентов. Затем необходимо настроить эти компоненты и соединить их друг с другом, чтобы образовался поток данных времени выполнения. В этом разделе описывается добавление компонента в задачу потока данных, создание экземпляра компонента времени разработки и последующая настройка компонента. Дополнительные сведения о соединении компонентов см. в статье [Программное соединение компонентов потока данных](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
## <a name="adding-a-component"></a>Добавление компонента  
 Вызовите метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaDataCollection100.New%2A> коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.MainPipeClass.ComponentMetaDataCollection%2A>, чтобы создать новый компонент и добавить его в задачу потока данных. Этот метод возвращает интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> компонента. Однако на этом этапе интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> не содержит сведений, относящихся к какому-либо определенному компоненту. Задайте свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>, чтобы определить тип компонента. Задача потока данных использует значение этого свойства для создания экземпляра компонента во время выполнения.  
  
 Значение, указанное в свойстве <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>, может обозначать идентификатор CLSID, PROGID или свойство <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> компонента. Идентификатор CLSID обычно отображается в окне «Свойства» как значение свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A> компонента. Сведения о получении значений этого свойства и других свойств доступных компонентов см. в разделе [Программный поиск компонентов потока данных](../../integration-services/building-packages-programmatically/discovering-data-flow-components-programmatically.md).  
  
## <a name="adding-a-managed-component"></a>Добавление управляемого компонента  
 Использовать идентификаторы CLSID или PROGID для добавления управляемых компонентов потока данных в поток данных нельзя, поскольку эти значения указывают на оболочку, а не на сам компонент. Вместо этого можно использовать свойство **CreationName** или свойство **AssemblyQualifiedName**, как показано в следующем примере.  
  
 Если требуется использовать свойство **AssemblyQualifiedName**, следует добавить в проект [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ссылку на сборку, содержащую управляемый компонент. Эти сборки отсутствуют в списке на вкладке ".NET" диалогового окна **Добавление ссылки**. В общем случае сборка находится в папке **C:\Program Files\Microsoft SQL Server\100\DTS\PipelineComponents**.  
  
 В число встроенных управляемых компонентов потока данных входят:  
  
-   Источник [!INCLUDE[vstecado](../../includes/vstecado-md.md)]  
  
-   XML-источник  
  
-   назначение DataReader  
  
-   Назначение [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Compact  
  
-   Компонент скрипта  
  
 В следующем образце кода демонстрируются оба способа добавления управляемого компонента в поток данных:  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Microsoft.SqlServer.Dts.Runtime.Package package = new Microsoft.SqlServer.Dts.Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Microsoft.SqlServer.Dts.Runtime.TaskHost thMainPipe = (Microsoft.SqlServer.Dts.Runtime.TaskHost)e;  
      MainPipe dataFlowTask = (MainPipe)thMainPipe.InnerObject;  
  
      // The Application object will be used to obtain the CreationName  
      //  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
      Application app = new Application();  
  
      // Add a first ADO NET source to the data flow.  
      //  The CreationName property requires an Application instance.  
      IDTSComponentMetaData100 component1 = dataFlowTask.ComponentMetaDataCollection.New();  
      component1.Name = "DataReader Source";  
      component1.ComponentClassID = app.PipelineComponentInfos["DataReader Source"].CreationName;  
  
      // Add a second ADO NET source to the data flow.  
      //  The AssemblyQualifiedName property requires a reference to the assembly.  
      IDTSComponentMetaData100 component2 = dataFlowTask.ComponentMetaDataCollection.New();  
      component2.Name = "DataReader Source";  
      component2.ComponentClassID = typeof(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName;  
    }  
  }  
}  
  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' The Application object will be used to obtain the CreationName  
    '  of a PipelineComponentInfo from its PipelineComponentInfos collection.  
    Dim app As New Application()  
  
    ' Add a first ADO NET source to the data flow.  
    '  The CreationName property requires an Application instance.  
    Dim component1 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component1.Name = "DataReader Source"  
    component1.ComponentClassID = app.PipelineComponentInfos("DataReader Source").CreationName  
  
    ' Add a second ADO NET source to the data flow.  
    '  The AssemblyQualifiedName property requires a reference to the assembly.  
    Dim component2 As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component2.Name = "DataReader Source"  
    component2.ComponentClassID = _  
      GetType(Microsoft.SqlServer.Dts.Pipeline.DataReaderSourceAdapter).AssemblyQualifiedName  
  
  End Sub  
  
End Module  
```  
  
## <a name="creating-the-design-time-instance-of-the-component"></a>Создание экземпляра компонента времени разработки  
 Вызовите метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A>, чтобы создать экземпляр компонента времени разработки, определенный свойством <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>. Этот метод возвращает объект <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper>, который является управляемой оболочкой для интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100>.  
  
 При возможности для изменения компонента следует использовать методы экземпляра времени разработки, а не изменять непосредственно метаданные компонента. Хотя некоторые элементы метаданных, например соединения, необходимо задавать непосредственно, обычно не рекомендуется изменять метаданные непосредственно, поскольку при этом не задействуются возможности компонента по отслеживанию и проверке изменений.  
  
## <a name="assigning-connections"></a>Назначение соединений  
 Для некоторых компонентов, например, компонента «Источник OLE DB», требуется соединение с внешним источником данных. Для этой цели используется существующий в пакете объект <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>. Значение свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnectionCollection100.Count%2A> коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A> указывает на число объектов <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager>, необходимых для компонента. Если это число больше нуля, для компонента требуется соединение. Назначьте для компонента диспетчер соединений из пакета, указав свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.ConnectionManager%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeConnection100.Name%2A> первого соединения в коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.RuntimeConnectionCollection%2A>. Обратите внимание на то, что имя диспетчера подключений в коллекции подключений времени выполнения должно совпадать с именем диспетчера подключений, на который ссылается пакет.  
  
## <a name="setting-the-values-of-custom-properties"></a>Задание значений пользовательских свойств  
 После создания экземпляра компонента времени разработки, вызовите метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A>. Этот метод подобен конструктору, поскольку он инициализирует только что созданный компонент, создавая его пользовательские свойства, а также объекты входа и выхода. Нельзя вызывать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A> более одного раза для компонента, поскольку при этом могут быть сброшены настройки компонента и потеряны все изменения, ранее внесенные в его метаданные.  
  
 Коллекция свойств <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.CustomPropertyCollection%2A> компонента содержит коллекцию объектов <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>, относящихся к компоненту. В отличие от других моделей программирования, где свойства объекта всегда доступны для объекта, компоненты заполняют свои коллекции пользовательских свойств только при вызове метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ProvideComponentProperties%2A>. После вызова этого метода используйте метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.SetComponentProperty%2A> экземпляра компонента времени разработки, чтобы присвоить значения его пользовательским свойствам. Этот метод принимает пару имя-значение, идентифицирующую пользовательское свойство, и возвращает ее новое значение.  
  
## <a name="initializing-output-columns"></a>Инициализация выходных столбцов  
 После добавления компонента в задачу и его настройки инициализируйте коллекцию столбцов в свойстве <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100> объекта. Этот шаг имеет непосредственное отношение к компоненту-источнику, однако для компонентов преобразования и назначения может не инициализировать столбцы, поскольку они, как правило, зависят от столбцов, получаемых из вышестоящих компонентов.  
  
 Вызовите метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A>, чтобы инициализировать столбцы на выходах компонента-источника. Так как компоненты не соединяются автоматически с внешними источниками данных, необходимо вызвать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.AcquireConnections%2A> перед вызовом метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReinitializeMetaData%2A>, чтобы обеспечить компоненту доступ к его внешнему источнику данных и возможность заполнить метаданными соответствующий столбец. Наконец, следует вызвать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapperClass.ReleaseConnections%2A>, чтобы освободить соединение.  
  
## <a name="next-step"></a>Следующий шаг  
 После добавления и настройки компонента следующим шагом является создание путей между компонентами, которое рассматривается в разделе [Создание пути между двумя компонентами](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md).  
  
## <a name="sample"></a>Образец  
 В следующем образце кода компонент «Источник OLE DB» добавляется в задачу потока данных, создается экземпляр компонента времени разработки и выполняется настройка свойств компонента. Для этого образца необходима дополнительная ссылка на сборку Microsoft.SqlServer.DTSRuntimeWrap.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Wrapper;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Runtime.Package package = new Runtime.Package();  
      Executable e = package.Executables.Add("STOCK:PipelineTask");  
      Runtime.TaskHost thMainPipe = e as Runtime.TaskHost;  
      MainPipe dataFlowTask = thMainPipe.InnerObject as MainPipe;  
  
      // Add an OLEDB connection manager to the package.  
      ConnectionManager cm = package.Connections.Add("OLEDB");  
      cm.Name = "OLEDB ConnectionManager";  
      cm.ConnectionString = "Data Source=(local);" +   
        "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" +   
        "Integrated Security=SSPI;"  
  
      // Add an OLE DB source to the data flow.  
      IDTSComponentMetaData100 component =   
        dataFlowTask.ComponentMetaDataCollection.New();  
      component.Name = "OLEDBSource";  
      component.ComponentClassID = "DTSAdapter.OleDbSource.1";  
      // You can also use the CLSID of the component instead of the PROGID.  
      //component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
      // Get the design time instance of the component.  
      CManagedComponentWrapper instance = component.Instantiate();  
  
      // Initialize the component  
      instance.ProvideComponentProperties();  
  
      // Specify the connection manager.  
      if (component.RuntimeConnectionCollection.Count > 0)  
      {  
        component.RuntimeConnectionCollection[0].ConnectionManager =   
          DtsConvert.GetExtendedInterface(package.Connections[0]);  
        component.RuntimeConnectionCollection[0].ConnectionManagerID =   
          package.Connections[0].ID;      }  
  
      // Set the custom properties.  
      instance.SetComponentProperty("AccessMode", 2);  
      instance.SetComponentProperty("SqlCommand",   
        "Select * from Production.Product");  
  
      // Reinitialize the metadata.  
      instance.AcquireConnections(null);  
      instance.ReinitializeMetaData();  
      instance.ReleaseConnections();  
  
      // Add other components to the data flow and connect them.  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Wrapper  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
Module Module1  
  
  Sub Main()  
  
    Dim package As Microsoft.SqlServer.Dts.Runtime.Package = _  
      New Microsoft.SqlServer.Dts.Runtime.Package()  
    Dim e As Executable = package.Executables.Add("STOCK:PipelineTask")  
    Dim thMainPipe As Microsoft.SqlServer.Dts.Runtime.TaskHost = _  
      CType(e, Microsoft.SqlServer.Dts.Runtime.TaskHost)  
    Dim dataFlowTask As MainPipe = CType(thMainPipe.InnerObject, MainPipe)  
  
    ' Add an OLEDB connection manager to the package.  
    Dim cm As ConnectionManager = package.Connections.Add("OLEDB")  
    cm.Name = "OLEDB ConnectionManager"  
    cm.ConnectionString = "Data Source=(local);" & _  
      "Initial Catalog=AdventureWorks;Provider=SQLOLEDB.1;" & _  
      "Integrated Security=SSPI;"  
  
    ' Add an OLE DB source to the data flow.  
    Dim component As IDTSComponentMetaData100 = _  
      dataFlowTask.ComponentMetaDataCollection.New()  
    component.Name = "OLEDBSource"  
    component.ComponentClassID = "DTSAdapter.OleDbSource.1"  
    ' You can also use the CLSID of the component instead of the PROGID.  
    'component.ComponentClassID = "{2C0A8BE5-1EDC-4353-A0EF-B778599C65A0}";  
  
    ' Get the design time instance of the component.  
    Dim instance As CManagedComponentWrapper = component.Instantiate()  
  
    ' Initialize the component.  
    instance.ProvideComponentProperties()  
  
    ' Specify the connection manager.  
    If component.RuntimeConnectionCollection.Count > 0 Then  
      component.RuntimeConnectionCollection(0).ConnectionManager = _  
        DtsConvert.GetExtendedInterface(package.Connections(0))  
      component.RuntimeConnectionCollection(0).ConnectionManagerID = _  
        package.Connections(0).ID  
    End If  
  
    ' Set the custom properties.  
    instance.SetComponentProperty("AccessMode", 2)  
    instance.SetComponentProperty("SqlCommand", _  
      "Select * from Production.Product")  
  
    ' Reinitialize the metadata.  
    instance.AcquireConnections(vbNull)  
    instance.ReinitializeMetaData()  
    instance.ReleaseConnections()  
  
    ' Add other components to the data flow and connect them.  
  
  End Sub  
  
End Module  
```  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [EzAPI — обновление для SQL Server 2012](http://go.microsoft.com/fwlink/?LinkId=243223) на сайте blogs.msdn.com.  

## <a name="see-also"></a>См. также:  
 [Программное соединение компонентов потока данных](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)  
  
  
