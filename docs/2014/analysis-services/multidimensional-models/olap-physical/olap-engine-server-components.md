---
title: Компоненты сервера ядра OLAP | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
ms.openlocfilehash: b60d721a69213ad52536830b49b40d6bb82a3811
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84545936"
---
# <a name="olap-engine-server-components"></a>Серверные компоненты ядра OLAP
  Серверный компонент компонента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] — это **msmdsrv.exe** приложение, которое выполняется как служба Windows. Оно состоит из компонентов безопасности, компонента прослушивания XML для аналитики (XMLA), компонента обработчика запросов и множества других внутренних компонентов, выполняющих следующие функции:

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

 ![Диаграмма архитектуры системы служб Analysis Services](../../../analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Диаграмма архитектуры системы служб Analysis Services")

## <a name="xmla-listener"></a>Прослушиватель XML для аналитики
 Компонент прослушивателя XML для аналитики обрабатывает все XMLA-взаимодействия между службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и их клиентами. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` Параметр конфигурации в файле msmdsrv.ini можно использовать для указания порта, который [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает экземпляр. Значение 0 указывает на то, что [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает порт по умолчанию. По умолчанию службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользуются следующими TCP-портами:

|Порт|Описание|
|----------|-----------------|
|2383|Экземпляр по умолчанию [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|
|2382|Перенаправитель для других экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|
|Динамически назначается при запуске сервера|Именованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .|

 Дополнительные сведения см. в разделе [Настройка брандмауэра Windows для разрешения Analysis Servicesного доступа](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .

## <a name="see-also"></a>См. также:
 [Правила именования объектов &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md) [физическую архитектуру &#40;Analysis Services — многомерные данные&#41;](understanding-microsoft-olap-physical-architecture.md) [логическая архитектура &#40;Analysis Services — многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)


