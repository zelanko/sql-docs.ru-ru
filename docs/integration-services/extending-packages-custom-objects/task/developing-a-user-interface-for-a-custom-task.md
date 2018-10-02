---
title: Разработка пользовательского интерфейса для пользовательской задачи | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom user interfaces [Integration Services]
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- custom tasks [Integration Services], user interface
- custom user interface [Integration Services], custom tasks
- user interface [Integration Services]
- SSIS custom tasks, user interface
ms.assetid: 1e940cd1-c5f8-4527-b678-e89ba5dc398a
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7f191ce84bc89b2958b4d72d6ec3d491e4f34eeb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47689442"
---
# <a name="developing-a-user-interface-for-a-custom-task"></a>Разработка пользовательского интерфейса для пользовательской задачи
  Объектная модель служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] предоставляет разработчикам пользовательских задач удобный способ создания собственного пользовательского интерфейса для задачи, который можно затем интегрировать и вывести в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Пользовательский интерфейс может предоставлять пользователю полезную информацию в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] и помогать пользователям правильно конфигурировать свойства и настройки пользовательской задачи.  
  
 Разработка собственного пользовательского интерфейса задачи требует использования двух важных классов. Эти классы описываются в следующей таблице.  
  
|Class|Описание|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|Атрибут, который идентифицирует управляемую задачу и предоставляет через свои свойства информацию времени разработки, определяющую, каким образом конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] выводит объект и взаимодействует с ним.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|Интерфейс, используемый задачей для того, чтобы связать ее с собственным пользовательским интерфейсом.|  
  
 В данном разделе описывается роль атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> и интерфейса <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> при разработке пользовательского интерфейса для пользовательской задачи и предоставляются подробные сведения о создании, интеграции, развертывании и отладке задачи в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
 Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] предоставляет несколько точек входа в пользовательский интерфейс данной задачи: пользователь может выбрать пункт **Изменить** в контекстном меню, дважды щелкнуть задачу или щелкнуть ссылку **Показать редактор** в нижней части страницы свойств. Когда пользователь получает доступ к одной из этих точек входа, конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] находит и загружает сборку, содержащую пользовательский интерфейс для соответствующей задачи. Пользовательский интерфейс задачи отвечает за создание диалогового окна свойств, которое выводится для пользователя в среде разработки [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].  
  
 Задача и ее пользовательский интерфейс представляют собой отдельные сущности. Их нужно реализовать в отдельных сборках, чтобы уменьшить объем работы по локализации, развертыванию и поддержке. Динамическая библиотека задачи не загружает и не вызывает свой пользовательский интерфейс и вообще ничего о нем не знает, за исключением информации, содержащейся в значениях атрибутов объектов <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>, создаваемых в коде задачи. Это единственная связь между задачей и ее пользовательским интерфейсом.  
  
## <a name="the-dtstask-attribute"></a>Атрибут DtsTask  
 Атрибут <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> включается в код класса задачи, чтобы связать задачу с ее пользовательским интерфейсом. Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] использует свойства атрибута, чтобы определить, каким образом показывать задачу в конструкторе. Свойства включают в себя имя задачи для вывода и значок задачи, если он есть.  
  
 В следующей таблице приводится описание свойств атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.  
  
|Свойство|Описание|  
|--------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>|Выводит имя задачи в области элементов потока управления.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>|Описание задачи (наследуется от <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>). Это свойство показывается во всплывающей подсказке.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A>|Значок выводится в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.RequiredProductLevel%2A>|Если это свойство используется, нужно задать для него одно из значений перечисления <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel>. Например, `RequiredProductLevel = DTSProductLevel.None`.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskContact%2A>|Хранит контактную информацию на случай, если работа задачи потребует технической поддержки.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskType%2A>|Присваивает задаче тип.|  
|Attribute.TypeId|Возвращает уникальный идентификатор для этого атрибута при реализации в производном классе. Дополнительные сведения см. в разделе, посвященном свойству **Attribute.TypeID**, документации по библиотеке классов платформы .NET Framework.|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>|Имя типа сборки, используемое конструктором служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] для загрузки сборки. Это свойство используется для поиска сборки пользовательского интерфейса данной задачи.|  
  
 В следующем примере кода показан код атрибута <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>, расположенный выше определения класса.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
 Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] использует свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> этого атрибута, которое включает в себя имя сборки, имя типа, значения токенов версии, языка, культуры, а также открытого ключа для поиска сборки в глобальном кэше сборок (GAC) и ее загрузки для использования в конструкторе.  
  
 Когда сборка найдена, конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] использует другие свойства атрибута для вывода дополнительной информации о задаче в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] — например, имени, значка и описания задачи.  
  
 Свойства <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> указывают, как задача представляется пользователю. Свойство <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> содержит идентификатор ресурса значка, внедренного в сборку пользовательского интерфейса. Конструктор загружает ресурс значка по идентификатору из сборки и выводит его рядом с именем задачи в области элементов и в области конструктора, когда задача добавлена к пакету. Если задача не предоставляет ресурс значка, конструктор использует для нее значок по умолчанию.  
  
