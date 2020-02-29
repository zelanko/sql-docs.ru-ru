---
title: Разработка пользовательского интерфейса для компонента потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow components [Integration Services], custom editors
- user interfaces [Integration Services]
- custom data flow components [Integration Services], custom editors
- custom component editors [Integration Services]
- IDtsComponentUI interface
- UITypeName property
- custom user interface [Integration Services], custom data flow component
- editors [Integration Services]
ms.assetid: 10b829a1-609b-42e3-9070-cfe5a2bb698c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 760e4c00401e42b6d6ccca8bd7c7acd7ec0d5b86
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176339"
---
# <a name="developing-a-user-interface-for-a-data-flow-component"></a>Разработка пользовательского интерфейса для компонента потока данных
  Разработчики компонентов могут включить для компонента настраиваемый пользовательский интерфейс, отображающийся в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] во время изменения компонента. Реализация пользовательского интерфейса обеспечивает возможность получать уведомления, когда компонент добавляется или удаляется из задачи потока данных или при вызове справки по компоненту.

 Если не создать для компонента пользовательский интерфейс, пользователи смогут настраивать компонент и его свойства с помощью расширенного редактора. Можно при необходимости убедиться, что расширенный редактор позволяет пользователям правильно изменять значения пользовательских свойств, с помощью свойств <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>. Дополнительные сведения см. в пункте "Создание пользовательских свойств" раздела [Методы времени разработки для компонента потока данных](design-time-methods-of-a-data-flow-component.md).

## <a name="setting-the-uitypename-property"></a>Указание свойства UITypeName
 Чтобы обеспечить пользовательский интерфейс, разработчик должен указать в качестве свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> атрибута <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> имя класса, реализующего интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>. Если это свойство задается компонентом, службы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] загружаются и вызывают пользовательский интерфейс при изменении компонента в конструкторе [!INCLUDE[ssIS](../../../includes/ssis-md.md)].

 Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A> представляет собой разделенную запятыми строку, указывающую полное имя типа. В следующем списке показаны по порядку элементы, указывающие тип.

-   Имя типа

-   Имя сборки

-   Версия файла

-   Язык и региональные параметры

-   Токен открытого ключа

 В следующем примере кода показан класс, производный от базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> и задающий свойство <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.UITypeName%2A>.

```csharp
[DtsPipelineComponent(
DisplayName="SampleComponent",
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...",
ComponentType = ComponentType.Transform)]
public class SampleComponent : PipelineComponent
{
//TODO: Implement the component here.
}
```

```vb
<DtsPipelineComponent(DisplayName="SampleComponent", _
UITypeName="MyNamespace.MyComponentUIClassName,MyAssemblyName,Version=1.0.0.0,Culture=neutral,PublicKeyToken=abcd...", ComponentType=ComponentType.Transform)> _ 
Public Class SampleComponent 
 Inherits PipelineComponent 
End Class
```

## <a name="implementing-the-idtscomponentui-interface"></a>Реализация интерфейса IDtsComponentUI
 Интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI> содержит методы, которые конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] вызывает при добавлении, удалении и изменении компонента. Разработчики компонентов могут включить в свои реализации код этих методов для взаимодействия с пользователями компонента.

 Этот класс обычно реализуется в сборке, отдельной от самого компонента. Хотя использование отдельной сборки необязательно, это позволяет разработчикам создавать и развертывать компонент и пользовательский интерфейс независимо, а также сохранять небольшой размер двоичного кода компонента.

 Реализация пользовательского интерфейса предоставляет разработчику больше возможностей по управлению компонентом во время изменения в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Например, компонент может добавить код в метод <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A>, который вызывается при первом добавлении компонента в задачу потока данных, и открыть мастер, помогающий пользователю выполнить первичную настройку компонента.

 После создания класса, реализующего интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>, необходимо добавить код, отвечающий на взаимодействие пользователя с компонентом. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> предоставляет интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> компонента и вызывается перед методами <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.New%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A>. Эта ссылка должна быть сохранена в переменной закрытого члена класса и использоваться для последующих изменений метаданных компонента.

