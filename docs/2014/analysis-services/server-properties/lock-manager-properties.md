---
title: Свойства диспетчера блокировок | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- lock manager properties [Analysis Services]
- LockWaitGranularityMS property
- DefaultLockTimeoutMS property
- DeadlockDetectionGranularityMS property
ms.assetid: 15fe9ead-825b-4ac3-9191-7a07caa2861b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: f773eb7fb512b9b1ae14b14a13717ecc8f42599f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62747246"
---
# <a name="lock-manager-properties"></a>Свойства диспетчера блокировок
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] поддерживают свойства сервера диспетчера блокировок, перечисленные в следующей таблице. Дополнительные сведения о дополнительных свойствах сервера и об их настройке см. в разделе [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).  
  
 **Применимо к:** Многомерный и Табличный режим сервера  
  
## <a name="properties"></a>Свойства  
 `DefaultLockTimeoutMS`  
 32-разрядное целочисленное свойство со знаком, которое определяет время ожидания блокировки по умолчанию в миллисекундах для внутренних запросов блокировки.  
  
 Значение по умолчанию для этого свойства -1, что соответствует отсутствию времени ожидания для внутренних запросов блокировки.  
  
 `LockWaitGranularityMS`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 `DeadlockDetectionGranularityMS`  
 Дополнительное свойство, которое следует изменять только под руководством службы поддержки [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера в службах Analysis Services](server-properties-in-analysis-services.md)   
 [Определение режима работы сервера экземпляра служб Analysis Services](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
