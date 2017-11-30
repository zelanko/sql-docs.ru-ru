---
title: "Задание ориентации текстового поля (построитель отчетов и службы SSRS) | Документы Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64bd53f4-2f31-4732-8c2e-64c7b54b6972
caps.latest.revision: "9"
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.workload: On Demand
ms.openlocfilehash: 7be98cbb004342ae11cc316fa33e778ad0c82347
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="set-text-box-orientation-report-builder-and-ssrs"></a>Задание ориентации текстового поля (построитель отчетов и службы SSRS)
В отчете [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] с разбиением на страницы текстовое поле можно поворачивать в разных направлениях:   
* по горизонтали;   
* по вертикали (поворот на 90 градусов, текст читается сверху вниз);  
* поворот на 270 градусов (текст читается снизу вверх).   
  
Поскольку поворот задается для текстового поля, а не для текста, вращение применяется ко всему тексту в поле. Для различных областей текста нельзя указать различный поворот вращения. Чтобы разместить разворачиваемый текст, задайте значения ширины столбца и высоты строки вручную.  
  
 Свойство WritingMode, используемое для указания ориентации текста, недоступно в диалоговом окне **Свойства текстового поля** . Оно находится и задается на панели свойств.   
  
## <a name="to-rotate-text"></a>Вращение текста  
  
1.  Создайте отчет или откройте существующий отчет и [добавьте текстовое поле](../../reporting-services/report-design/add-move-or-delete-a-text-box-report-builder-and-ssrs.md) в область конструктора.  
  
3.  Выберите текстовое поле, которое следует повернуть.  
  
2.  Если панель свойств не открыта, перейдите на вкладку **Вид** и установите флажок **Свойства** .  
  
4.  Найдите свойство WritingMode в панели свойства и в раскрывающемся списке выберите ориентацию текста для применения к текстовому полю.  
  
    > [!NOTE]  
    >  Если свойства на панели свойств упорядочены по категориям, свойство WritingMode относится к категории **Локализация** .  
  
5.  В списке выберите **Горизонтально**, **Вертикально**или **Поворот на 270 градусов**.  
  
## <a name="see-also"></a>См. также  
 [Текстовые поля (построитель отчетов и службы SSRS)](../../reporting-services/report-design/text-boxes-report-builder-and-ssrs.md)   
 [Учебник. Форматирование текста (построитель отчетов)](../../reporting-services/tutorial-format-text-report-builder.md)  
  
  