## <a name="modifying-a-component-and-persisting-changes"></a>Изменение компонента и устойчивые изменения
 Интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> передается в качестве параметра методу <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A>. Эта ссылка должна кэшироваться в переменной члена кодом пользовательского интерфейса, а затем использоваться для изменения компонента в ответ на взаимодействие пользователя с интерфейсом.

 Хотя можно изменить компонент напрямую с помощью интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100>, лучше создать экземпляр <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.Instantiate%2A>. При непосредственном изменении компонента с помощью интерфейса проверочная защита компонента обходится. Преимуществом использования экземпляра среды разработки для проектирования компонента с помощью <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.CManagedComponentWrapper> является возможность удостовериться, что компонент может управлять внесенными в него изменениями.

 Возвращаемое значение метода <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> определяет, сохранились ли или отменены изменения, внесенные в компонент. Если метод возвращает значение `false`, все изменения отменяются; при значении `true` изменения в компоненте сохраняются, а пакет помечается как нуждающийся в сохранении.

### <a name="using-the-services-of-the-ssis-designer"></a>Использование служб конструктора служб SSIS
 Параметр `IServiceProvider` метода <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Initialize%2A> предоставляет доступ к следующим службам конструктора служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].

|Служба|Описание|
|-------------|-----------------|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsClipboardService>|Используется для определения, был ли компонент создан в ходе операции копирования и вставки или вырезания и вставки.|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionService>|Используется для доступа к существующим соединениям или для создания новых соединений в пакете.|
|<xref:Microsoft.SqlServer.Dts.Design.IErrorCollectionService>|Используется для получения событий из компонентов потока данных, если требуется зафиксировать все возникающие ошибки и предупреждения, а не только получить последнее сообщение об ошибке или предупреждение.|
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsVariableService>|Используется для доступа к существующим переменным или для создания новых переменных в пакете.|
|<xref:Microsoft.SqlServer.Dts.Design.IDtsPipelineEnvironmentService>|Используется компонентами потока данных для доступа к родительской задаче потока данных и другим компонентам в потоке данных. Эту функцию можно использовать для разработки такого компонента, как мастер медленно изменяющихся измерений, при необходимости создающего дополнительные компоненты потока данных.|

 Эти службы предоставляют разработчикам компонентов возможность доступа к объектам и создания объектов в пакете, в котором загружен компонент.

## <a name="sample"></a>Образец
 В следующем примере кода показана интеграция класса пользовательского интерфейса, реализующего интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>, и форма Windows, служащая редактором компонента.

### <a name="custom-user-interface-class"></a>Собственный класс пользовательского интерфейса
 В следующем примере кода показан класс, реализующий интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI>. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A> создает редактор компонента и отображает форму. Возвращаемое формой значение определяет, сохраняются ли изменения, внесенные в компонент.

```csharp
using System;
using System.Windows.Forms;
using Microsoft.SqlServer.Dts.Runtime;
using Microsoft.SqlServer.Dts.Pipeline.Design;
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;

namespace Microsoft.Samples.SqlServer.Dts
{
    public class SampleComponentUI : IDtsComponentUI
    {
        IDTSComponentMetaData100 md;
        IServiceProvider sp;

        public void Help(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void New(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public void Delete(System.Windows.Forms.IWin32Window parentWindow)
        {
        }
        public bool Edit(System.Windows.Forms.IWin32Window parentWindow, Variables vars, Connections cons)
        {
            // Create and display the form for the user interface.
            SampleComponentUIForm componentEditor = new SampleComponentUIForm(cons, vars, md);

            DialogResult result  = componentEditor.ShowDialog(parentWindow);

            if (result == DialogResult.OK)
                return true;

            return false;
        }
        public void Initialize(IDTSComponentMetaData100 dtsComponentMetadata, IServiceProvider serviceProvider)
        {
            // Store the component metadata.
            this.md = dtsComponentMetadata;
        }
    }
}
```

