---
title: Удаление источника данных в обозревателе решений (многомерные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.deleteobjects.f1
helpviewer_keywords:
- data sources [Analysis Services], deleting
- deleting data sources
- removing data sources
ms.assetid: b45441ef-f909-4736-98b9-cc80d0acac99
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 648c974b1a23128c9d6c6e3977494291ef182510
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48113350"
---
# <a name="delete-a-data-source-in-solution-explorer-ssas-multidimensional"></a>Удаление источника данных в обозревателе решений (многомерные службы SSAS)
  Удалив объект источника данных, можно окончательно исключить его из проекта многомерной модели служб Analysis Services.  
  
 В службах [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]источники данных представляют собой основу для построения представлений источников данных, которые в свою очередь используются для определения измерений, кубов и структур интеллектуального анализа данных в проекте или базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Таким образом, удаление источника данных может сделать недействительными другие объекты служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в проекте служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] . Перед тем как удалить объект, необходимо всегда проверять список зависимых объектов, открываемый до удаления.  
  
> [!IMPORTANT]  
>  Источники данных, от которых зависят другие объекты, не могут быть удалены из базы данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , открытых в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] в режиме в сети. Следует удалить все объекты в базе данных служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , которые зависят от источника данных, до удаления его самого. Дополнительные сведения о режиме в сети см. в разделе [Connect in Online Mode to an Analysis Services Database](connect-in-online-mode-to-an-analysis-services-database.md).  
  
### <a name="to-delete-a-data-source"></a>Удаление источника данных  
  
1.  Откройте проект в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]или подключитесь к базе данных, из которой необходимо удалить источник данных.  
  
2.  В **обозревателе решений**откройте папку **Источники данных** .  
  
3.  Щелкните правой кнопкой мыши источник данных и выберите пункт **Удалить**. Появится диалоговое окно **Удаление объектов**  со списком объектов, которые станут недействительными при удалении этого источника данных. Внимательно просмотрите список, прежде чем нажать кнопку **ОК** и удалить источник данных.  
  
4.  Сохраните проект.  
  
     После удаления источника данных из проекта служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо сохранить в проекте изменения, чтобы не получить сообщение об ошибке при следующем его открытии, так как при обработке XML-файла для удаленного источника данных будет выдана ошибка.  
  
## <a name="see-also"></a>См. также  
 [Источники данных в многомерных моделях](data-sources-in-multidimensional-models.md)   
 [Источники данных, поддерживаемые &#40;многомерные службы SSAS&#41;](supported-data-sources-ssas-multidimensional.md)  
  
  
