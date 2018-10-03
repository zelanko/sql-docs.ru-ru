---
title: Архитектура серверных объектов ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: abbc415f86eed4433fc6dc41b474515e2b801ce6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48177500"
---
# <a name="adomdnet-server-object-architecture"></a>Архитектура серверных объектов ADOMD.NET
  Серверные объекты ADOMD.NET являются вспомогательными, которые могут использоваться для создания определяемых пользователем функций (UDF) или хранимых процедур в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Для использования пространства имен `Microsoft.AnalysisServices.AdomdServer` (и этих объектов) необходимо добавить в проект определяемой пользователем функции или хранимой процедуры ссылку на библиотеку msmgdsrv.dll.  
  
 ![Показывает отношения между объектами на сервере ADOMD.NET](../../../2014/analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "показаны отношения между объектами на сервере ADOMD.NET")  
Модель объектов ADOMD.NET  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Чтобы|Используемый объект|  
|--------|---------------------|  
|Вычисление многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Expression> позволяет выполнить многомерное выражение и вычислить его по указанному кортежу.|  
|Обеспечение поддержки выполнения функций MDX без создания полной инструкции многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> С помощью объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX> удобно вызывать стандартные функции MDX без использования объекта <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. В будущих версиях планируется появление дополнительных функций для объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX>.|  
|Представление текущего контекста выполнения для определяемой пользователем функции|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> выдает такие сведения, как текущий куб или модель интеллектуального анализа данных, а также различные коллекции метаданных. Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> используется главным образом в качестве свойства <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> объекта <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Благодаря этому основному варианту использования автор определяемой пользователем функции или хранимой процедуры может принимать решения, исходя из того, какой элемент из определенного измерения запроса включен.|  
|Создание наборов и кортежей|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> позволяет создавать неизменяемые наборы, а объект <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> — неизменяемые кортежи.|  
|Поддержка неявного преобразования и приведения для шести основных типов языка многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> обеспечивает неявное преобразование и приведение для следующих типов:<br /><br /> -   <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Level><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Member><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br />-   <xref:Microsoft.AnalysisServices.AdomdServer.Set><br />-Скалярные, или типы значений|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](../multidimensional-models-adomd-net-server/adomd-net-server-programming.md)  
  
  
