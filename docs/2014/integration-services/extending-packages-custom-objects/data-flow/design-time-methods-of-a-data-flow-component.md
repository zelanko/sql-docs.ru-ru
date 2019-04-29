---
title: Методы времени разработки для компонента потока данных | Документы Майкрософт
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
- custom data flow components [Integration Services], method execution sequence
- ProcessInput method
- method execution sequence [Integration Services]
- PrimeOutput method
- data flow components [Integration Services], method execution sequence
ms.assetid: b5a121a1-b87c-441b-a42c-2cec628dc81c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7d7d1a2d3b62578fc2fd627aea32112c218895d3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896264"
---
# <a name="design-time-methods-of-a-data-flow-component"></a>Методы времени разработки для компонента потока данных
  Перед выполнением задача потока данных считается находящейся в состоянии времени разработки, поскольку она подвергается добавочным изменениям. К таким изменениям относятся добавление или удаление компонентов, добавление или удаление объектов пути, которые соединяют компоненты, и изменения в метаданных компонентов. При изменении метаданных компонент может отслеживать их и выполнять ответные действия. Например, компонент может не допускать внесения определенных изменений или вносить дополнительные изменения в ответ на изменение. Во время разработки конструктор взаимодействует с компонентом через интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> времени разработки.  
  
## <a name="design-time-implementation"></a>Реализация времени разработки  
 Интерфейс времени разработки компонента описывается интерфейсом <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100>. Хотя нельзя явным образом реализовать этот интерфейс, знакомство с методами, определенными в этом интерфейсе, поможет понять, какие методы базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> соответствуют экземпляру компонента времени разработки.  
  
 При загрузке компонента в среду [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] создается экземпляр компонента времени разработки, и при изменении компонента вызываются методы интерфейса <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100>. Реализация базового класса позволяет переопределить только те методы, которые необходимы для компонента. Во многих случаях можно переопределить эти методы, чтобы предотвратить внесение неправильных изменений в компонент. Например, чтобы не дать пользователям возможности добавлять выход в компонент, переопределите метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.InsertOutput%2A>. В противном случае при вызове реализации этого метода базовым классом он добавляет выход в компонент.  
  
 Независимо от предназначения или функциональности компонента, следует переопределить методы <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>, <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>. Дополнительные сведения о <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> и <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> см. в разделе [Проверка компонента потока данных](validating-a-data-flow-component.md).  
  
## <a name="providecomponentproperties-method"></a>Метод ProvideComponentProperties  
 Инициализация компонента происходит в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>. Этот метод вызывается конструктором служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] при добавлении компонента в задачу потока данных. Он аналогичен конструктору классов. Разработчикам компонентов следует создавать и инициализировать свои входы, выходы и пользовательские свойства во время вызова этого метода. Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A> отличается от конструктора тем, что не вызывается каждый раз при создании экземпляра компонента времени разработки или времени выполнения.  
  
 Реализация этого метода базового класса добавляет вход и выход в компонент и присваивает идентификатор входа в качестве значения свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutput100.SynchronousInputID%2A>. Однако в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] объекты входа и выхода, добавленные базовым классом, не именуются. Успешная загрузка пакетов, содержащих компонент с объектами входа или выхода, свойство Name которых не задано, невозможна. Поэтому при использовании базовой реализации нужно явным образом назначить значения свойству Name входа и выхода по умолчанию.  
  
```csharp  
public override void ProvideComponentProperties()  
{  
    /// TODO: Reset the component.  
    /// TODO: Add custom properties.  
    /// TODO: Add input objects.  
    /// TODO: Add output objects.  
}  
```  
  
```vb  
Public Overrides Sub ProvideComponentProperties()  
    ' TODO: Reset the component.  
    ' TODO: Add custom properties.  
    ' TODO: Add input objects.  
    ' TODO: Add output objects.  
End Sub  
```  
  