## <a name="the-idtstaskui-interface"></a>Интерфейс IDTSTaskUI  
 Интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> определяет коллекцию методов и свойств, вызываемых конструктором служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] для инициализации и вывода пользовательского интерфейса, связанного с данной задачей. При вызове пользовательского интерфейса задачи конструктор вызывает метод <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A>, реализованный в пользовательском интерфейсе задачи во время разработки, а затем передает коллекции <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> и <xref:Microsoft.SqlServer.Dts.Runtime.Connections> задачи и пакета соответственно в качестве параметров. Коллекции хранятся локально и последовательно используются методом <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A>.  
  
 Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] вызывает метод <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A>, чтобы запросить окно, выводимое в конструкторе. Задача создает экземпляр окна, содержащего пользовательский интерфейс задачи, и возвращает пользовательский интерфейс конструктору для вывода. Обычно окну через перегруженный конструктор предоставляются объекты <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> и <xref:Microsoft.SqlServer.Dts.Runtime.Connections>, чтобы их можно было использовать для настройки задачи.  
  
 Конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] вызывает метод <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> пользовательского интерфейса задачи, чтобы вывести пользовательский интерфейс данной задачи. Пользовательский интерфейс задачи возвращает после вызова данного метода форму Windows, и конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] выводит эту форму как модальное диалоговое окно. После закрытия формы конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] исследует значение свойства **DialogResult** формы, чтобы определить, была ли задача изменена и следует ли сохранить эти изменения. Если значение свойства **DialogResult** равно **OK**, конструктор служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] вызывает методы сохранения задачи, чтобы сохранить изменения; в противном случае изменения отменяются.  
  
 В приведенном образце кода реализован интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>. Предполагается существование класса форм Windows с именем SampleTaskForm.  
  
```csharp  
using System;  
using System.Windows.Forms;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Design;  
  
namespace Sample  
{  
   public class HelloWorldTaskUI : IDtsTaskUI  
   {  
      TaskHost   taskHost;  
      Connections connections;  
      public void Initialize(TaskHost taskHost, IServiceProvider serviceProvider)  
      {  
         this.taskHost = taskHost;  
         IDtsConnectionService cs = serviceProvider.GetService  
         ( typeof( IDtsConnectionService ) ) as   IDtsConnectionService;   
         this.connections = cs.GetConnections();  
      }  
      public ContainerControl GetView()  
      {  
        return new HelloWorldTaskForm(this.taskHost, this.connections);  
      }  
     public void Delete(IWin32Window parentWindow)  
     {  
     }  
     public void New(IWin32Window parentWindow)  
     {  
     }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Design  
Imports System.Windows.Forms  
  
Public Class HelloWorldTaskUI  
  Implements IDtsTaskUI  
  
  Dim taskHost As TaskHost  
  Dim connections As Connections  
  
  Public Sub Initialize(ByVal taskHost As TaskHost, ByVal serviceProvider As IServiceProvider) _  
    Implements IDtsTaskUI.Initialize  
  
    Dim cs As IDtsConnectionService  
  
    Me.taskHost = taskHost  
    cs = DirectCast(serviceProvider.GetService(GetType(IDtsConnectionService)), IDtsConnectionService)  
    Me.connections = cs.GetConnections()  
  
  End Sub  
  
  Public Function GetView() As ContainerControl _  
    Implements IDtsTaskUI.GetView  
  
    Return New HelloWorldTaskForm(Me.taskHost, Me.connections)  
  
  End Function  
  
  Public Sub Delete(ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.Delete  
  
  End Sub  
  
  Public Sub [New](ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.[New]  
  
  End Sub  
  
End Class  
```  
 
## <a name="see-also"></a>См. также:  
 [Создание пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/creating-a-custom-task.md)   
 [Создание кода пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/coding-a-custom-task.md)   
 [Разработка пользовательского интерфейса для пользовательской задачи](../../../integration-services/extending-packages-custom-objects/task/developing-a-user-interface-for-a-custom-task.md)  
  
  
