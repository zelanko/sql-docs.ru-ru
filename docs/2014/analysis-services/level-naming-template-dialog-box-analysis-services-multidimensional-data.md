---
title: Диалоговое окно «Шаблон именования уровней» (Analysis Services-многомерные данные) | Документация Майкрософт
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
ms.openlocfilehash: 4dd704e619e49f0dd1adb8fed8f1e743b61309af
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84542006"
---
# <a name="level-naming-template-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Шаблон именования уровней» (службы Analysis Services — многомерные данные)
  Используйте диалоговое окно **Шаблон именования уровней** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для создания шаблона именования уровней родительского атрибута измерения. Дополнительные сведения о шаблонах именования уровней см. в разделе [Элемент NamingTemplate (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/namingtemplate-element-assl). Диалоговое окно **шаблон именования уровней** можно отобразить, нажав кнопку с многоточием (**...**) в `NamingTemplate` значении перевода для атрибута на панели **сведения о переводе** на вкладке **переводы** **конструктора измерений**.  
  
## <a name="options"></a>Варианты  
  
|Термин|Определение|  
|----------|----------------|  
|**Определить шаблон данного уровня**|Отображает сетку, в которой можно спроектировать иерархию уровней для родительского атрибута. Сетка содержит следующие столбцы:<br /><br /> **Уровень**: отображает порядковый номер уровня, для которого используется имя, указанное в поле **имя** . Чтобы добавить новый шаблон именования для уровня, выберите **Имя** в строке, содержащей звездочку (\*) в поле **Уровень**.<br /><br /> **Имя**: содержит шаблон именования, используемый для уровня, указанного в поле **уровень**. Чтобы добавить заполнитель для порядкового положения уровня в шаблоне именования, вставьте одну звездочку (*). Чтобы добавить звездочку как часть имени, созданного с помощью шаблона именования, добавьте две звездочки ( \* \* ).|  
|**Очистить все**|Выберите удаление всех строк в **Определении шаблона уровня**.|  
|**Результат**|Отображает шаблон именования уровня, созданный при помощи этого диалогового окна.|  
  
## <a name="see-also"></a>См. также:  
 [Analysis Services конструкторов и диалоговых окон &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Переводы &#40;конструктор измерений&#41; &#40;Analysis Services многомерных данных&#41;](translations-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
