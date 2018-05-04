---
title: Серверные компоненты ядра OLAP | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43d15eaa7500362cc34f21994441b19f080c5773
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="olap-engine-server-components"></a>Серверные компоненты ядра OLAP
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
 ![Диаграмма архитектуры системы служб аналитики](../../../analysis-services/data-mining/media/analysisservicessystemarchitecture.gif "диаграмма архитектуры системы служб аналитики")  
  
## <a name="xmla-listener"></a>Прослушиватель XML для аналитики  
 Компонент прослушивателя XML для аналитики обрабатывает все XMLA-взаимодействия между службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и их клиентами. Параметр конфигурации [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] **Порт** , указанный в файле msmdsrv.ini, может использоваться для указания порта, на котором экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] выполняет прослушивание. Значение 0 указывает на то, что [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает порт по умолчанию. По умолчанию службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользуются следующими TCP-портами:  
  
|Порт|Описание|  
|----------|-----------------|  
|2383|Экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]по умолчанию.|  
|2382|Перенаправитель для других экземпляров служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|Динамически назначается при запуске сервера|Именованный экземпляр служб [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 В разделе [Configure Windows Firewall to Allow Analysis Services Access](../../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) для получения дополнительных сведений.  
  
## <a name="see-also"></a>См. также  
 [Правила именования объектов &#40;служб Analysis Services&#41;](../../../analysis-services/multidimensional-models/olap-physical/object-naming-rules-analysis-services.md)   
 [Физическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../../../analysis-services/multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md)   
 [Логическая архитектура &#40;службы Analysis Services — многомерные данные&#41;](../../../analysis-services/multidimensional-models/olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
