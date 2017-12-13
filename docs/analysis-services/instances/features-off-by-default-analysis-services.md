---
title: "Функции из системы по умолчанию (службы Analysis Services) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: "5"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 644101b1010028ac88066f44f2b4427776ca983f
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="features-off-by-default-analysis-services"></a>Возможности, отключенные по умолчанию (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] обеспечивают безопасность по умолчанию. Следовательно, функции, которые способны снизить безопасность, по умолчанию отключены. Следующие функции установлены в отключенном состоянии. Чтобы их использовать, их нужно специально включить.  
  
## <a name="feature-list"></a>Список функций  
 Чтобы включить следующие функции, подключитесь к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Правой кнопкой мыши щелкните имя экземпляра и выберите пункт **Аспекты**. Или можно воспользоваться свойствами сервера, как описано в следующем разделе.  
  
-   Нерегламентированные запросы интеллектуального анализа данных (OpenRowset)  
  
-   Связанные объекты (к)  
  
-   Связанные объекты (от)  
  
-   Прослушивание только локальных соединений  
  
-   Определенные пользователем функции  
  
## <a name="server-properties"></a>Свойства сервера  
 Дополнительные отключенные по умолчанию функции можно включить с помощью свойств сервера. Подключитесь к [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Правой кнопкой мыши щелкните имя экземпляра и выберите пункт **Свойства**. Щелкните **Общие**, а затем щелкните **Показать дополнительные** , чтобы отобразить длинный список свойств.  
  
-   Нерегламентированные запросы интеллектуального анализа данных (OpenRowset)  
  
-   Разрешить сеансные модели интеллектуального анализа данных (интеллектуальный анализ данных)  
  
-   Связанные объекты (к)  
  
-   Связанные объекты (от)  
  
-   Определенные пользователем функции на базе COM  
  
-   Определения отслеживаний «черного ящика» (шаблоны).  
  
-   Ведение журнала запросов  
  
-   Прослушивание только локальных соединений  
  
-   Двоичный XML-файл  
  
-   Сжатие  
  
-   Групповая схожесть. Дополнительные сведения см. в разделе [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) .  
  
  
