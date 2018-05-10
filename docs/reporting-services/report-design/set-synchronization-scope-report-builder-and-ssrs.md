---
title: Задание области действия синхронизации (построитель отчетов и службы SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6f4a11e6-6151-47be-a43f-e3dbf6c0e737
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00b6638849391c64686afd9f9c070bffeb39e539
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-synchronization-scope-report-builder-and-ssrs"></a>Задание области действия синхронизации (построитель отчетов и службы SSRS)
  В отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы индикаторы показывают значения данных с проведением синхронизации по всему диапазону значений индикаторов в пределах указанной области действия.   
    
  По умолчанию областью действия родительского контейнера индикатора является объект, который содержит индикатор, такой как таблица или матрица. Синхронизацию индикатора можно менять в зависимости от разметки отчета. Например, если в такой области данных, как таблица, есть группа строк, можно выбрать эту группу в качестве области индикатора. Индикатор позволяет также пропускать синхронизацию.  
  
 Такие параметры, как единицы измерения, можно задать с помощью выражений. Дополнительные сведения см. в разделе [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md).  
  
 Общие сведения о работе и определении областей действия в отчетах см. в разделе [Область выражения для суммирования, агрегатов и встроенных коллекций &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="to-change-the-synchronization-scope-of-an-indicator"></a>Изменение области действия синхронизации индикатора  
  
1.  Щелкните правой кнопкой мыши индикатор, который необходимо изменить, и выберите **Свойства индикатора**.  
  
2.  Нажмите кнопку **Значения и состояния** на левой панели.  
  
3.  В списке **Область действия синхронизации** щелкните область действия, которую необходимо применить.  
  
     Всегда доступен параметр **(Нет)** , который удаляет область действия синхронизации из индикатора. Наличие других параметров зависит от макета конкретного отчета.  
  
     Нажмите кнопку **Выражение** (*fx*), чтобы изменить выражение, задающее область действия (необязательно).  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Индикаторы (построитель отчетов и службы SSRS)](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  
