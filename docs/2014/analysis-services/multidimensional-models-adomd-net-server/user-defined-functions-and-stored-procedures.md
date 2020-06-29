---
title: Определяемые пользователем функции и хранимые процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- stored procedures [ADOMD.NET]
- ADOMD.NET, user defined functions
- user defined functions [ADOMD.NET]
- ADOMD.NET, UDFs
- ADOMD.NET, stored procedures
ms.assetid: 07e8aa47-37d4-4bbc-8bff-49e422d12897
author: minewiskan
ms.author: owend
ms.openlocfilehash: a49aa41d158bf2c9fd1ebb1a711d6ff35c0df98b
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469019"
---
# <a name="user-defined-functions-and-stored-procedures"></a>Определяемые пользователем функции и хранимые процедуры
  С помощью объектов ADOMD.NET Server можно создать определяемую пользователем функцию (UDF) или хранимые процедуры для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] взаимодействия с метаданными и данными с сервера. Эти внутрипроцессные методы вызываются при помощи инструкций на языке MDX или DMX для предоставления дополнительных функциональных возможностей без задержек, связанных с обменом данными по сети.  
  
## <a name="udf-examples"></a>Примеры определяемых пользователем функций  
 Определяемая пользователем функция — это метод, который можно вызывать в контексте инструкции MDX или DMX; он может принимать любое количество параметров и возвращать данные любого типа.  
  
 Определяемая пользователем функция, созданная при помощи языка MDX, похожа на функцию, созданную на языке DMX. Основное отличие состоит в том, что определенные свойства объекта [Microsoft. AnalysisServices. того объектная AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) , такие как свойства [Microsoft. AnalysisServices. того объектная AdomdServer. Context. CURRENTCUBE *](/previous-versions/sql/sql-server-2014/ms137081(v=sql.120)) и [Microsoft. AnalysisServices. того объектная AdomdServer. Context. куррентминингмодел *](/previous-versions/sql/sql-server-2014/ms137178(v=sql.120)) , доступны только для одного языка сценариев или другого.  
  
 Следующие примеры демонстрируют использование определяемой пользователем функции для возврата описания узла, фильтрации кортежей и применения фильтра к кортежу.  
  
### <a name="returning-a-node-description"></a>Возврат описания узла  
 В следующем примере создается определяемая пользователем функция, которая возвращает описание указанного узла. В этой определяемой пользователем функции используется текущий контекст, в котором она выполняется, а также предложение FROM языка DMX для извлечения узла из текущей модели интеллектуального анализа данных.  
  
```  
public string GetNodeDescription(string nodeUniqueName)  
{  
   return Context.CurrentMiningModel.GetNodeFromUniqueName(nodeUniqueName).Description;  
}  
```  
  
 После развертывания описанный выше пример определяемой пользователем функции можно вызвать следующей инструкцией DMX, которая извлекает наиболее вероятный узел прогнозирования. В описании приводятся сведения, характеризующие условия, из которых состоит узел прогнозирования.  
  
```  
select Cluster(), SampleAssembly.GetNodeDescription( PredictNodeId(Cluster()) ) FROM [Customer Clusters]  
```  
  
### <a name="returning-tuples"></a>Возврат кортежей  
 В следующем примере показано, как получить набор и количество возвращаемых значений, а также случайным образом извлечь кортежи из набора, возвращая конечное подмножество.  
  
```  
public Set RandomSample(Set set, int returnCount)  
{  
   //Return the original set if there are fewer tuples  
   //in the set than the number requested.  
   if (set.Tuples.Count <= returnCount)  
      return set;  
  
   System.Random r = new System.Random();  
   SetBuilder returnSet = new SetBuilder();  
  
   //Retrieve random tuples until the return set is filled.  
   int i = set.Tuples.Count;  
   foreach (Tuple t in set.Tuples)  
   {  
      if (r.Next(i) < returnCount)  
      {  
         returnCount--;  
         returnSet.Add(t);  
      }  
      i--;  
      //Stop the loop if we have enough tuples.  
      if (returnCount == 0)  
         break;  
   }  
   return returnSet.ToSet();  
}  
```  
  
 Описанная выше функция вызывается в следующем примере многомерного выражения (MDX). В этом примере многомерных выражений из базы данных **Adventure Works** извлекаются пять случайных состояний или провинции.  
  
```  
SELECT SampleAssembly.RandomSample([Geography].[State-Province].Members, 5) on ROWS,   
[Date].[Calendar].[Calendar Year] on COLUMNS  
FROM [Adventure Works]  
WHERE [Measures].[Reseller Freight Cost]  
```  
  
### <a name="applying-a-filter-to-a-tuple"></a>Применение фильтра к кортежу  
 В следующем примере создается определяемая пользователем функция, которая принимает набор и при помощи объекта Expression применяет фильтр к каждому кортежу в наборе. В возвращаемый набор будут добавлены все кортежи, соответствующие фильтру.  
  
 [!code-csharp[Adomd.NetServer#FilterSet](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#filterset)]  
  
 Описанная выше функция вызывается в следующем примере многомерного выражения, где набор фильтруется по городам, название которых начинается с «А».  
  
```  
Select Measures.Members on Rows,  
SampleAssembly.FilterSet([Customer].[Customer Geography].[City], "[Customer].[Customer Geography].[City].CurrentMember.Name < 'B'") on Columns  
From [Adventure Works]  
```  
  
## <a name="stored-procedure-example"></a>Пример хранимой процедуры  
 В следующем примере показано, как в хранимой процедуре, основанной на многомерном выражении, по мере необходимости используется объект AMO для создания секций для узла «Продажи через Интернет».  
  
 [!code-csharp[Adomd.NetServer#CreateInternetSalesMeasureGroupPartitions](../../snippets/csharp/SQL14/adomd.net/adomd.netserver/cs/class1.cs#createinternetsalesmeasuregrouppartitions)]  
  
  