```vb
Imports System 
Imports System.Windows.Forms 
Imports Microsoft.SqlServer.Dts.Runtime 
Imports Microsoft.SqlServer.Dts.Pipeline.Design 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Class SampleComponentUI 
 Implements IDtsComponentUI 
   Private md As IDTSComponentMetaData100 
   Private sp As IServiceProvider 

   Public Sub Help(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub New(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Sub Delete(ByVal parentWindow As System.Windows.Forms.IWin32Window) 
   End Sub 

   Public Function Edit(ByVal parentWindow As System.Windows.Forms.IWin32Window, ByVal vars As Variables, ByVal cons As Connections) As Boolean 
     ' Create and display the form for the user interface.
     Dim componentEditor As SampleComponentUIForm = New SampleComponentUIForm(cons, vars, md) 
     Dim result As DialogResult = componentEditor.ShowDialog(parentWindow) 
     If result = DialogResult.OK Then 
       Return True 
     End If 
     Return False 
   End Function 

   Public Sub Initialize(ByVal dtsComponentMetadata As IDTSComponentMetaData100, ByVal serviceProvider As IServiceProvider) 
     Me.md = dtsComponentMetadata 
   End Sub 
 End Class 

End Namespace
```

### <a name="custom-editor"></a>Пользовательский редактор
 В следующем примере кода показана реализация формы Windows, отображающейся во время вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.Design.IDtsComponentUI.Edit%2A>.

```csharp
using System;
using System.Drawing;
using System.Collections;
using System.ComponentModel;
using System.Windows.Forms;
using System.Data;

using Microsoft.SqlServer.Dts.Pipeline.Wrapper;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.Samples.SqlServer.Dts
{
    public partial class SampleComponentUIForm : System.Windows.Forms.Form
    {
        private Connections connections;
        private Variables variables;
        private IDTSComponentMetaData100 metaData;
        private CManagedComponentWrapper designTimeInstance;
        private System.ComponentModel.IContainer components = null;

        public SampleComponentUIForm( Connections cons, Variables vars, IDTSComponentMetaData100 md)
        {
            variables = vars;
            connections = cons;
            metaData = md;
        }

        private void btnOk_Click(object sender, System.EventArgs e)
        {
            if (designTimeInstance == null)
                designTimeInstance = metaData.Instantiate();

            designTimeInstance.SetComponentProperty( "CustomProperty", txtCustomPropertyValue.Text);

            this.Close();
        }

        private void btnCancel_Click(object sender, System.EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System 
Imports System.Drawing 
Imports System.Collections 
Imports System.ComponentModel 
Imports System.Windows.Forms 
Imports System.Data 
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper 
Imports Microsoft.SqlServer.Dts.Runtime 

Namespace Microsoft.Samples.SqlServer.Dts 

 Public Partial Class SampleComponentUIForm 
  Inherits System.Windows.Forms.Form 
   Private connections As Connections 
   Private variables As Variables 
   Private metaData As IDTSComponentMetaData100 
   Private designTimeInstance As CManagedComponentWrapper 
   Private components As System.ComponentModel.IContainer = Nothing 

   Public Sub New(ByVal cons As Connections, ByVal vars As Variables, ByVal md As IDTSComponentMetaData100) 
     variables = vars 
     connections = cons 
     metaData = md 
   End Sub 

   Private Sub btnOk_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     If designTimeInstance Is Nothing Then 
       designTimeInstance = metaData.Instantiate 
     End If 
     designTimeInstance.SetComponentProperty("CustomProperty", txtCustomPropertyValue.Text) 
     Me.Close 
   End Sub 

   Private Sub btnCancel_Click(ByVal sender As Object, ByVal e As System.EventArgs) 
     Me.Close 
   End Sub 
 End Class 

End Namespace
```

![Значок Integration Services (маленький)](../../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [Создание пользовательского компонента потока данных](creating-a-custom-data-flow-component.md)


