---
title: Просмотр аналитических отчетов для SQL Server обновлений
description: Просмотр аналитических отчетов в Database Experimentation Assistant
ms.custom: seo-lt-2019
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: b72d49e691311104481637ff49d6c1e09ae0c230
ms.sourcegitcommit: 9e026cfd9f2300f106af929d88a9b43301f5edc2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/22/2019
ms.locfileid: "74317744"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Просмотр аналитических отчетов в Database Experimentation Assistant

После использования Database Experimentation Assistant (ДЕА) для [создания аналитического отчета](database-experimentation-assistant-create-report.md)выполните приведенные ниже действия, чтобы ознакомиться с отчетом по анализу производительности на основе теста A/B.

## <a name="select-a-server"></a>Выберите сервер

В ДЕА выберите значок меню. В развернутом меню выберите **отчеты об анализе** рядом со значком контрольного списка, чтобы открыть окно Анализ отчетов.

В разделе **аналитические отчеты**введите имя компьютера, на котором работает SQL Server с базой данных анализа, а затем нажмите кнопку **подключить**.

![Подключение к существующему отчету](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Если у вас нет зависимостей, на странице **Предварительные требования** будут предложены ссылки для их установки. При необходимости установите необходимые компоненты и нажмите кнопку **повторить попытку**.

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

## <a name="see-also"></a>См. также:

- Чтобы узнать, как создать аналитический отчет в командной строке, см. раздел [Запуск в командной строке](database-experimentation-assistant-run-command-prompt.md).
