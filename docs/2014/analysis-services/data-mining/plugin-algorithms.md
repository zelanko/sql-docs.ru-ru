---
title: Подключаемые алгоритмы | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: cd32a0b9d26ae1e254c41f1390912b50d1f30629
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102318"
---
# <a name="plugin-algorithms"></a>Подключаемые алгоритмы
  Кроме алгоритмов, предусмотренных в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , существует множество других алгоритмов, которые можно использовать для интеллектуального анализа данных. Соответственно, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляют механизм «подключения» алгоритмов, созданных сторонними производителями. При соблюдении алгоритмами определенных стандартов их можно использовать в рамках служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] так же, как алгоритмы [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Подключаемые алгоритмы обладают всеми возможностями алгоритмов, предоставляемых службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Полное описание интерфейсов, используемых службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для связи с подключаемыми алгоритмами, см. в примерах создания пользовательского алгоритма и пользовательского средства просмотра моделей, которые опубликованы на веб-сайте [CodePlex](http://go.microsoft.com/fwlink/?LinkID=87843) .  
  
## <a name="algorithm-requirements"></a>Требования алгоритма  
 Для подключения алгоритма к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]необходимо реализовать следующие COM-интерфейсы:  
  
 `IDMAlgorithm`  
 Реализует алгоритм, создающий модели, и реализует операции прогнозирования итоговых моделей.  
  
 `IDMAlgorithmNavigation`  
 Позволяет обозревателям получать доступ к содержимому моделей.  
  
 `IDMPersist`  
 Позволяет сохранять и загружать модели, обучаемые алгоритмом, при помощи служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 `IDMAlgorithmMetadata`  
 Описывает возможности и входные параметры алгоритма.  
  
 `IDMAlgorithmFactory`  
 Создает экземпляры объектов, которые реализуют интерфейс алгоритма, и обеспечивает службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] доступ к интерфейсу с метаданными алгоритма.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют данные COM-интерфейсы для связи с подключаемыми алгоритмами. Хотя используемые подключаемые алгоритмы должны поддерживать спецификацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных, им не обязательно поддерживать в спецификации все параметры интеллектуального анализа данных. Для определения возможностей алгоритма можно использовать набор строк схемы [MINING_SERVICES](../schema-rowsets/data-mining/dmschema-mining-services-rowset.md) . В наборе строк схемы перечисляются параметры поддержки интеллектуального анализа данных для каждого поставщика подключаемых алгоритмов.  
  
 Прежде чем использовать новые алгоритмы со службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], их необходимо зарегистрировать. Для регистрации алгоритма включите следующие сведения в INI-файл экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , в котором необходимо включить алгоритмы:  
  
-   Название алгоритма  
  
-   ProgID (этот параметр необязателен и включается только для подключаемых алгоритмов)  
  
-   Флажок означает, включен алгоритм или нет  
  
 В следующем образце кода показана регистрация нового алгоритма:  
  
 `<ConfigurationSettings>`  
  
 `...`  
  
 `<DataMining>`  
  
 `...`  
  
 `<Algorithms>`  
  
 `...`  
  
 `<Sample_Plugin_Algorithm>`  
  
 `<Enabled>1</Enabled>`  
  
 `<ProgID>Microsoft.DataMining.SamplePlugInAlgorithm.Factory</ProgID>`  
  
 `</Sample_PlugIn_Algorithm>`  
  
 `...`  
  
 `</Algorithms>`  
  
 `...`  
  
 `</DataMining>`  
  
 `...`  
  
 `</ConfigurationSettings>`  
  
## <a name="see-also"></a>См. также  
 [Алгоритмы интеллектуального анализа данных &#40;службы Analysis Services — Интеллектуальный анализ данных&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Набор строк DMSCHEMA_MINING_SERVICES](../schema-rowsets/data-mining/dmschema-mining-services-rowset.md)  
  
  