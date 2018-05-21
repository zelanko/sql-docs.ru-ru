---
title: 'Учебник: Включение таблицы места использования образца insight мини-приложения в Studio операций SQL (Предварительная версия) | Документы Microsoft'
description: Этот учебник демонстрирует включение таблицы места использования образца insight мини-приложения на панель мониторинга базы данных SQL Studio операций (Предварительная версия).
ms.custom: tools|sos
ms.date: 03/19/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3a09dd273bb005432eaf638bb88c55ff35a5bd90
ms.sourcegitcommit: 6fd8a193728abc0a00075f3e4766a7e2e2859139
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Учебник: Включите таблицу места использования примера insight мини-приложения с помощью [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Этот учебник демонстрирует включение мини-приложение подробные сведения на панели мониторинга базы данных, представления в быстро об использовании места для всех таблиц в базе данных. С помощью этого учебника вы узнаете, как:

> [!div class="checklist"]
> * Быстро включите анализ мини-приложение с помощью пример мини-приложения для встроенной подробные сведения
> * Просмотр сведений о объем использования таблиц
> * Фильтрация данных и просматривать исходные метки в представление диаграммы

## <a name="prerequisites"></a>предварительные требования

Упражнений этого учебника требуется SQL Server или база данных SQL Azure *TutorialDB*. Для создания *TutorialDB* базы данных, выполните одно из следующих краткие руководства:

- [Подключения и запроса с помощью SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключения и запроса с помощью базы данных SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Включить анализ управления на [!INCLUDE[name-sos](../includes/name-sos-short.md)]в панель мониторинга базы данных
[!INCLUDE[name-sos](../includes/name-sos-short.md)] имеет встроенные образец мини-приложение для отслеживания пространства, используемый в таблицах в базе данных.

1. Откройте *параметры пользователя* , нажав клавишу **Ctrl + Shift + P** Открытие *палитры команд*.
2. Тип *параметры* в поле поиска и выберите **предпочтения: открыть параметры пользователя**.
2. Тип *мониторинга* поле ввода параметров поиска и найдите **dashboard.database.widgets**.

3. Для настройки **dashboard.database.widgets** нужно изменить параметры **dashboard.database.widgets** запись в **параметры пользователя** раздела (в столбце Правая панель). При наличии не **dashboard.database.widgets** в **параметры пользователя** статьи, наведите указатель мыши на **dashboard.database.widgets** текст в столбце параметры по умолчанию и нажмите кнопку значок карандаша, который отображается слева от текста и нажмите кнопку **Копировать параметры**. Если указано всплывающего окна **заменить в параметрах**, не щелкая! Последовательно выберите пункты **параметры пользователя** столбец вправо и найдите **dashboard.database.widgets** раздел и переход к следующему шагу.

4. В **dashboard.database.widgets** статьи, добавьте следующий код:

   ```json
        {
            "name": "Space Used by Tables",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "table-space-db-insight": null
            }
        },
    ```
**Dashboard.database.widgets** раздел должен выглядеть как на следующем рисунке:

   ![Параметры поиска](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Нажмите клавишу **Ctrl + S** для сохранения настроек.

6. Панель мониторинга открыть базу данных, щелкнув правой кнопкой мыши **TutorialDB** и нажмите кнопку **управление**.

7. Представление *табличное пространство* анализ графического элемента, как показано на следующем рисунке: 

   ![Мини-приложения](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Работа с диаграммой подробные сведения

[!INCLUDE[name-sos](../includes/name-sos-short.md)]в представление диаграммы предоставляет сведения о фильтрации и наведения мыши. Чтобы повторить следующие действия:

1. Нажмите кнопку и включать или выключать *row_count* условных обозначений на диаграмме. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Показать и скрыть ряд данных, как условных обозначений можно включить или выключить.
    
2. Наведите указатель мыши на диаграмме. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Дополнительные сведения о подписи рядов данных и его значение, как показано на следующем снимке экрана.

   ![переключить диаграммы и условные обозначения](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Следующие шаги
В этом учебнике вы узнали, как:
> [!div class="checklist"]
> * Быстро включите анализ мини-приложение с образцом insight встроенных мини-приложения.
> * Просмотр сведений объем использования таблиц.
> * Фильтрация данных и просматривать исходные метки в представление диаграммы

Чтобы узнать, как можно создавать пользовательские представления мини-приложение, с этим учебником далее:

> [!div class="nextstepaction"]
> [Построение пользовательского представления мини-приложение](tutorial-build-custom-insight-sql-server.md).