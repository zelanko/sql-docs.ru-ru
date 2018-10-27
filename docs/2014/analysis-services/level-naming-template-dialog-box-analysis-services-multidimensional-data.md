---
title: Диалоговое окно «шаблон» (службы Analysis Services — многомерные данные) именования уровней | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 37afa05887059607edc257c3957495a8db335d3c
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50144775"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Шаблон именования уровней» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Шаблон именования уровней** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для создания шаблона именования уровней родительского атрибута измерения. Дополнительные сведения о шаблонах именования уровней см. в разделе [Элемент NamingTemplate (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Можно отобразить **шаблон именования уровней** диалоговое окно, нажав кнопку с многоточием (**...** ) на `NamingTemplate` значении перевода для атрибута в **сведения о переводе** панели **переводы** вкладке **конструктор измерений**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Определение шаблона уровня**|Отображает сетку, в которой можно спроектировать иерархию уровней для родительского атрибута. Сетка содержит следующие столбцы:<br /><br /> **Уровень**: отображает порядковое положение уровня, для которого имя, указанное в **имя** используется. Чтобы добавить новый шаблон именования для уровня, выберите **Имя** в строке, содержащей звездочку (\*) в поле **Уровень**.<br /><br /> **Имя**: содержит шаблон именования для уровня, указанного в **уровень**. Чтобы добавить заполнитель для порядкового положения уровня в шаблоне именования, вставьте одну звездочку (*). Чтобы сделать звездочку частью имени, создаваемого шаблоном именования, необходимо добавить две звездочки (\*\*).|  
|**Очистить все**|Выберите удаление всех строк в **Определении шаблона уровня**.|  
|**Результат**|Отображает шаблон именования уровня, созданный при помощи этого диалогового окна.|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
