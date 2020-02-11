---
title: Разработка компонентов потоков данных с несколькими входами | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
ms.assetid: 3c7b50e8-2aa6-4f6a-8db4-e8293bc21027
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 74bcf1549cdd97752c805f1c6a9cc774ef1a9e52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62896034"
---
# <a name="developing-data-flow-components-with-multiple-inputs"></a>Разработка компонентов потоков данных с несколькими входами
  Компонент потока данных с несколькими входами может использовать чрезмерное количество ресурсов памяти в случае неравномерного поступления данных из нескольких входов этого потока. При разработке пользовательского компонента потока данных, поддерживающего два или более входов, нагрузку на ресурсы памяти можно контролировать с помощью следующих элементов в пространстве имен Microsoft.SqlServer.Dts.Pipeline:  
  
-   Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> класса <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Задайте значение этого свойства равным `true`, если необходимо реализовать код, который требуется пользовательскому компоненту потока данных для управления данными, поступающими с неравномерной скоростью.  
  
-   Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Необходимо обеспечить реализацию этого метода, если для свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> задано значение `true`. Если реализация не будет предоставлена, то подсистема обработки потока данных сформирует исключение во время выполнения.  
  
-   Метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>. Также необходимо обеспечить реализацию этого метода, если для свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> задано значение `true`, а пользовательский компонент поддерживает более двух входов. Если реализация не будет предоставлена, то подсистема обработки потока данных сформирует исключение во время выполнения при подключении пользователем более двух входов.  
  
 Совместно эти элементы позволяют разработать решение управления нагрузкой на ресурсы памяти схожее с решением, разработанным корпорацией Майкрософт для преобразований «Слияние» и «Соединение слиянием».  
  
## <a name="setting-the-supportsbackpressure-property"></a>Настройка свойства SupportsBackPressure  
 Первым этапом реализации усовершенствованного управления ресурсами памяти для пользовательского компонента потока данных, поддерживающего несколько входов, является задание значения свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> равным `true` в <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Если значение <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> равно `true`, подсистема обработки потока данных вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> и, при наличии более двух входов, также вызывает <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> во время выполнения.  
  
### <a name="example"></a>Пример  
 В следующем примере реализация <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> задает значение <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> равным `true`.  
  
```csharp  
[DtsPipelineComponent(ComponentType = ComponentType.Transform,  
        DisplayName = "Shuffler",  
        Description = "Shuffle the rows from input.",  
        SupportsBackPressure = true,  
        LocalizationType = typeof(Localized),  
        IconResource = "Microsoft.Samples.SqlServer.Dts.MIBPComponent.ico")  
]  
public class Shuffler : Microsoft.SqlServer.Dts.Pipeline.PipelineComponent  
        {  
          ...  
        }  
```  
  
## <a name="implementing-the-isinputready-method"></a>Реализация метода IsInputReady  
 При задании значения свойства <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.SupportsBackPressure%2A> равным `true` в объекте <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>, также необходимо обеспечить реализацию для метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
> [!NOTE]  
>  Реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> не должна вызывать реализации базового класса. Реализация этого метода по умолчанию в базовом классе просто вызывает исключение `NotImplementedException`.  
  
 Во время реализации этого метода нужно задать состояние элемента в массиве *canProcess* типа Boolean для каждого входа компонента. (Входные данные идентифицируются по их значениям ИДЕНТИФИКАТОРов в массиве *инпутидс* .) Если для элемента в массиве *canProcess* задано значение `true` для входа, подсистема обработки потока данных вызывает <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> метод компонента и предоставляет дополнительные данные для указанных входных данных.  
  
 Пока доступны более вышестоящий объем данных, значение элемента массива *canProcess* по крайней мере для одного входного параметра всегда должно быть `true`, или обработка останавливается.  
  
 Подсистема обработки потока данных вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> до отправки всех буферов с данными для определения входов, ожидающих получения дополнительных данных. Если возвращаемое значение указывает на блокировку входа, подсистема обработки потока данных временно кэширует дополнительные буферы данных для этого входа вместо отправки их компоненту.  
  
> [!NOTE]  
>  Не следует вызывать методы <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> или <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> в собственном коде. Подсистема обработки потока данных вызывает эти методы класса `PipelineComponent`, которые переопределяются при запуске подсистемой обработки потока данных компонента.  
  
