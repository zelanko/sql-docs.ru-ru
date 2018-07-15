---
title: Привязка объекта | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql.asvs.dimensiondesigner.dbv.objectbinding.f1
helpviewer_keywords:
- Object Binding dialog box
ms.assetid: 2bb5ad7c-2962-4559-8c95-cf7148bd2e72
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 52a860a5228494eef64955c6f3ee4d0c577d9a87
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299134"
---
# <a name="object-binding-dialog-box"></a>Диалоговое окно «Привязка объектов»
  Используйте диалоговое окно **Привязка объекта** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для определения привязок между свойством объекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и таблицей или столбцом в представлении источника данных. Диалоговое окно **Привязка объектов** можно открыть, выбрав пункт **(создать)** из раскрывающегося списка для значения следующих свойств объекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] в окне **Свойства** среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]:  
  
-   NameColumn  
  
-   ValueColumn  
  
-   CustomRollupColumn  
  
-   CustomRollupPropertiesColumn  
  
-   UnaryOperatorColumn  
  
## <a name="options"></a>Параметры  
 **Тип привязки**  
 Выбирает привязку для использования с объектом служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Можно использовать следующие типы привязки:  
  
 Привязка к столбцу  
 Привязывает объект к существующей таблице и столбцу в представлении источника данных.  
  
 Сформировать столбец  
 Указывает, что в представлении источника данных следует определить новый столбец и ассоциировать с ним привязку к столбцу.  
  
> [!NOTE]  
>  Если выбран этот параметр, необходимо запустить **мастер формирования схем** до развертывания объекта служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 Привязка строк  
 Привязывает объект к строке в таблице фактов и используется для облегчения подсчета мер на основе количества строк, обработанных в таблице фактов.  
  
 **Исходная таблица**  
 Выводит список таблиц в представлении источника данных, ассоциированном с объектом служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
 **Исходный столбец**  
 Выводит список столбцов в таблице, выбранной в параметре **Исходная таблица**.  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  
