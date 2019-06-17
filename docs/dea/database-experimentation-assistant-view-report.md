---
title: Просмотр отчетов по анализу в помощнике по базе данных службы "Экспериментирование" для обновления до SQL Server
description: Просмотр отчетов по анализу в помощнике по базе данных службы "Экспериментирование"
ms.custom: ''
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
manager: jroth
ms.openlocfilehash: da99a24ab6729e78220aeed3d18819e7b075603f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794437"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>Просмотр отчетов по анализу в помощнике по базе данных службы "Экспериментирование"

После того как вы [создания отчета анализа](database-experimentation-assistant-create-report.md) в базе данных службы "Экспериментирование" Assistant (веб), выполните действия, описанные в этой статье, для просмотра отчета и получение ценных сведений о производительности, предоставляемых вашей A / B-тестирования.

## <a name="select-a-server"></a>Выберите сервер

В Инициатив выберите значок "меню". В развернутом меню, выберите **отчеты с анализом** рядом со значком контрольный список, чтобы открыть окно отчеты с анализом.

В разделе **отчеты с анализом**, введите имя компьютера под управлением SQL Server, который имеет базы данных служб analysis. Выберите **Подключиться**. 

![Подключиться к существующему отчету](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

Если вы пропустили все зависимости **предварительные требования** страницы подскажет вам ссылки для их установки. Установите необходимые компоненты, а затем выберите **повторите попытку**.

![Страница предварительных требований](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>Выберите отчет анализа для просмотра

В списке отчеты с анализом дважды щелкните отчет, чтобы открыть его.

![Просмотр существующего отчета](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

Вы можете получить ценные сведения о того, насколько хорошо представлена рабочей нагрузки, как показано на этой диаграмме примере:

![Инструкция Rep рабочей нагрузки диаграммы](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>Просматривать и понимать отчет об анализе

В этом разделе поможет выполнить отчет об анализе.

### <a name="query-categories"></a>Запрос категории

Выберите различные срезы левой круговой диаграммы для отображения только запросы, которые подпадают под эту категорию.

![Секторов диаграммы в отчет](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **Снижение запросы**: Запросы, которые более эффективной в А, чем в B.  
- **Ошибки**: Запросы, которые показывают ошибки в экземпляре B, но не в экземпляре а.  
- **Улучшенные запросы**: Запросы, которые выполняются лучше в экземпляре B, чем в экземпляре а.  
- **Неопределенное запросы**: Запросы, которые бы произошло изменение в неопределенном состоянии производительности.  
- **Же**: Запросы, в которых производительность неизменным на экземплярах A и B.

### <a name="individual-query-drill-down"></a>Индивидуальный запрос детализации

Вы можете выбрать ссылок шаблон запроса, чтобы увидеть более подробные сведения о конкретных запросов.

![Запрос детализации](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

Выберите конкретного запроса, чтобы открыть сравнение сводки для запроса.

![Сводка сравнения](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

Вы увидите экземпляры A и B, выполнили запрос. Также вы увидите шаблон запрос может выглядеть так. В таблице отображается запрос сведения, относящиеся к экземпляры A и B.

### <a name="error-queries"></a>Ошибки запросов

Сводный отчет сравнения имеет расширяемый **сведения об ошибке** и **данные плана запроса** разделы. В разделах показывают сообщения об ошибках и сведения о для обоих экземпляров плане.

Выберите сектор ошибки (красное) для отображения таких ошибок:
- **Существующие ошибки**: Ошибки, которые были в A.
- **Новые ошибки**: Ошибки, которые были в B.
- **Разрешить ошибки**: Ошибки, которые были в объект, но не в B.

![Ошибка диаграммы](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>Следующие шаги

- Чтобы узнать, как для создания отчета об анализе в командной строке, см. в разделе [выполните в командной строке](database-experimentation-assistant-run-command-prompt.md).

- 19-минутный введение Инициатив и демонстрации в следующем видео:

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