### <a name="example"></a>Пример  
 В следующем примере реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> указывает на ожидание входом приема дополнительных данных при соблюдении следующих условий:  
  
-   Для входа доступны дополнительные данные выше по уровню обработки (`!inputEOR`).  
  
-   В буферах, уже полученных компонентом (`inputBuffers[inputIndex].CurrentRow() == null`), сейчас отсутствуют данные, доступные для обработки для входа.  
  
 Если входные данные ожидают получения дополнительных данных, компонент потока данных показывает это путем установки `true` значения элемента в массиве *canProcess* , соответствующего этому входу.  
  
 И наоборот, если у компонента все еще имеются данные, доступные для обработки, для входа, в примере обработка входа приостанавливается. В этом примере для `false` этого устанавливается значение элемента в массиве *canProcess* , соответствующее входным данным.  
  
```csharp  
public override void IsInputReady(int[] inputIDs, ref bool[] canProcess)  
{  
    for (int i = 0; i < inputIDs.Length; i++)  
    {  
        int inputIndex = ComponentMetaData.InputCollection.GetObjectIndexByID(inputIDs[i]);  
  
        canProcess[i] = (inputBuffers[inputIndex].CurrentRow() == null)  
            && !inputEOR[inputIndex];  
    }  
}  
```  
  
 В предыдущем примере использовался массив `inputEOR` типа Boolean для указания наличия дополнительных восходящих данных, доступных для каждого входа. `EOR` в имени массива представляет «конец набора строк» и ссылается на свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> буферов потока данных. В части примера, не приведенной здесь, метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> проверяет значение свойства <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.EndOfRowset%2A> для всех получаемых буферов данных. Если значение `true` указывает на отсутствие дополнительных данных с предыдущего этапа для входа, значение элемента массива `inputEOR` для этого входа задается в примере равным `true`. В этом примере <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> метода задается значение соответствующего элемента в массиве `false` *canProcess* для входных данных, если значение элемента `inputEOR` массива указывает на то, что для входных данных больше не доступно ни одного вышестоящего объекта.  
  
## <a name="implementing-the-getdependentinputs-method"></a>Реализация метода GetDependentInputs  
 Если пользовательский компонент потока данных поддерживает более двух входов, также необходимо обеспечить реализацию для метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>.  
  
> [!NOTE]  
>  Реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> не должна вызывать реализации базового класса. Реализация этого метода по умолчанию в базовом классе просто вызывает исключение `NotImplementedException`.  
  
 Подсистема обработки потока данных вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> только в случаях, когда пользователь подключает к компоненту более двух входов. Если компонент <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> имеет только два входа, а метод указывает, что один вход заблокирован (*canProcess* = `false`), подсистема обработки потока данных знает, что другие входные данные ожидают получения дополнительных данных. Однако при наличии более двух входов и в случае, если метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> указывает на блокировку одного из входов, дополнительный код в <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> указывает входы, ожидающие приема дополнительных данных.  
  
> [!NOTE]  
>  Не следует вызывать методы <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.IsInputReady%2A> или <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> в собственном коде. Подсистема обработки потока данных вызывает эти методы класса `PipelineComponent`, которые переопределяются при запуске подсистемой обработки потока данных компонента.  
  
### <a name="example"></a>Пример  
 Для конкретного блокируемого входа следующая реализация метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> возвращает коллекцию входов, ожидающих дополнительных данных и поэтому блокирующих указанный вход. Компонент определяет блокирующие входы путем проверки наличия других входов помимо заблокированного, которые не имеют в настоящее время в буферах доступных для обработки данных, которые уже получены компонентом (`inputBuffers[i].CurrentRow() == null`). Затем метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.GetDependentInputs%2A> возвращает коллекцию блокирующих входов в виде коллекции идентификаторов входов.  
  
```csharp  
public override Collection<int> GetDependentInputs(int blockedInputID)  
{  
    Collection<int> currentDependencies = new Collection<int>();  
    for (int i = 0; i < ComponentMetaData.InputCollection.Count; i++)  
    {  
        if (ComponentMetaData.InputCollection[i].ID != blockedInputID  
            && inputBuffers[i].CurrentRow() == null)  
        {  
            currentDependencies.Add(ComponentMetaData.InputCollection[i].ID);  
        }  
    }  
  
    return currentDependencies;  
}  
```  
  
  
