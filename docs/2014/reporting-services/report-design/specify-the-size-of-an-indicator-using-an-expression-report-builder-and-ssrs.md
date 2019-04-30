---
title: Указание размера индикатора с помощью выражения (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: ab0b86f1-4882-4258-a2b6-c612faecfa4b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a77a96d57a1ea9489697a415e96fb52165b8270f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63215715"
---
# <a name="specify-the-size-of-an-indicator-using-an-expression-report-builder-and-ssrs"></a>Указание размера индикатора с помощью выражения (построитель отчетов и службы SSRS)
  Помимо цвета, направления и формы, для изменения визуального представления индикатора можно использовать его размер.  
  
 У индикатора есть коллекция состояний индикатора IndicatorStates. Коллекция IndicatorStates обычно имеет несколько состояний. Каждое состояние является частью коллекции и представляется значком. Вместе состояния представляют собой коллекцию IndicatorStates.  
  
 Для динамической настройки размера значков надо задать свойства элементов коллекции IndicatorStates на панели "Свойства" в построителе отчетов. Если панель **Свойства** не отображается, перейдите на вкладку **Вид** и выберите пункт **Свойства**.  
  
> [!NOTE]  
>  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]окно **Свойства** используется для установки свойств элемента. Если окно **Свойства** не открыто, нажмите клавишу F4.  
  
 Панель **Свойства** предоставляет доступ к свойствам коллекции IndicatorStates индикатора. Разные размеры значков задаются установкой свойства ScaleFactor коллекции IndicatorStates с помощью выражения. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](expressions-report-builder-and-ssrs.md).  
  
 Выражение, используемое для этой процедуры, также применяется для создания отчетов с разными размерами индикаторов, как показано в разделе [Индикаторы (построитель отчетов и службы SSRS)](indicators-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-the-indicator-icon-size-using-an-expression"></a>Указание размера значка индикатора с помощью выражения  
  
1.  Щелкните индикатор, который нужно изменить.  
  
2.  На панели "Свойства" найдите свойство IndicatorStates.  
  
     Если панель "Свойства" организована по категориям, свойство IndicatorStates будет находиться в категории **Состояния** .  
  
3.  Нажмите кнопку с многоточием **(...)** рядом со свойством IndicatorStates. Откроется диалоговое окно **Редактор коллекции состояний индикатора** .  
  
     Выберите все элементы коллекции.  
  
4.  В списке **Выбор нескольких свойств** щелкните стрелку вниз рядом со свойством ScaleFactor и выберите **Выражение**.  
  
5.  В диалоговом окне **Выражение** введите выражение.  
  
     В следующем образце выражения размер значка изменяется в зависимости от значения поля **Продажи за год на дату** .  
  
     `=IIF(Fields!SalesYTD.value = 0,0,Fields!SalesYTD.value/Max(Fields!SalesYTD.value,"Indicator"))`  
  
     Дополнительные сведения см. в разделе [Примеры выражений (построитель отчетов и службы SSRS)](expression-examples-report-builder-and-ssrs.md).  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Индикаторы (построитель отчетов и службы SSRS)](indicators-report-builder-and-ssrs.md)  
  
  
