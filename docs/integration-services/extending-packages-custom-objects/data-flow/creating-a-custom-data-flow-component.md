---
title: "Создание пользовательского компонента потока данных | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-custom-objects
ms.reviewer: 
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- design-time component interface [Integration Services]
- custom data flow components [Integration Services], about data flow components
- custom data flow components [Integration Services]
- data flow components [Integration Services]
- data flow components [Integration Services], developing
ms.assetid: 9d96bcf5-eba8-44bd-b113-ed51ad0d0521
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 565a2b8e48537cea20a8e509cf5b6d7b59cc12f0
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-custom-data-flow-component"></a>Создание пользовательского компонента потока данных
  В [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], задача потока данных предоставляет модель объектов, которая позволяет разработчикам создавать пользовательские компоненты потока данных — источники, преобразования и назначения — с помощью [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] и управляемого кода.  
  
 Задача потока данных состоит из компонентов, содержащих интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> и коллекцию объектов <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSPath100>, которыми определяется движение данных между компонентами.  
  
> [!NOTE]  
>  При создании настраиваемого поставщика в файл ProviderDescriptors.xml необходимо внести значения столбца метаданных.  
  
## <a name="design-time-and-run-time"></a>Время разработки и время выполнения  
 Перед выполнением задача потока данных считается находящейся в состоянии времени разработки, поскольку она подвергается добавочным изменениям. К таким изменениям относятся добавление или удаление компонентов, добавление или удаление объектов пути, которые соединяют компоненты, и изменения в метаданных компонентов. При изменении метаданных компонент может отслеживать их и выполнять ответные действия. Например, компонент может не допускать внесения определенных изменений или вносить дополнительные изменения в ответ на изменение. Во время разработки конструктор взаимодействует с компонентом через интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> времени разработки.  
  
 Во время выполнения задача потока данных исследует последовательность компонентов, подготавливает план выполнения и управляет пулом рабочих потоков, выполняющих план работы. Хотя каждый рабочий поток выполняет некоторую работу, являющуюся внутренней для задачи потока данных, основной задачей рабочего потока является вызов методов компонента через интерфейс <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> времени выполнения.  
  
## <a name="creating-a-component"></a>Создание компонента  
 Чтобы создать компонент потока данных, необходимо создать производный класс от базового класса <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent>, применить класс <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>, а затем переопределить соответствующие методы базового класса. Класс <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> реализует интерфейсы <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSDesigntimeComponent100> и <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSRuntimeComponent100> и предоставляет доступ к их методам для переопределения в пользовательском компоненте.  
  
 В зависимости от объектов, используемых компонентом, для проекта могут потребоваться ссылки на некоторые (или все) из следующих сборок.  
  
|Компонент|Сборка для ссылки|Пространство имен для импорта|  
|-------------|---------------------------|-------------------------|  
|Поток данных|Microsoft.SqlServer.PipelineHost|<xref:Microsoft.SqlServer.Dts.Pipeline>|  
|Оболочка потока данных|Microsoft.SqlServer.DTSPipelineWrap|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper>|  
|Параметры выполнения|Microsoft.SQLServer.ManagedDTS|<xref:Microsoft.SqlServer.Dts.Runtime>|  
|Оболочка среды выполнения|Microsoft.SqlServer.DTSRuntimeWrap|<xref:Microsoft.SqlServer.Dts.Runtime.Wrapper>|  
  
 В следующем примере кода показан простой компонент, который является производным от базового класса и применяет класс <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>. Необходимо добавить ссылку на сборку Microsoft.SqlServer.DTSPipelineWrap.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsPipelineComponent(DisplayName = "SampleComponent", ComponentType = ComponentType.Transform )]  
    public class BasicComponent: PipelineComponent  
    {  
        // TODO: Override the base class methods.  
    }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(DisplayName:="SampleComponent", ComponentType:=ComponentType.Transform)> _  
Public Class BasicComponent  
  
    Inherits PipelineComponent  
  
    ' TODO: Override the base class methods.  
  
End Class  
```  
  
## <a name="see-also"></a>См. также:  
 [Разработка пользовательского интерфейса для компонента потока данных](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-user-interface-for-a-data-flow-component.md)  
  
  

