---
title: Серверная архитектура объектов ADOMD.NET | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- ADOMD.NET, object model
- object model [ADOMD.NET]
ms.assetid: bdc81de9-b390-4654-b62a-cd6c0c9ca10d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 33a8f420f985c9e62c7d7f275e7de370a6988e8d
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85469059"
---
# <a name="adomdnet-server-object-architecture"></a>Архитектура серверных объектов ADOMD.NET
  Объекты сервера ADOMD.NET являются вспомогательными объектами, которые можно использовать для создания определяемых пользователем функций (UDF) или хранимых процедур в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
> [!NOTE]  
>  Для использования пространства имен `Microsoft.AnalysisServices.AdomdServer` (и этих объектов) необходимо добавить в проект определяемой пользователем функции или хранимой процедуры ссылку на библиотеку msmgdsrv.dll.  
  
 ![Показывает связи между объектами на сервере ADOMD.NET](../../analysis-services/dev-guide/media/adomdnetserverobjectmodel.gif "Показывает связи между объектами на сервере ADOMD.NET")  
Модель объектов ADOMD.NET  
  
 Взаимодействие с иерархией объектов ADOMD.NET обычно начинается с одного или нескольких объектов верхнего уровня, как описано в следующей таблице.  
  
|Кому|Используемый объект|  
|--------|---------------------|  
|Вычисление многомерных выражений|[Microsoft. AnalysisServices. того объектная AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120))<br /> Объект [Microsoft. AnalysisServices. того объектная AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) предоставляет способ выполнения многомерного выражения и вычисления этого выражения в указанном кортеже.|  
|Обеспечение поддержки выполнения функций MDX без создания полной инструкции многомерных выражений|[Microsoft. AnalysisServices. того объектная AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120))<br /> Объект [Microsoft. AnalysisServices. того объектная AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) удобен для вызова предопределенных функций многомерных выражений без использования объекта [Microsoft. AnalysisServices. того объектная AdomdServer. Expression](/previous-versions/sql/sql-server-2014/ms143609(v=sql.120)) . Дополнительные функции для объекта [Microsoft. AnalysisServices. того объектная AdomdServer. MDX](/previous-versions/sql/sql-server-2014/ms143616(v=sql.120)) должны быть доступны в будущих выпусках.|  
|Представление текущего контекста выполнения для определяемой пользователем функции|[Microsoft. AnalysisServices. того объектная AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))<br /> Объект [Microsoft. AnalysisServices. того объектная AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) предоставляет такие сведения, как текущий куб или модель интеллектуального анализа данных и различные коллекции метаданных. Одним из ключевых использования объекта [Microsoft. AnalysisServices. того объектная AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) является свойство [Microsoft. AnalysisServices. того объектная AdomdServer. Hierarchy. CurrentMember *](/previous-versions/sql/sql-server-2014/ms137044(v=sql.120)) объекта [Microsoft. AnalysisServices. того объектная AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120)) . Благодаря этому основному варианту использования автор определяемой пользователем функции или хранимой процедуры может принимать решения, исходя из того, какой элемент из определенного измерения запроса включен.|  
|Создание наборов и кортежей|[Microsoft. AnalysisServices. того объектная AdomdServer. сетбуилдер](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)), [Microsoft. AnalysisServices. того объектная AdomdServer. туплебуилдер](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120))<br /> [Microsoft. AnalysisServices. того объектная AdomdServer. сетбуилдер](/previous-versions/sql/sql-server-2014/ms144510(v=sql.120)) предоставляет способ создания неизменяемых наборов, в то время как [Microsoft. AnalysisServices. того объектная AdomdServer. туплебуилдер](/previous-versions/sql/sql-server-2014/ms145407(v=sql.120)) предоставляет способ создания неизменяемых кортежей.|  
|Поддержка неявного преобразования и приведения для шести основных типов языка многомерных выражений|[Microsoft. AnalysisServices. того объектная AdomdServer. Мдксвалуе](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120))<br /> Объект [Microsoft. AnalysisServices. того объектная AdomdServer. мдксвалуе](/previous-versions/sql/sql-server-2014/ms143573(v=sql.120)) предоставляет неявное преобразование и приведение типов из следующих:<br /><br /> -   [Microsoft. AnalysisServices. того объектная AdomdServer. Hierarchy](/previous-versions/sql/sql-server-2014/ms143578(v=sql.120))<br />-   [Microsoft. AnalysisServices. того объектная AdomdServer. Level](/previous-versions/sql/sql-server-2014/ms143581(v=sql.120))<br />-   [Microsoft. AnalysisServices. того объектная AdomdServer. Member](/previous-versions/sql/sql-server-2014/ms143820(v=sql.120))<br />-   [Microsoft. AnalysisServices. того объектная AdomdServer. Tuple](/previous-versions/sql/sql-server-2014/ms145330(v=sql.120))<br />-   [Microsoft. AnalysisServices. того объектная AdomdServer. Set](/previous-versions/sql/sql-server-2014/ms144530(v=sql.120))<br />-Scalar или типы значений|  
  
## <a name="see-also"></a>См. также  
 [Программирование сервера ADOMD.NET](https://docs.microsoft.com/bi-reference/adomd/multidimensional-models-adomd-net-server/adomd-net-server-programming)  
  
  
