---
title: Службы Analysis Services Personalization Extensions | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- personalization extensions [Multidimensional Databases]
ms.assetid: 0f144059-24e0-40c0-bde4-d48c75e46598
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 313b1764dfb17c3a8b49fa3ffa139668f9b2b421
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62726120"
---
# <a name="analysis-services-personalization-extensions"></a>Модули персонализации служб Analysis Services
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модули персонализации служб являются основой лежат в основе архитектуры подключаемых модулей. С помощью архитектуры подключаемых модулей можно динамически разрабатывать новые объекты кубов и функциональность и легко обмениваться ими с другими разработчиками. Таким образом [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модулей персонализации служб предоставляют функциональность, позволяет добиться следующего:  
  
-   **Динамическое проектирование и разработка** сразу же после создания и развертывания [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модулей персонализации, пользователи имеют доступ к объектам и функциональности в начале следующего сеанса пользователя.  
  
-   **Независимость интерфейсов** независимо от того, интерфейс, который используется для создания [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модулей персонализации, пользователи могут использовать любой интерфейс для доступа к объектам и функциональности.  
  
-   **Контекст сеанса** [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модулей персонализации не являются постоянными объектами в существующей инфраструктуре и не требуют куба для повторной обработки. Они создаются для пользователя, когда он подключается к базе данных, и остаются доступными на протяжении пользовательского сеанса.  
  
-   **Быстрое распространение** общего ресурса [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] модулей персонализации с другими разработчиками программного обеспечения, не нужно изучать подробные спецификации о том, где или как найти это расширенная функциональность.  
  
 Модули персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеют множество возможных применений. Например, компания продает товар за различные виды валют. Можно создать вычисляемый элемент, возвращающий общую цифру продаж в местной валюте пользователя, который просматривает куб. Этот элемент создается как модуль персонализации. Затем этот вычисляемый элемент можно сделать общим для группы пользователей. Как только элемент сделан общим, пользователи немедленно получают доступ к вычисляемому элементу, как только подключатся к серверу. Они получат доступ к элементу, даже если интерфейс, которым они пользуются, отличен от использованного при создании вычисляемого элемента.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширения персонализации простое и элегантное изменение существующей архитектуры управляемых сборок и предоставляются на протяжении всего [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <xref:Microsoft.AnalysisServices.AdomdServer> объектов модели, синтаксис многомерных выражений (MDX) и наборы строк схемы.  
  
## <a name="logical-architecture"></a>Логическая архитектура  
 Архитектура модулей персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] основана на архитектуре управляемых сборок и следующих четырех основных элементах.  
  
 Специальный атрибут [PlugInAttribute]  
 При запуске службы, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] загружает необходимые сборки и определяет, какие классы имеют <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute> настраиваемого атрибута.  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] определяет специальные атрибуты как способ описания программного кода и влияния на поведение времени выполнения. Дополнительные сведения см. в разделе "[Обзор атрибутов](https://go.microsoft.com/fwlink/?LinkId=82929),» в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] руководства для разработчиков на сайте MSDN.  
  
 Для всех классов, содержащих <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute> настраиваемого атрибута [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] вызывают конструкторы по умолчанию. Вызов всех конструкторов при запуске представляет собой удобный, из которого выполняется построение новых объектов и независимо от действий пользователя.  
  
 Конструктор класса, помимо построения небольшого кэша информации о разработке и управлении модулями персонализации, обычно подписывается на события <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened> и <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>. Если класс не подписан на эти события, он может быть ошибочно помечен для удаления сборщиком мусора среды CLR.  
  
 Контекст сеанса  
 Для объектов, основанных на модулях персонализации, службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создают среду выполнения во время клиентского сеанса и динамически строят большинство объектов этой среды. Эта среда выполнения, как и любая другая сборка CLR, имеет доступ к другим функциям и хранимым процедурам. При завершении сеанса пользователя, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] удаляет динамически созданные объекты и закрывают среду выполнения.  
  
 События  
 Создание объекта запускается событиями сеанса `On-Cube-OpenedCubeOpened` и `On-Cube-ClosingCubeClosing`.  
  
 Связь между клиентом и сервером происходит посредством определенных событий. Эти события сообщают клиенту о ситуациях, в результате которых создаются клиентские объекты. Среда клиента создается динамически с помощью двух наборов событий: события сеанса и события куба.  
  
 События сеанса связаны с объектом сервера. При входе клиента на сервере, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создает сеанс и запускают <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened> событий. Когда клиент закрывает сеанс на сервере, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] триггеры <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing> событий.  
  
 События куба связаны с объектом соединения. Соединение с кубом запускает событие <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeOpened>. Закрытие соединения с кубом — посредством закрытия куба или переключения на другой куб — запускает событие <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeClosing>.  
  
 Трассировка и обработка ошибок  
 С помощью приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] можно трассировать любые действия. Необработанные ошибки заносятся в журнал событий Windows.  
  
 Всякое создание объектов и управление ими происходит независимо от этой архитектуры, и за него отвечают разработчики этих объектов.  
  
