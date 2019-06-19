---
title: Диалоговое окно «Свойства сборки» (службы Analysis Services — многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b21230ddff5a3db043b533a4f921a30b02da739b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062299"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>Диалоговое окно «Свойства сборки» (службы Analysis Services — многомерные данные)
  Диалоговое окно **Свойства сборки** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] используется для задания свойств ссылки на сборку в базе данных служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Чтобы отобразить диалоговое окно **Свойства сборки** , можно щелкнуть правой кнопкой мыши сборку в **обозревателе объектов** и выбрать пункт **Свойства**.  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Name**|Введите новое имя ссылки на сборку.<br /><br /> Примечание. Изменение этого значения не изменяет имя сборки, на который ссылается ссылки на сборку, но зато измените имя, используемое с [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] экземпляра или базы данных, при ссылке на сборку.|  
|**Идентификатор**|Отображается идентификатор сборки, на которую указывает ссылка.|  
|**Описание**|Введите новое описание ссылки на сборку.|  
|**Отметка времени создания**|Отображает дату и время создания ссылки на сборку.|  
|**Последнее обновление схемы**|Отображается дата и время последнего обновления метаданных для ссылки на сборку.|  
|**Тип**|Отображается тип ссылки на сборку. Могут отображаться следующие значения:<br /><br /> **Сборка .NET** Ссылка указывает на сборку [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework.<br /><br /> **COM DLL** Ссылка на сборку указывает на библиотеку COM.|  
|**Source**|Отображается источник ссылки на сборку. Обычно это свойство содержит полный путь и имя файла сборки, на которую указывает ссылка.|  
|**Набор разрешений**|Выберите набор разрешений, используемый для определения доступа к ссылке на сборку. Дополнительные сведения о возможных значениях этого свойства см. в разделе <xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>.|  
|**Сведения об олицетворении**|Выберите сведения об олицетворении, используемые при обращении к ссылке на сборку. Дополнительные сведения о возможных значениях этого свойства см. в разделе [Элемент ImpersonationInfo (ASSL)](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl).|  
  
## <a name="see-also"></a>См. также  
 [Конструкторы и диалоговые окна служб Analysis Services &#40;многомерных данных&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [Управление сборками многомерной модели](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
