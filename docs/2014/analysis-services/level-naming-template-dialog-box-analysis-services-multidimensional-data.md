---
title: Диалоговое окно «шаблон» (службы Analysis Services — многомерные данные) именования уровней | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.levelnamingtemplatedialog.f1
helpviewer_keywords:
- Level Naming Template dialog box
ms.assetid: 96cad715-213e-4eac-9003-130a2f5fc985
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3f7c3bf3d7c1b09d8655443d4de711f851667947
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095582"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Шаблон именования уровней» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Шаблон именования уровней** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для создания шаблона именования уровней родительского атрибута измерения. Дополнительные сведения о шаблонах именования уровней см. в разделе [Элемент NamingTemplate (ASSL)](scripting/properties/namingtemplate-element-assl.md). Можно отобразить **шаблон именования уровней** диалоговое окно, нажав кнопку с многоточием (**...** ) на `NamingTemplate` значение для перевода для атрибута в **Подробности перевода** на панели **переводы** вкладке **конструктор измерений**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Определить шаблон данного уровня**|Отображает сетку, в которой можно спроектировать иерархию уровней для родительского атрибута. Сетка содержит следующие столбцы:<br /><br /> **Уровень**: отображает порядковое положение уровня, для которого имя, указанное в **имя** используется. Чтобы добавить новый шаблон именования для уровня, выберите **Имя** в строке, содержащей звездочку (\*) в поле **Уровень**.<br /><br /> **Имя**: содержит шаблон именования для уровня, указанного в **уровень**. Чтобы добавить заполнитель для порядкового положения уровня в шаблоне именования, вставьте одну звездочку (*). Чтобы сделать звездочку частью имени, создаваемого шаблоном именования, необходимо добавить две звездочки (\*\*).|  
|**Очистить все**|Выберите удаление всех строк в **Определении шаблона уровня**.|  
|**Результат**|Отображает шаблон именования уровня, созданный при помощи этого диалогового окна.|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Переводы &#40;конструктор измерений&#41; &#40;службы Analysis Services — многомерные данные&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  