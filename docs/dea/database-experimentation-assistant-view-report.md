---
title: Просмотр аналитических отчетов для SQL Server обновлений
description: Просмотр аналитических отчетов в Database Experimentation Assistant
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: fddc71bf7cdf7686154b4f9b5612cf671ca64fce
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056663"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Просмотр аналитических отчетов в Database Experimentation Assistant

После [создания отчета по анализу](database-experimentation-assistant-create-report.md) в Database EXPERIMENTATION ASSISTANT (ДЕА) выполните действия, описанные в этой статье, чтобы просмотреть отчет и получить ценные сведения о производительности, предоставляемые тестом A/B.

## <a name="select-a-server"></a>Выберите сервер

В ДЕА выберите значок меню. В развернутом меню выберите **отчеты об анализе** рядом со значком контрольного списка, чтобы открыть окно Анализ отчетов.

В разделе **аналитические отчеты**введите имя компьютера, на котором работает SQL Server с базой данных анализа. Выберите **Подключиться**. 

![Подключение к существующему отчету](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Если у вас нет зависимостей, на странице **Предварительные требования** будут предложены ссылки для их установки. Установите необходимые компоненты и нажмите кнопку **повторить попытку**.

![Страница необходимых компонентов](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Выберите аналитический отчет для просмотра

В списке аналитических отчетов дважды щелкните отчет, чтобы открыть его.

![Просмотреть существующий отчет](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Вы можете получить представление о том, насколько хорошо представлена рабочая нагрузка, как показано в следующем примере диаграммы:

![Схемы рабочих нагрузок](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Просмотр и анализ отчета об анализе

В этом разделе описывается анализ отчета.

### <a name="query-categories"></a>Категории запросов

Выберите различные срезы левой круговой диаграммы, чтобы отобразить только те запросы, которые попадают в эту категорию.

![Отчет о срезах круговой диаграммы](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **Запросы с пониженной производительностью**: запросы, которые выполнялись лучше, чем в B.  
- **Ошибки**: запросы, отображающие ошибки в экземпляре B, но не в экземпляре A.  
- **Улучшенные запросы**: запросы, которые были выполнены в экземпляре B лучше, чем в экземпляре а.  
- **Неопределенные запросы**: запросы с неопределенным изменением производительности.  
- **Аналогично**: запросы, в которых производительность неизменности одинаково между экземплярами A и B.

### <a name="individual-query-drill-down"></a>Детализация отдельных запросов

Можно выбрать ссылки на шаблон запроса, чтобы просмотреть более подробные сведения о конкретных запросах.

![Детализация запроса](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Выберите конкретный запрос, чтобы открыть сводку сравнения для запроса.

![Сводка сравнения](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Вы увидите экземпляры A и B, в которых выполнялся запрос. Кроме того, можно просмотреть шаблон того, как может выглядеть запрос. В таблице отображаются сведения о запросах, относящиеся к экземплярам A и B.

### <a name="error-queries"></a>Запросы с ошибками

Сводный отчет о сравнении содержит развернутые разделы **сведений об ошибках** и **плане запросов** . В разделах показаны ошибки и сведения о плане для обоих экземпляров.

Выберите появление ошибки (красный), чтобы отобразить ошибки следующих типов:
- **Существующие ошибки**: ошибки, которые были в.
- **Новые ошибки**: ошибки в B.
- **Разрешенные ошибки**: ошибки, которые были в, но не в B.

![Диаграммы ошибок](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>Следующие шаги

- Чтобы узнать, как создать аналитический отчет в командной строке, см. раздел [Запуск в командной строке](database-experimentation-assistant-run-command-prompt.md).

- Чтобы получить 19-минутное введение в ДЕА и демонстрацию, просмотрите следующее видео:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
