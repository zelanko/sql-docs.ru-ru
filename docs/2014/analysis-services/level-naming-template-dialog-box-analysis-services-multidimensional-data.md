---
title: Диалоговое окно «шаблон» (службы Analysis Services — многомерные данные) именования уровней | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: febaae6051e8428d3fed2bb6533ce2c4d972950f
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66078062"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Шаблон именования уровней» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Шаблон именования уровней** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для создания шаблона именования уровней родительского атрибута измерения. Дополнительные сведения о шаблонах именования уровней см. в разделе [Элемент NamingTemplate (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Можно отобразить **шаблон именования уровней** диалоговое окно, нажав кнопку с многоточием (**...** ) на `NamingTemplate` значении перевода для атрибута в **сведения о переводе** панели **переводы** вкладке **конструктор измерений**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Определение шаблона уровня**|Отображает сетку, в которой можно спроектировать иерархию уровней для родительского атрибута. Сетка содержит следующие столбцы:<br /><br /> **Уровень**. Отображает порядковое положение уровня, для которого используется имя, заданное в поле **Имя** . Чтобы добавить новый шаблон именования для уровня, выберите **Имя** в строке, содержащей звездочку (\*) в поле **Уровень**.<br /><br /> **Имя**: Содержит шаблон именования для уровня, указанного в поле **Уровень**. Чтобы добавить заполнитель для порядкового положения уровня в шаблоне именования, вставьте одну звездочку (*). Чтобы сделать звездочку частью имени, создаваемого шаблоном именования, необходимо добавить две звездочки (\*\*).|  
|**Очистить все**|Выберите удаление всех строк в **Определении шаблона уровня**.|  
|**Результат**|Отображает шаблон именования уровня, созданный при помощи этого диалогового окна.|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
