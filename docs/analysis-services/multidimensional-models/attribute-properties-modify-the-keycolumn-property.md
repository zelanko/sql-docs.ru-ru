---
title: "Изменение свойства KeyColumn атрибута | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d661563b794e205b554d3f11bcd2eb495d7d3a08
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="attribute-properties---modify-the-keycolumn-property"></a>Атрибут свойства — изменение свойства KeyColumn
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Вы можете изменить **KeyColumns** свойства атрибута. Например, в качестве ключа атрибута может потребоваться не одиночный ключ, а составной.  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a>Изменение свойства KeyColumns атрибута  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]откройте проект, в котором необходимо изменить свойство **KeyColumns** .  
  
2.  Откройте конструктор измерений одним из следующих способов:  
  
    -   В **обозревателе решений**правой кнопкой мыши щелкните папку **Измерения** , а затем выберите либо **Открыть** , либо **Конструктор представлений**.  
  
         —или—  
  
    -   В конструкторе кубов на **Структура куба** , разверните измерение куба в **измерения** панели и нажмите **изменить \<измерения >**.  
  
3.  На вкладке **Структура измерения** , на панели **Атрибуты** , щелкните атрибут, для которого нужно изменить свойство **KeyColumns** .  
  
4.  В окне **Свойства** щелкните значение для свойства **KeyColumns** .  
  
5.  Нажмите кнопку обзора **(...)** , отображающуюся в ячейке значения поля свойства.  
  
     Откроется диалоговое окно **Ключевые столбцы** .  
  
6.  Для удаления существующего ключевого столбца выберите его в списке **Ключевые столбцы** и нажмите кнопку **\<** .  
  
7.  Для добавления ключевого столбца выберите его в списке **Доступные столбцы** и нажмите кнопку **>** .  
  
    > [!NOTE]  
    >  Если задано несколько ключевых столбцов, они отображаются в том же порядке, что и в списке **Ключевые столбцы** . Например, у атрибута «месяц» два ключевых столбца: месяц и год. Если столбец «год» появится в списке раньше столбца «месяц», службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] будут выполнять сортировку по годам, а затем по месяцам. Если столбец «месяц» будет в списке раньше столбца «год», службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] будут выполнять сортировку по месяцам, а затем по годам.  
  
8.  Чтобы изменить порядок ключевых столбцов, выберите столбец и нажмите кнопку **Вверх** или кнопку **Вниз** .  
  
## <a name="see-also"></a>См. также  
 [Справочник по свойствам атрибута измерения](../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md)  
  
  
