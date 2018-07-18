---
title: Функции из системы по умолчанию (службы Analysis Services) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9bcb28d99f8d06430ca1ff68563e8ab8c075929f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214184"
---
# <a name="features-off-by-default-analysis-services"></a>Возможности, отключенные по умолчанию (службы Analysis Services)
  Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] по умолчанию поддерживает параметры, обеспечивающие его безопасность. Следовательно, функции, которые способны снизить безопасность, по умолчанию отключены. Следующие функции установлены в отключенном состоянии. Чтобы их использовать, их нужно специально включить.  
  
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
  
-   Групповая схожесть. Дополнительные сведения см. в разделе [Thread Pool Properties](../server-properties/thread-pool-properties.md) .  
  
  
