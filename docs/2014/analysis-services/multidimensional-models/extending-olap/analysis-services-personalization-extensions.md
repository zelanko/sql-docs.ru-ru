---
title: Analysis Services расширения персонализации | Документация Майкрософт
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
ms.openlocfilehash: 0cd36cb2882659bff902d9830af0c5acefd98444
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468979"
---
# <a name="analysis-services-personalization-extensions"></a>Модули персонализации служб Analysis Services
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]расширения персонализации являются основой реализации архитектуры подключаемых модулей. С помощью архитектуры подключаемых модулей можно динамически разрабатывать новые объекты кубов и функциональность и легко обмениваться ими с другими разработчиками. Таким образом, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширения персонализации предоставляют функциональные возможности, позволяющие достичь следующих возможностей:  
  
-   **Динамическое проектирование и развертывание** Сразу после проектирования и развертывания [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширений персонализации пользователи получают доступ к объектам и функциям в начале следующего сеанса пользователя.  
  
-   **Независимость от интерфейса** Независимо от интерфейса, используемого для создания [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширений персонализации, пользователи могут использовать любой интерфейс для доступа к объектам и функциональным возможностям.  
  
-   **Контекст сеанса** [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширения персонализации не являются постоянными объектами в существующей инфраструктуре и не нуждаются в повторной обработке куба. Они создаются для пользователя, когда он подключается к базе данных, и остаются доступными на протяжении пользовательского сеанса.  
  
-   **Быстрое распределение** Обменивайтесь [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] расширениями персонализации с другими разработчиками программного обеспечения, не обращаясь к подробным сведениям о том, где или как найти эту расширенную функциональность.  
  
 Модули персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] имеют множество возможных применений. Например, компания продает товар за различные виды валют. Можно создать вычисляемый элемент, возвращающий общую цифру продаж в местной валюте пользователя, который просматривает куб. Этот элемент создается как модуль персонализации. Затем этот вычисляемый элемент можно сделать общим для группы пользователей. Как только элемент сделан общим, пользователи немедленно получают доступ к вычисляемому элементу, как только подключатся к серверу. Они получат доступ к элементу, даже если интерфейс, которым они пользуются, отличен от использованного при создании вычисляемого элемента.  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]расширения персонализации — это простое и элегантное изменение существующей архитектуры управляемой сборки. они доступны во всей [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] объектной модели [Microsoft. AnalysisServices. того объектная AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) , синтаксисе многомерных выражений и наборах строк схемы.  
  
## <a name="logical-architecture"></a>Логическая архитектура  
 Архитектура модулей персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] основана на архитектуре управляемых сборок и следующих четырех основных элементах.  
  
 Специальный атрибут [PlugInAttribute]  
 При запуске службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] загружает необходимые сборки и определяет, какие классы имеют настраиваемый атрибут [Microsoft. AnalysisServices. того объектная AdomdServer. плугинаттрибуте](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120)) .  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] определяет специальные атрибуты как способ описания программного кода и влияния на поведение времени выполнения. Дополнительные сведения см. в разделе «[Общие сведения об атрибутах](https://go.microsoft.com/fwlink/?LinkId=82929)» в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Руководстве разработчика на сайте MSDN.  
  
 Для всех классов с пользовательским атрибутом [Microsoft. AnalysisServices. того объектная AdomdServer. плугинаттрибуте](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120)) [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] вызывает конструкторы по умолчанию. Вызов всех конструкторов при запуске представляет собой удобный момент для построения новых объектов независимо от действий пользователя.  
  
 Помимо создания небольшого кэша информации о создании и управлении расширениями персонализации, конструктор класса обычно подписывается на события [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionOpened](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120)) и [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionClosing](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120)) . Если класс не подписан на эти события, он может быть ошибочно помечен для удаления сборщиком мусора среды CLR.  
  
 Контекст сеанса  
 Для объектов, основанных на модулях персонализации, службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создают среду выполнения во время клиентского сеанса и динамически строят большинство объектов этой среды. Эта среда выполнения, как и любая другая сборка CLR, имеет доступ к другим функциям и хранимым процедурам. По окончании сеанса пользователя [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] удаляет динамически созданные объекты и закрывает среду выполнения.  
  
 События  
 Создание объекта запускается событиями сеанса `On-Cube-OpenedCubeOpened` и `On-Cube-ClosingCubeClosing`.  
  
 Связь между клиентом и сервером происходит посредством определенных событий. Эти события сообщают клиенту о ситуациях, в результате которых создаются клиентские объекты. Среда клиента создается динамически с помощью двух наборов событий: события сеанса и события куба.  
  
 События сеанса связаны с объектом сервера. Когда клиент входит в систему на сервере, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] создает сеанс и запускает событие [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionOpened](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120)) . Когда клиент завершает сеанс на сервере, [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] запускает событие [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionClosing](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120)) .  
  
 События куба связаны с объектом соединения. При подключении к кубу вызывается событие [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. CubeOpened](/previous-versions/sql/sql-server-2014/bb630581(v=sql.120)) . Закрытие соединения с кубом путем закрытия куба или перехода к другому Кубу вызывает событие [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. CubeClosing](/previous-versions/sql/sql-server-2014/bb630371(v=sql.120)) .  
  
 Трассировка и обработка ошибок  
 С помощью приложения [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] можно трассировать любые действия. Необработанные ошибки заносятся в журнал событий Windows.  
  
 Всякое создание объектов и управление ими происходит независимо от этой архитектуры, и за него отвечают разработчики этих объектов.  
  
