---
title: Подключаемые алгоритмы | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- third-party algorithms [Analysis Services]
- algorithms [data mining], creating
- plugin algorithms [Analysis Services]
ms.assetid: fe364ddc-576e-42fc-9ced-baa399992f92
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ac6494a438f8ecd9c1fb48cc7c2a588cfab9bd9a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66083173"
---
# <a name="plugin-algorithms"></a>Подключаемые алгоритмы
  Помимо алгоритмов [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , предоставляемых, существует множество других алгоритмов, которые можно использовать для интеллектуального анализа данных. Соответственно, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляют механизм «подключения» алгоритмов, созданных сторонними производителями. При соблюдении алгоритмами определенных стандартов их можно использовать в рамках служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] так же, как алгоритмы [!INCLUDE[msCoName](../../includes/msconame-md.md)] . Алгоритмы подключаемых модулей обладают всеми возможностями алгоритмов, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] предоставляемых.  
  
 Полное описание интерфейсов, используемых службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] для связи с подключаемыми алгоритмами, см. в примерах создания пользовательского алгоритма и пользовательского средства просмотра моделей, которые опубликованы на веб-сайте [CodePlex](https://go.microsoft.com/fwlink/?LinkID=87843) .  
  
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
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют данные COM-интерфейсы для связи с подключаемыми алгоритмами. Хотя используемые подключаемые алгоритмы должны поддерживать спецификацию [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB для интеллектуального анализа данных, им не обязательно поддерживать в спецификации все параметры интеллектуального анализа данных. Для определения возможностей алгоритма можно использовать набор строк схемы [MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset) . В наборе строк схемы перечисляются параметры поддержки интеллектуального анализа данных для каждого поставщика подключаемых алгоритмов.  
  
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
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining-algorithms-analysis-services-data-mining.md)   
 [Набор строк DMSCHEMA_MINING_SERVICES](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-services-rowset)  
  
  
