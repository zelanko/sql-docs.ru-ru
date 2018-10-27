---
title: Архитектура серверных объектов ADOMD.NET | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 9a527f9fd3a1d41b0b41190952705a4066b402ac
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144969"
---
# <a name="adomdnet-server-object-architecture"></a>Архитектура серверных объектов ADOMD.NET
  Серверные объекты ADOMD.NET являются вспомогательными, которые могут использоваться для создания определяемых пользователем функций (UDF) или хранимых процедур в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы использовать **Microsoft.AnalysisServices.AdomdServer** пространства имен (и эти объекты), необходимо добавить ссылку на библиотеку msmgdsrv.dll проект определяемой пользователем функции или хранимой процедуры.  
  
 ![Показывает отношения между объектами на сервере ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-server/media/adomdnetserverobjectmodel.gif "показаны отношения между объектами на сервере ADOMD.NET")  
Модель объектов ADOMD.NET  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Чтобы|Используемый объект|  
|--------|---------------------|  
|Вычисление многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.Expression><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Expression> позволяет выполнить многомерное выражение и вычислить его по указанному кортежу.|  
|Обеспечение поддержки выполнения функций MDX без создания полной инструкции многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDX><br /> С помощью объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX> удобно вызывать стандартные функции MDX без использования объекта <xref:Microsoft.AnalysisServices.AdomdServer.Expression>. В будущих версиях планируется появление дополнительных функций для объекта <xref:Microsoft.AnalysisServices.AdomdServer.MDX>.|  
|Представление текущего контекста выполнения для определяемой пользователем функции|<xref:Microsoft.AnalysisServices.AdomdServer.Context><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> выдает такие сведения, как текущий куб или модель интеллектуального анализа данных, а также различные коллекции метаданных. Объект <xref:Microsoft.AnalysisServices.AdomdServer.Context> используется главным образом в качестве свойства <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy.CurrentMember%2A> объекта <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy>. Благодаря этому основному варианту использования автор определяемой пользователем функции или хранимой процедуры может принимать решения, исходя из того, какой элемент из определенного измерения запроса включен.|  
|Создание наборов и кортежей|<xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder>, <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.SetBuilder> позволяет создавать неизменяемые наборы, а объект <xref:Microsoft.AnalysisServices.AdomdServer.TupleBuilder> — неизменяемые кортежи.|  
|Поддержка неявного преобразования и приведения для шести основных типов языка многомерных выражений|<xref:Microsoft.AnalysisServices.AdomdServer.MDXValue><br /> Объект <xref:Microsoft.AnalysisServices.AdomdServer.MDXValue> обеспечивает неявное преобразование и приведение для следующих типов:<br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Hierarchy><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Level><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Member><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Tuple><br /><br /> <xref:Microsoft.AnalysisServices.AdomdServer.Set><br /><br /> Скалярные типы или типы значений|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
