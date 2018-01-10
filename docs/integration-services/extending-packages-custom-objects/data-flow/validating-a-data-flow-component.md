---
title: "Проверка компонента потока данных | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ReinitializeMetaData method
- Validate method
- component validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- data flow components [Integration Services], validating
- validation [Integration Services]
ms.assetid: 1a7d5925-b387-4e31-af7f-c7f3c5151040
caps.latest.revision: "48"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 57133b3aaccbd1f6e3b019c77cb2d2da8178721f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="validating-a-data-flow-component"></a>Проверка компонента потока данных
  Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> предназначен для того, чтобы не допустить исполнения неправильно настроенного компонента. С помощью этого метода можно убедиться, что у компонента есть нужное число входных и выходных объектов, его пользовательские свойства имеют допустимые значения и что любые нужные соединения заданы. Этот метод также используется для проверки правильности типов данных во входной и выходной коллекциях столбцов и что свойство <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSUsageType> всех столбцов настроено в соответствии с типом компонента. Реализация метода в базовом классе участвует в проверке: она проверяет коллекцию входных столбцов компонента, гарантируя, что каждый столбец этой коллекции ссылается на столбец коллекции <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputCollection100> вышестоящего компонента.  
  
## <a name="validate-method"></a>Метод Validate  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> неоднократно вызывается при изменении компонента в конструкторе служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)]. Отзыв для конструктора и пользователей компонента можно обеспечить через возвращаемое значение <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> из перечисления, а также с помощью выводимых предупреждений и сообщений об ошибках. Перечисление <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus> содержит три значения, указывающие на различные степени неудачи, и четвертое, <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISVALID>, которое указывает, что компонент настроен правильно и готов к выполнению.  
  
 Значение <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> указывает, что в данных <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> есть ошибка и компонент может ее исправить. Если компонент обнаруживает ошибку в метаданных, которую может исправить, ее не следует исправлять в методе <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> и во время проверки не следует изменять метаданные <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A>. Вместо этого метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A> должен вернуть только значение <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA>, а компонент должен исправить метаданные с помощью вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>, как будет описано ниже в этом разделе.  
  
 Значение <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISBROKEN> указывает, что компонент содержит ошибку, которую можно исправить, изменив компонент в конструкторе. Такая ошибка обычно вызвана неправильно заданным или настроенным пользовательским свойством или обязательным соединением.  
  
 Последнее значение ошибки — <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_ISCORRUPT>: оно указывает, что компонент обнаружил ошибки, которые могут возникнуть только в случае непосредственного изменения свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> редактированием XML-кода программного пакета или с помощью модели объектов. Например, такая ошибка может возникнуть, если в компоненте добавлен только один входной параметр, но при проверке обнаруживается, что в метаданных <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ComponentMetaData%2A> их указано несколько. Ошибки, выдающие это возвращаемое значение, можно исправить только сбросом компонента с помощью кнопки **Сброс** в диалоговом окне **Расширенный редактор**.  
  
 Кроме возвращения кода ошибки, компоненты предоставляют отзыв с помощью предупреждений и сообщений об ошибках, выдаваемых во время проверки. Этот механизм поддерживают методы <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireWarning%2A> и <xref:Microsoft.SqlServer.Dts.Runtime.IDTSComponentEvents.FireError%2A>. При их вызове сообщения о соответствующих событиях публикуются в окне **Список ошибок** среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Затем разработчики компонента могут предоставить отзыв пользователям о происшедших ошибках и, по возможности, о способах их исправления.  
  
 В следующем примере кода показана переопределенная реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>.  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    bool pbCancel = false;  
  
    // Validate that there is one input.  
    if (ComponentMetaData.InputCollection.Count != 1)  
    {  
    ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, out pbCancel);  
    return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Validate that the UserName custom property is set.  
    if (ComponentMetaData.CustomPropertyCollection["UserName"].Value == null || ((string)ComponentMetaData.CustomPropertyCollection["UserName"].Value).Length == 0)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISBROKEN;  
    }  
  
    // Validate that there is one output.  
    if (ComponentMetaData.OutputCollection.Count != 1)  
    {  
        ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, out pbCancel);  
        return DTSValidationStatus.VS_ISCORRUPT;  
    }  
  
    // Let the base class verify that the input column reflects the output   
    // of the upstream component.  
    return base.Validate();  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
  
 Dim pbCancel As Boolean = False  
  
 ' Validate that there is one input.  
 If Not (ComponentMetaData.InputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of inputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Validate that the UserName custom property is set.  
 If ComponentMetaData.CustomPropertyCollection("UserName").Value Is Nothing OrElse CType(ComponentMetaData.CustomPropertyCollection("UserName").Value, String).Length = 0 Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "The UserName property must be set.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISBROKEN   
 End If   
  
 ' Validate that there is one output.  
 If Not (ComponentMetaData.OutputCollection.Count = 1) Then   
   ComponentMetaData.FireError(0, ComponentMetaData.Name, "Incorrect number of outputs.", "", 0, pbCancel)   
   Return DTSValidationStatus.VS_ISCORRUPT   
 End If   
  
 ' Let the base class verify that the input column reflects the output   
 ' of the upstream component.  
  
 Return MyBase.Validate   
  
End Function  
```  
  
## <a name="reinitializemetadata-method"></a>Метод ReinitializeMetaData  
 Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A> вызывается конструктором служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)] каждый раз, когда компонент возвращает значение <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.DTSValidationStatus.VS_NEEDSNEWMETADATA> после вызова метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.Validate%2A>. Компоненты должны содержать код, который обнаруживает и устраняет проблемы, выявленные компонентом во время проверки.  
  
 В этом примере показан компонент, обнаруживающий недостатки в ходе проверки и исправляющий их с помощью метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ReinitializeMetaData%2A>.  
  
```csharp  
private bool areInputColumnsValid = true;  
public override DTSValidationStatus Validate()  
{  
    IDTSInput100 input = ComponentMetaData.InputCollection[0];  
    IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
    bool Cancel = false;  
    foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
    {  
        try  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
        }  
        catch  
        {  
            ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, out Cancel);  
            areInputColumnsValid = false;  
            return DTSValidationStatus.VS_NEEDSNEWMETADATA;  
        }  
    }  
  
    return DTSValidationStatus.VS_ISVALID;  
}  
public override void ReinitializeMetaData()  
{  
    if (!areInputColumnsValid)  
    {  
        IDTSInput100 input = ComponentMetaData.InputCollection[0];  
        IDTSVirtualInput100 vInput = input.GetVirtualInput();  
  
        foreach (IDTSInputColumn100 column in input.InputColumnCollection)  
        {  
            IDTSVirtualInputColumn100 vColumn = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID);  
  
            if (vColumn == null)  
                input.InputColumnCollection.RemoveObjectByID(column.ID);  
        }  
        areInputColumnsValid = true;  
    }  
}  
```  
  
```vb  
Private areInputColumnsValid As Boolean = True   
  