## <a name="infrastructure-foundations"></a>Основания инфраструктуры  
 Модули персонализации служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] основаны на существующих компонентах. Далее следует сводка усовершенствований и улучшений, обеспечивающих функциональность модулей персонализации.  
  
### <a name="assemblies"></a>Сборки  
 Пользовательский атрибут [Microsoft. AnalysisServices. того объектная AdomdServer. плугинаттрибуте](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120))можно добавить в пользовательские сборки для обнаружения [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] классов расширений персонализации.  
  
### <a name="changes-to-the-adomdserver-object-model"></a>Изменения модели объектов AdomdServer  
 Следующие объекты в объектной модели [Microsoft. AnalysisServices. того объектная AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) были расширены или добавлены в модель.  
  
#### <a name="new-adomdconnection-class"></a>Новый класс AdomdConnection  
 Класс [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection](/previous-versions/sql/sql-server-2014/bb678193(v=sql.120)) является новым и предоставляет несколько расширений персонализации через свойства и события.  
  
 **Свойства**  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. SessionID *](/previous-versions/sql/sql-server-2014/bb678099(v=sql.120)), доступное только для чтения строковое значение, представляющее идентификатор сеанса текущего соединения.  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. клиенткултуре *](/previous-versions/sql/sql-server-2014/bb677433(v=sql.120)), доступная только для чтения ссылка на язык и региональные параметры клиента, связанные с текущим сеансом.  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. User *](/previous-versions/sql/sql-server-2014/bb630315(v=sql.120))— доступная только для чтения ссылка на интерфейс идентификации, представляющий текущего пользователя.  
  
 **События**  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. CubeOpened](/previous-versions/sql/sql-server-2014/bb630581(v=sql.120))  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection. CubeClosing](/previous-versions/sql/sql-server-2014/bb630371(v=sql.120))  
  
#### <a name="new-properties-in-the-context-class"></a>Новые свойства в классе Context  
 Класс [Microsoft. AnalysisServices. того объектная AdomdServer. Context](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120)) имеет два новых свойства:  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. Context. Server *](/previous-versions/sql/sql-server-2014/bb678098(v=sql.120))— доступная только для чтения ссылка на новый объект Server.  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. Context. куррентконнектион *](/previous-versions/sql/sql-server-2014/bb630975(v=sql.120))— это доступная только для чтения ссылка на новый объект [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdConnection](/previous-versions/sql/sql-server-2014/bb678193(v=sql.120)) .  
  
