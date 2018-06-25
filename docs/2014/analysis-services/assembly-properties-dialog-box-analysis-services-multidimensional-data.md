---
title: Диалоговое окно «Свойства сборки» (службы Analysis Services — многомерные данные) | Документы Microsoft
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
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fa00c8753e30926113d90881401a8b38e573e6b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109613"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Свойства сборки» (службы Analysis Services — многомерные данные)
  Диалоговое окно **Свойства сборки** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] используется для задания свойств ссылки на сборку в базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Чтобы отобразить диалоговое окно **Свойства сборки** , можно щелкнуть правой кнопкой мыши сборку в **обозревателе объектов** и выбрать пункт **Свойства**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Название**|Введите новое имя ссылки на сборку.<br /><br /> Примечание. Изменив это значение, вы не измените имя сборки, на которую указывает ссылка, но зато измените имя, по которому экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] или база данных обращаются к ссылке на сборку.|  
|**Идентификатор**|Отображается идентификатор сборки, на которую указывает ссылка.|  
|**Описание**|Введите новое описание ссылки на сборку.|  
|**Отметка времени создания**|Отображает дату и время создания ссылки на сборку.|  
|**Последнее обновление схемы**|Отображается дата и время последнего обновления метаданных для ссылки на сборку.|  
|**Тип**|Отображается тип ссылки на сборку. Могут отображаться следующие значения:<br /><br /> **Сборка .NET**: ссылка на сборку указывает на [!INCLUDE[msCoName](../includes/msconame-md.md)] сборки .NET Framework.<br /><br /> **COM DLL**: ссылка на сборку указывает на библиотеку COM.|  
|**Source**|Отображается источник ссылки на сборку. Обычно это свойство содержит полный путь и имя файла сборки, на которую указывает ссылка.|  
|**Набор разрешений**|Выберите набор разрешений, используемый для определения доступа к ссылке на сборку. Дополнительные сведения о возможных значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Сведения об олицетворении**|Выберите сведения об олицетворении, используемые при обращении к ссылке на сборку. Дополнительные сведения о возможных значениях этого свойства см. в разделе [Элемент ImpersonationInfo (ASSL)](scripting/properties/impersonationinfo-element-assl.md).|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Управление сборками многомерной модели](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  