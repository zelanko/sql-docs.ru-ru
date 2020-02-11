---
title: Организатор скриптов (вкладка «вычисления», конструктор кубов) (Analysis Services многомерных данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.calculationsview.scriptorganizerpane.f1
ms.assetid: 92624ca4-de67-4ebd-aab2-8adb527d327e
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c8c8484089bf3aa1f9c88b3b2163a49b445bf8d6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66069921"
---
# <a name="script-organizer-calculations-tab-cube-designer-analysis-services---multidimensional-data"></a>Организатор скриптов (вкладка «Вычисления», конструктор кубов) (службы Analysis Services — многомерные данные)
  Используйте панель **Организатор скриптов** на вкладке **Вычисления** конструктора кубов, чтобы получить доступ к вычисляемым элементам, именованным наборам и командам скриптов, содержащимся в скрипте куба для определенного куба, а также реорганизовать их.  
  
> [!NOTE]  
>  Эта панель не отображается в представлении формы.  
  
## <a name="options"></a>Параметры  
 **Шаг**  
 Отображает порядок выполнения вычисляемых элементов, именованных наборов и команд скриптов в скрипте куба.  
  
 Щелкните **Вверх** или **Вниз** на панели **Панель инструментов** или в контекстном меню, чтобы изменить порядок исполнения вычислений.  
  
 **Тип**  
 Отображает значок, который определяет вычисления как вычисляемый элемент, именованный набор или команду скрипта.  
  
 **Command**  
 Отображает имя команды (для вычисляемых элементов и именованных наборов) или первую строку вычисления (для команд скрипта.)  
  
 Выберите команду, чтобы отобразить **Редактор скрипта**, **Редактор формы вычисляемого элемента**или **Редактор формы именованного набора** в соответствии с данной командой (в представлении формы) или прокручивать содержимое панели **Редактор скрипта** до расположения команды в скрипте куба (в режиме просмотра скрипта).  
  
## <a name="context-menu"></a>Контекстное меню  
 Следующие пункты доступны в контекстном меню, которое выводится при щелчке правой кнопкой мыши команды панели **Организатор скриптов** .  
  
|Параметр|Определение|  
|------------|----------------|  
|**Создать вычисляемый элемент**|Выберите для отображения панели **Редактор формы вычисляемого элемента** и создания нового вычисляемого элемента. Дополнительные сведения о **Редактор формы вычисляемого элемента**см. в разделе [Редактор формы вычисляемого элемента &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md).|  
|**Создать именованный набор**|Выберите для отображения панели **Редактор формы именованного набора** и создания нового именованного набора. Дополнительные сведения о **Редактор формы именованного набора**см. в разделе [Редактор формы именованного набора &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md).|  
|**Создать команду скрипта**|Выберите, чтобы отобразить **Редактор скриптов** и создать новую команду скрипта. Дополнительные сведения о **Редактор скрипта**см. в разделе [Редактор скрипта &#40;Calculations Tab, Cube Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md).|  
|**Вверх**|Выберите, чтобы переместить выбранное вычисление на одну позицию вверх.<br /><br /> Примечание. Этот параметр недоступен, если выделенное вычисление нельзя переместить дальше.|  
|**Вниз**|Выберите, чтобы переместить выбранное вычисление на одну позицию вниз.<br /><br /> Примечание. Этот параметр недоступен, если выделенное вычисление нельзя переместить дальше.|  
|**Удаление**|Выберите для удаления выбранного вычисления.|  
  
## <a name="see-also"></a>См. также:  
 [Конструктор кубов &#40;Analysis Services многомерных данных&#41;](cube-designer-analysis-services-multidimensional-data.md)   
 [Панель инструментов &#40;вкладка «вычисления», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](toolbar-calculations-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Средства вычисления &#40;вкладка «вычисления», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](calculation-tools-cube-designer-analysis-services-multidimensional-data.md)   
 [Редактор форм вычисляемых элементов вкладка «вычисления» &#40;, конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](calculated-member-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Редактор формы именованных наборов &#40;вкладка «вычисления», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](named-set-form-editor-cube-designer-analysis-services-multidimensional-data.md)   
 [Редактор скриптов &#40;вкладка «вычисления», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](script-editor-calculations-cube-designer-analysis-services-multidimensional-data.md)   
 [Вычисления &#40;конструкторе кубов&#41; &#40;Analysis Services многомерных данных&#41;](calculations-cube-designer-analysis-services-multidimensional-data.md)  
  
  