#### <a name="new-server-class"></a>Новый класс Server  
 Класс [Microsoft. AnalysisServices. того объектная AdomdServer. Server](/previous-versions/sql/sql-server-2014/bb677955(v=sql.120)) является новым и предоставляет несколько расширений персонализации через свойства и события класса.  
  
 **Свойства**  
  
-   [Microsoft.AnalysisServices.AdomdServer.Server.Name *](/previous-versions/sql/sql-server-2014/bb677694(v=sql.120))— доступное только для чтения строковое значение, представляющее имя сервера.  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. Server. culture *](/previous-versions/sql/sql-server-2014/bb677437(v=sql.120)), доступная только для чтения ссылка на глобальный язык и региональные параметры, связанные с сервером.  
  
 **События**  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionOpened](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))  
  
-   [Microsoft. AnalysisServices. того объектная AdomdServer. Server. SessionClosing](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))  
  
#### <a name="adomdcommand-class"></a>Класс AdomdCommand  
 Класс [Microsoft. AnalysisServices. того объектная AdomdServer. AdomdCommand](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120)) теперь поддерживает следующие команды многомерных выражений:  
  
-   [Инструкция CREATE MEMBER (многомерные выражения)](/sql/mdx/mdx-data-definition-create-member)  
  
-   [Инструкция обновления элемента &#40;многомерных выражений&#41;](/sql/mdx/mdx-data-definition-update-member)  
  
-   [Инструкция DROP MEMBER &#40;&#41;многомерных выражений](/sql/mdx/mdx-data-definition-drop-member)  
  
-   [Инструкция CREATE SET (многомерные выражения)](/sql/mdx/mdx-data-definition-create-set)  
  
-   [Инструкция DROP SET &#40;&#41;многомерных выражений](/sql/mdx/mdx-data-definition-drop-set)  
  
-   [Инструкция CREATE KPI &#40;&#41;многомерных выражений](/sql/mdx/mdx-data-definition-create-kpi)  
  
-   [Инструкция DROP KPI &#40;&#41;многомерных выражений](/sql/mdx/mdx-data-definition-drop-kpi)  
  
### <a name="mdx-extensions-and-enhancements"></a>Расширения и усовершенствования многомерных выражений  
 Команда CREATE MEMBER улучшена добавлением свойств `caption`,  `display_folder` и `associated_measure_group`.  
  
 Добавлена новая команда UPDATE MEMBER, чтобы избежать повторного создания элемента, если необходимо обновление с последующей потерей порядка вычислений. Обновления не могут изменить область вычисляемого элемента, переместить вычисляемый элемент к другому родителю или определить другой `solveorder`.  
  
 Команда CREATE SET улучшена добавлением свойств `caption` и `display_folder` и новым ключевым словом `STATIC | DYNAMIC`. *Статическое* значение означает, что набор вычисляется только во время создания. *Dynamic* означает, что набор вычисляется каждый раз, когда набор используется в запросе. Если ключевое слово отсутствует, значение по умолчанию — `STATIC`.  
  
 В синтаксис многомерных выражений добавлены команды CREATE KPI и DROP KPI. Ключевые показатели эффективности можно создавать динамически из любого скрипта многомерных выражений.  
  
### <a name="schema-rowsets-extensions"></a>Расширения наборов строк схем  
 Добавляется столбец *области* MDSCHEMA_MEMBERS. Значения области выглядят следующим образом: MDMEMBER_SCOPE_GLOBAL = 1, MDMEMBER_SCOPE_SESSION = 2.  
  
 В MDSCHEMA_SETS столбец *set_evaluation_context* добавлен. Задайте следующие значения контекста вычисления: MDSET_RESOLUTION_STATIC = 1, MDSET_RESOLUTION_DYNAMIC = 2.  
  
 Добавлен столбец scope  в набор строк схемы MDSCHEMA_KPIS. Значения области выглядят следующим образом: MDKPI_SCOPE_GLOBAL = 1, MDKPI_SCOPE_SESSION = 2.  
  
  