## <a name="infrastructure-foundations"></a>Основания инфраструктуры  
 Модули персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] основаны на существующих компонентах. Далее следует сводка усовершенствований и улучшений, обеспечивающих функциональность модулей персонализации.  
  
### <a name="assemblies"></a>Сборки  
 Специальный атрибут <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute> можно добавлять в пользовательские сборки, чтобы опознать классы модулей персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
### <a name="changes-to-the-adomdserver-object-model"></a>Изменения модели объектов AdomdServer  
 Следующие объекты в модели объектов <xref:Microsoft.AnalysisServices.AdomdServer> были улучшены или добавлены.  
  
#### <a name="new-adomdconnection-class"></a>Новый класс AdomdConnection  
 Новый класс <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection> содержит несколько модулей персонализации, доступ к которым предоставляется через свойства и события.  
  
 **Свойства**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.SessionID%2A> — строковое значение, представляющее собой идентификатор сеанса текущего соединения (только для чтения).  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.ClientCulture%2A> — ссылка на культуру заказчика, связанная с текущим сеансом (только для чтения).  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.User%2A> — ссылка на интерфейс идентификации, представляющий текущего пользователя (только для чтения).  
  
 **События**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeOpened>  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeClosing>  
  
#### <a name="new-properties-in-the-context-class"></a>Новые свойства в классе Context  
 У класса <xref:Microsoft.AnalysisServices.AdomdServer.Context> появились два новых свойства:  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Context.Server%2A> — ссылка на новый объект сервера (только для чтения);  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentConnection%2A> — ссылка на новый объект <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection> (только для чтения).  
  
#### <a name="new-server-class"></a>Новый класс Server  
 Новый класс <xref:Microsoft.AnalysisServices.AdomdServer.Server> содержит несколько модулей персонализации, доступ к которым предоставляется через свойства и события.  
  
 **Свойства**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Name%2A> — строка, представляющая собой имя сервера (только для чтения).  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Culture%2A> — ссылка на глобальную культуру, связанную с сервером.  
  
 **События**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened>  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>  
  
#### <a name="adomdcommand-class"></a>Класс AdomdCommand  
 Класс <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> теперь поддерживает следующие команды многомерных выражений:  
  
-   [Инструкция CREATE MEMBER (многомерные выражения)](/sql/mdx/mdx-data-definition-create-member)  
  
-   [Инструкция UPDATE MEMBER &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-update-member)  
  
-   [Инструкция DROP MEMBER &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-drop-member)  
  
-   [Инструкция CREATE SET (многомерные выражения)](/sql/mdx/mdx-data-definition-create-set)  
  
-   [Инструкция DROP SET &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-drop-set)  
  
-   [Инструкция CREATE KPI &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-create-kpi)  
  
-   [Инструкцию DROP KPI &#40;многомерных Выражений&#41;](/sql/mdx/mdx-data-definition-drop-kpi)  
  
### <a name="mdx-extensions-and-enhancements"></a>Расширения и усовершенствования многомерных выражений  
 Команда CREATE MEMBER улучшена добавлением свойств `caption`,  `display_folder` и `associated_measure_group`.  
  
 Добавлена новая команда UPDATE MEMBER, чтобы избежать повторного создания элемента, если необходимо обновление с последующей потерей порядка вычислений. Обновления не могут изменить область вычисляемого элемента, переместить вычисляемый элемент к другому родителю или определить другой `solveorder`.  
  
 Команда CREATE SET улучшена добавлением свойств `caption` и `display_folder` и новым ключевым словом `STATIC | DYNAMIC`. *Статические* означает, что набор вычисляется только во время создания. *Динамические* означает, что набор вычисляется при каждом его использовании в запросе. Если ключевое слово отсутствует, значение по умолчанию — `STATIC`.  
  
 В синтаксис многомерных выражений добавлены команды CREATE KPI и DROP KPI. Ключевые показатели эффективности можно создавать динамически из любого скрипта многомерных выражений.  
  
### <a name="schema-rowsets-extensions"></a>Расширения наборов строк схем  
 На MDSCHEMA_MEMBERS *область* добавляется столбец. Область значения определяются следующим образом: MDMEMBER_SCOPE_GLOBAL = 1, MDMEMBER_SCOPE_SESSION = 2.  
  
 На MDSCHEMA_SETS *set_evaluation_context* добавляется столбец. Ниже приведены значения контекста вычислений. MDSET_RESOLUTION_STATIC = 1, MDSET_RESOLUTION_DYNAMIC = 2.  
  
 Добавлен столбец scope  в набор строк схемы MDSCHEMA_KPIS. Область значения определяются следующим образом: MDKPI_SCOPE_GLOBAL = 1, MDKPI_SCOPE_SESSION = 2.  
  
  
