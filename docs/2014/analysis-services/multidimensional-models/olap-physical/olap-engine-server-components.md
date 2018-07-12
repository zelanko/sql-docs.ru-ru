---
title: Серверные компоненты ядра OLAP | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
caps.latest.revision: 39
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2471838c89fa2cfb6ded22c9daa8ad9ca6e1cfd8
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37224126"
---
# <a name="olap-engine-server-components"></a>Серверные компоненты ядра OLAP
  Серверный компонент служб [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] — **msmdsrv.exe** приложение, которое работает как служба Windows. Оно состоит из компонентов безопасности, компонента прослушивания XML для аналитики (XMLA), компонента обработчика запросов и множества других внутренних компонентов, выполняющих следующие функции:  
  
-   Синтаксический анализ инструкций, получаемых от клиентов  
  
-   Управление метаданными  
  
-   Обработка транзакций  
  
-   Обработка вычислений  
  
-   Сохранение измерения и данных ячеек  
  
-   Создание агрегатов  
  
-   Планирование запросов  
  
-   Кэширование объектов  
  
-   Управление ресурсами сервера  
  
## <a name="architectural-diagram"></a>Архитектурная диаграмма  
 Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] запускается как изолированная служба, взаимодействие с этой службой происходит через XMLA с использованием протокола HTTP или TCP. Объекты AMO — это прослойка между приложением пользователя и экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Они предоставляют доступ к административным объектам служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Объект AMO — это библиотека классов, которая принимает команды от клиентского приложения и преобразует их в XMLA-сообщения для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Объекты AMO представляют объекты экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , как классы для приложения конечного пользователя, с элементами-методами, запускающими команды и элементами-свойствами, хранящими данные объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Следующий рисунок отображает архитектуру компонентов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], включая все главные элементы, запущенные на экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], и все пользовательские компоненты, взаимодействующие с этим экземпляром. Рисунок также отображает, что единственным путем доступа к экземпляру является прослушиватель XML для аналитики или использование протокола HTTP или TCP.  
  
 ![Диаграмма архитектуры системы служб аналитики](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "диаграмма архитектуры системы служб аналитики")  
  
## <a name="xmla-listener"></a>Прослушиватель XML для аналитики  
 Компонент прослушивателя XML для аналитики обрабатывает все XMLA-взаимодействия между службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и их клиентами. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` Параметр конфигурации в файле msmdsrv.ini, может использоваться для указания порта, на котором [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр осуществляет прослушивание. Значение 0 указывает на то, что [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает порт по умолчанию. По умолчанию службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользуются следующими TCP-портами:  
  
|Порт|Описание|  
|----------|-----------------|  
|2383|Экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]по умолчанию.|  
|2382|Перенаправитель для других экземпляров служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|Динамически назначается при запуске сервера|Именованный экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 См. в разделе [Настройка брандмауэра Windows на разрешение доступа к Analysis Services](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [Правила именования объектов &#40;служб Analysis Services&#41;](object-naming-rules-analysis-services.md)   
 [Физическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](understanding-microsoft-olap-physical-architecture.md)   
 [Логическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
