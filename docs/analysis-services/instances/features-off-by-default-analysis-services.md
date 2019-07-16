---
title: Функции из системы по умолчанию (службы Analysis Services) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3238e09bea0ef150dde01c78ef5d2c802c1c1853
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209497"
---
# <a name="features-off-by-default-analysis-services"></a>Возможности, отключенные по умолчанию (службы Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
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
  
-   Групповая схожесть. Дополнительные сведения см. в разделе [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) .  
  
  