Public  Overrides Function Validate() As DTSValidationStatus   
 Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
 Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
 Dim Cancel As Boolean = False   
 For Each column As IDTSInputColumn100 In input.InputColumnCollection   
   Try   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
   Catch   
     ComponentMetaData.FireError(0, ComponentMetaData.Name, "The input column " + column.IdentificationString + " does not match a column in the upstream component.", "", 0, Cancel)   
     areInputColumnsValid = False   
     Return DTSValidationStatus.VS_NEEDSNEWMETADATA   
   End Try   
 Next   
 Return DTSValidationStatus.VS_ISVALID   
End Function   
  
Public  Overrides Sub ReinitializeMetaData()   
 If Not areInputColumnsValid Then   
   Dim input As IDTSInput100 = ComponentMetaData.InputCollection(0)   
   Dim vInput As IDTSVirtualInput100 = input.GetVirtualInput   
   For Each column As IDTSInputColumn100 In input.InputColumnCollection   
     Dim vColumn As IDTSVirtualInputColumn100 = vInput.VirtualInputColumnCollection.GetVirtualInputColumnByLineageID(column.LineageID)   
     If vColumn Is Nothing Then   
       input.InputColumnCollection.RemoveObjectByID(column.ID)   
     End If   
   Next   
   areInputColumnsValid = True   
 End If   
End Sub  
```  
  