### <a name="creating-custom-properties"></a>Создание пользовательских свойств  
 Разработчики компонентов должны добавлять пользовательские свойства (<xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProvideComponentProperties%2A>) в компонент с помощью вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100>. Пользовательские свойства не имеют свойства типа данных. Тип данных пользовательского свойства определяется типом данных значения, которое присвоено его свойству <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.Value%2A>. Однако после присвоения пользовательскому свойству исходного значения присвоить ему значение с другим типом данных нельзя.  
  
> [!NOTE]  
>  Интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100> обеспечивает ограниченную поддержку значений свойств типа `Object`. Единственный объект, который можно сохранять в качестве значения пользовательского свойства, – это массив простых типов, например, строк или целых чисел.  
  
 Можно указать, что пользовательское свойство поддерживает выражения свойств, присвоив его свойству <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.ExpressionType%2A> в качестве значения `CPET_NOTIFY` из перечисления <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSCustomPropertyExpressionType>, как показано в следующем примере. Нет необходимости добавлять какой-либо код для обработки или проверки выражения свойства, введенного пользователем. Можно задать значение для свойства по умолчанию, проверить его значение, прочитать и использовать это значение обычным образом.  
  
```csharp  
IDTSCustomProperty100 myCustomProperty;  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY;  
```  
  
```vb  
Dim myCustomProperty As IDTSCustomProperty100  
...  
myCustomProperty.ExpressionType = DTSCustomPropertyExpressionType.CPET_NOTIFY  
```  
  
 Вы можете ограничить пользователей выбором значения для пользовательского свойства из перечисления с помощью <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.TypeConverter%2A> свойства, как показано в следующем примере предполагается, что было определено общее перечисление с именем `MyValidValues`.  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the type with the custom property.  
customProperty.TypeConverter = typeof(MyValidValues).AssemblyQualifiedName;  
// Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne;    
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the type with the custom property.  
customProperty.TypeConverter = GetType(MyValidValues).AssemblyQualifiedName   
' Now you can use the enumeration values directly.  
customProperty.Value = MyValidValues.ValueOne  
```  
  
 Дополнительные сведения см. в разделах "Преобразование обобщенного типа" и "Реализация преобразователя типов" [библиотеки MSDN](https://go.microsoft.com/fwlink/?LinkId=7022).  
  
 С помощью свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> в качестве значения пользовательского свойства можно указать диалоговое окно пользовательского редактора, как показано в следующем примере. Сначала необходимо создать пользовательский редактор типов, наследующий от `System.Drawing.Design.UITypeEditor`, если не удается найти существующий класс редактора типов пользовательских интерфейсов, отвечающий потребностям пользователя.  
  
```csharp  
public class MyCustomTypeEditor : UITypeEditor  
{  
...  
}  
```  
  
```vb  
Public Class MyCustomTypeEditor  
  Inherits UITypeEditor   
  ...  
End Class  
```  
  
 Затем укажите этот класс в качестве значения для свойства <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSCustomProperty100.UITypeEditor%2A> пользовательского свойства.  
  
```csharp  
IDTSCustomProperty100 customProperty = outputColumn.CustomPropertyCollection.New();  
customProperty.Name = "My Custom Property";  
// This line associates the editor with the custom property.  
customProperty.UITypeEditor = typeof(MyCustomTypeEditor).AssemblyQualifiedName;  
```  
  
```vb  
Dim customProperty As IDTSCustomProperty100 = outputColumn.CustomPropertyCollection.New   
customProperty.Name = "My Custom Property"   
' This line associates the editor with the custom property.  
customProperty.UITypeEditor = GetType(MyCustomTypeEditor).AssemblyQualifiedName  
```  
  
 Дополнительные сведения см. в разделе "Реализация редактора типов пользовательских интерфейсов" [библиотеки MSDN](https://go.microsoft.com/fwlink/?LinkId=7022).  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Методы времени выполнения для компонента потока данных](run-time-methods-of-a-data-flow-component.md)  
  
  
