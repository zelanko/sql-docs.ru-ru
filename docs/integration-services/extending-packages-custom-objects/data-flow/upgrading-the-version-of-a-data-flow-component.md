---
title: Обновление версии компонента потока данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1a30138401f1a5e81b710278de46dad1be383889
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47750832"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a>Обновление версии компонента потока данных
  Пакеты, созданные с устаревшей версией компонента, могут содержать недопустимые метаданные, например, пользовательские свойства, применение которых было изменено в более новых версиях компонента. Можно переопределить метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>, чтобы обеспечить обновление метаданных, которые были сохранены в ранее созданных пакетах, для соответствия текущим свойствам компонента.  
  
> [!NOTE]  
>  При перекомпиляции пользовательского компонента для более новой версии служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] нет необходимости изменять значение свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A>, если свойства компонента не изменялись.  
  
## <a name="example"></a>Пример  
 В следующем образце содержится код из версии 2.0 вымышленного компонента потока данных. Номер новой версии определен в свойстве <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> атрибута <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Компонент имеет свойство, которым определяется обработка числовых значений, превышающих заданное пороговое значение. В версии 1.0 вымышленного компонента это свойство называлось `RaiseErrorOnInvalidValue` и принимало логическое значение (true или false). В версии 2.0 вымышленного компонента свойство было переименовано в `InvalidValueHandling` и настроено для приема одного из четырех возможных значений, полученных в результате пользовательского перечисления.  
  
 Переопределенный метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> в следующем образце выполняет следующие действия:  
  
-   Возвращает текущую версию компонента.  
  
-   Возвращает предыдущее значение пользовательского свойства.  
  
-   Удаляет прежнее свойство из коллекции пользовательских свойств.  
  
-   Задает значение нового пользовательского свойства на основе значения прежнего свойства (если это возможно).  
  
-   Указывает версию метаданных в соответствии с текущей версией компонента.  
  
> [!NOTE]  
>  Подсистема обработки потока данных передает номер своей версии в метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> через параметр *pipelineVersion*. Этот параметр бесполезен в версии 1.0 служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], но может оказаться полезным в последующих версиях.  
  
 В образце кода используются только два значения перечисления, которые сопоставляются непосредственно с предыдущими логическими значениями пользовательского свойства. Пользователи могут выбрать другие доступные значения перечисления с помощью пользовательского интерфейса компонента, в расширенном редакторе или программным способом. Сведения об отображении значений перечисления для пользовательского свойства в расширенном редакторе см. в подразделе "Создание пользовательских свойств" раздела [Методы времени разработки для компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/design-time-methods-of-a-data-flow-component.md).  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```
