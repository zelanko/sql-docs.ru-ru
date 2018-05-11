---
title: Удаление источника данных в обозревателе решений (многомерные службы SSAS) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c97ab49a703998610a4ba0daed5da5f99239dff5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a>Удаление источника данных в обозревателе решений (многомерные службы SSAS)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Удалив объект источника данных, можно окончательно исключить его из проекта многомерной модели служб Analysis Services.  
  
 В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]источники данных представляют собой основу для построения представлений источников данных, которые в свою очередь используются для определения измерений, кубов и структур интеллектуального анализа данных в проекте или базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Таким образом, удаление источника данных может сделать недействительными другие объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Перед тем как удалить объект, необходимо всегда проверять список зависимых объектов, открываемый до удаления.  
  
> [!IMPORTANT]  
>  Источники данных, от которых зависят другие объекты, не могут быть удалены из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , открытых в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети. Следует удалить все объекты в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые зависят от источника данных, до удаления его самого. Дополнительные сведения о режиме в сети см. в разделе [Подключение в режиме «в сети» к базе данных служб Analysis Services](../../analysis-services/multidimensional-models/connect-in-online-mode-to-an-analysis-services-database.md).  
  
### <a name="to-delete-a-data-source"></a>Удаление источника данных  
  
1.  Откройте проект в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]или подключитесь к базе данных, из которой необходимо удалить источник данных.  
  
2.  В **обозревателе решений**откройте папку **Источники данных** .  
  
3.  Щелкните правой кнопкой мыши источник данных и выберите пункт **Удалить**. Появится диалоговое окно **Удаление объектов**  со списком объектов, которые станут недействительными при удалении этого источника данных. Внимательно просмотрите список, прежде чем нажать кнопку **ОК** и удалить источник данных.  
  
4.  Сохраните проект.  
  
     После удаления источника данных из проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо сохранить в проекте изменения, чтобы не получить сообщение об ошибке при следующем его открытии, так как при обработке XML-файла для удаленного источника данных будет выдана ошибка.  
  
## <a name="see-also"></a>См. также  
 [Источники данных в многомерных моделях](../../analysis-services/multidimensional-models/data-sources-in-multidimensional-models.md)   
 [Поддерживаемые источники данных (службы SSAS — многомерные базы данных)](../../analysis-services/multidimensional-models/supported-data-sources-ssas-multidimensional.md)  
  
  
