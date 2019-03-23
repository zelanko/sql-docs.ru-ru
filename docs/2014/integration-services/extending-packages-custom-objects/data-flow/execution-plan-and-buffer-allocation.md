---
title: План выполнения и выделение буферов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom data flow components [Integration Services], buffer allocations
- custom data flow components [Integration Services], execution plans
- buffer allocations [Integration Services]
- data flow components [Integration Services], buffer allocations
- data flow components [Integration Services], execution plans
- execution plans [Integration Services]
ms.assetid: 679d9ff0-641e-47c3-abb8-d1a7dcb279dd
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: a9a300ce29141ed0a065b4186b737c4d8c294820
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58387262"
---
# <a name="execution-plan-and-buffer-allocation"></a>План выполнения и выделение буферов
  Перед выполнением задача потока данных проверяет свои компоненты и формирует план выполнения для каждой последовательности компонентов. В этом разделе предоставляются сведения о плане выполнения, рассматривается, как просмотреть план и как на основании плана выполнения выделяются входной и выходной буферы.  
  
## <a name="understanding-the-execution-plan"></a>Основные сведения о плане выполнения  
 План выполнения содержит потоки источника и рабочие потоки. Каждый поток содержит списки действий, которые задают списки действий над выходными данными для потоков источника или списки действий над входными и выходными данными для рабочих потоков. Потоки источника в плане выполнения представляют компоненты источника в потоке данных и идентифицируются в плане выполнения как *SourceThread**n*, где *n* — это начинающееся с нуля число потоков источника.  
  
 Каждый поток источника создает буфер, устанавливает прослушивателя и вызывает метод <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A> на компоненте источника. Здесь начинается выполнение и отсюда берутся данные, когда компонент источника начинает добавлять строки в выходные буферы, предоставляемые ему задачей потока данных. После начала работы потоков источника работа распределяется среди рабочих потоков.  
  
 Рабочий поток содержит списки действий как над входными, так и над выходными данными и идентифицируется в плане выполнения как *WorkThread**n*, где *n* — это начинающееся с нуля число рабочих потоков. Эти потоки содержат списки действий над выходными данными, если граф содержит компонент с асинхронными выходами.  
  
 Следующий образец плана выполнения представляет поток данных, который содержит компонент источника, подключенный к преобразованию с асинхронным выходом, подключенным к компоненту назначения. В этом примере WorkThread0 содержит список действий над выходными данными, поскольку компонент преобразования имеет асинхронный выход.  
  
```  
SourceThread0   
    Influences: 72 158   
    Output Work List   
        CreatePrimeBuffer of type 1 for output id 10   
        SetBufferListener: "WorkThread0" for input ID 73   
        CallPrimeOutput on component "OLE DB Source" (1)   
    End Output Work List   
    This thread drives 0 distributors   
End SourceThread0   
WorkThread0   
    Influences: 72 158   
    Input Work list, input ID 73   
        CallProcessInput on input ID 73 on component "Sort" (72) for view type 2   
    End Input Work list for input 73   
    Output Work List   
        CreatePrimeBuffer of type 3 for output id 74   
        SetBufferListener: "WorkThread1" for input ID 171with internal handoff   
        CallPrimeOutput on component "Sort" (72)   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread0   
WorkThread1   
    Influences: 158   
    Input Work list, input ID 171  
        CallProcessInput on input ID 171 on component "OLE DB Destination" (158) for view type 4  
    End Input Work list for input 171   
    Output Work List   
    End Output Work List   
    This thread drives 0 distributors   
End WorkThread1  
```  
  
> [!NOTE]  
>  План выполнения создается при каждом выполнении пакета и может отслеживаться с помощью добавления в пакет регистратора, включения ведения журнала и выбора события **PipelineExecutionPlan**.  
  
## <a name="understanding-buffer-allocation"></a>Основные сведения о выделении буферов  
 На основании плана выполнения задача потока данных создает буферы, содержащие столбцы, определенные в выходах компонентов потока данных. Буфер повторно используется как потоки данных через последовательность компонентов, пока не встретится компонент с асинхронными выходами. После этого создается новый буфер, который содержит выходные столбцы асинхронного выхода и выходные столбцы компонентов нисходящего потока.  
  
 Во время выполнения компоненты имеют доступ к буферу в текущем источнике рабочего потока. Буфер является либо входным буфером, предоставляемым методом <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A>, либо выходным буфером, предоставляемым методом <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>. Свойство <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer.Mode%2A> буфера <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineBuffer> также идентифицирует каждый буфер как входной или выходной буфер.  
  
 Компоненты преобразования с асинхронными выходами получают существующий входной буфер от метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.ProcessInput%2A> и получают новый выходной буфер от метода <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PrimeOutput%2A>. Компонент преобразования с асинхронными выходами является единственным типом компонентов потока данных, который получает и входной, и выходной буфера.  
  
 Поскольку буфер, предоставленный компоненту, скорее всего, содержит больше столбцов, чем имеет компонент в его коллекциях входных и выходных столбцов, разработчики компонентов могут вызывать метод <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSBufferManager100.FindColumnByLineageID%2A>, чтобы определить положение столбца в буфере по его идентификатору `LineageID`.  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
  
