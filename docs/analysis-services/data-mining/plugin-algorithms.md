---
title: Подключаемые алгоритмы | Документы Microsoft
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6ad5f7d214b5b8f1763041f139fc57a84a9c1be6
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="plugin-algorithms"></a>Подключаемые алгоритмы
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Кроме алгоритмов, предусмотренных в службах [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , существует множество других алгоритмов, которые можно использовать для интеллектуального анализа данных. Соответственно, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляют механизм «подключения» алгоритмов, созданных сторонними производителями. При соблюдении алгоритмами определенных стандартов их можно использовать в рамках служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] так же, как алгоритмы [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Подключаемые алгоритмы обладают всеми возможностями алгоритмов, предоставляемых службами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] .  
  
 Полное описание интерфейсов, используемых службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для связи с подключаемыми алгоритмами, см. в примерах создания пользовательского алгоритма и пользовательского средства просмотра моделей, которые опубликованы на веб-сайте [CodePlex](http://go.microsoft.com/fwlink/?LinkID=87843) .  
  
## <a name="algorithm-requirements"></a>Требования алгоритма  
 Для подключения алгоритма к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]необходимо реализовать следующие COM-интерфейсы:  
  
 **IDMAlgorithm**  
 Реализует алгоритм, создающий модели, и реализует операции прогнозирования итоговых моделей.  
  
 **IDMAlgorithmNavigation**  
 Позволяет обозревателям получать доступ к содержимому моделей.  
  
 **IDMPersist**  
 Позволяет сохранять и загружать модели, обучаемые алгоритмом, при помощи служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 **IDMAlgorithmMetadata**  
 Описывает возможности и входные параметры алгоритма.  
  
 **IDMAlgorithmFactory**  
 Создает экземпляры объектов, которые реализуют интерфейс алгоритма, и обеспечивает службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] доступ к интерфейсу с метаданными алгоритма.  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]использует данные COM-интерфейсы для связи с подключаемыми алгоритмами. Хотя используемые подключаемые алгоритмы должны поддерживать спецификацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных, им не обязательно поддерживать в спецификации все параметры интеллектуального анализа данных. Для определения возможностей алгоритма можно использовать набор строк схемы [MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md) . В наборе строк схемы перечисляются параметры поддержки интеллектуального анализа данных для каждого поставщика подключаемых алгоритмов.  
  
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
 [Алгоритмы интеллектуального анализа данных & #40; Службы Analysis Services — Интеллектуальный анализ данных & #41;](../../analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Набор строк DMSCHEMA_MINING_SERVICES](../../analysis-services/schema-rowsets/data-mining/dmschema-mining-services-rowset.md)  
  
  
