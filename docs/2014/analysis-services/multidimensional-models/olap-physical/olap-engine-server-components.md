---
title: Компоненты сервера двигателя OLAP (англ.) Документы Майкрософт
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
manager: craigg
ms.openlocfilehash: 535d1e05fc82882e0a2b5ea43ac9b2147e62338b
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388018"
---
# <a name="olap-engine-server-components"></a>Серверные компоненты ядра OLAP
  Компонентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] сервера является приложение **msmdsrv.exe,** которое работает как служба Windows. Оно состоит из компонентов безопасности, компонента прослушивания XML для аналитики (XMLA), компонента обработчика запросов и множества других внутренних компонентов, выполняющих следующие функции:

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
 Компонент прослушивателя XML для аналитики обрабатывает все XMLA-взаимодействия между службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и их клиентами. Настройка [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` конфигурации в файле msmdsrv.ini может быть [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] использована для указания порта, на котором слушает экземпляр. Значение 0 указывает на то, что [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает порт по умолчанию. По умолчанию службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользуются следующими TCP-портами:

|Порт|Описание|
|----------|-----------------|
|2383|По умолчанию экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|
|2382|Редиректор для других [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]случаев .|
|Динамически назначается при запуске сервера|Названный [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]экземпляр .|

 [См. Наконфигурировать брандмауэр Windows, чтобы предоставить доступ к службам анализа](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) для получения более подробной информации.

## <a name="see-also"></a>См. также:
 [Правила наименования объектов &#40;аналитические услуги&#41;](object-naming-rules-analysis-services.md) [услуги по анализу физической архитектуры &#40;- Многомерные данные&#41;](understanding-microsoft-olap-physical-architecture.md) [Услуги анализа &#40;архитектуры - Многомерные данные&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)


