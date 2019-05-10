---
title: Учебник. Включение таблицы места использования образца insight мини-приложения
titleSuffix: Azure Data Studio
description: Этот учебник демонстрирует включение таблицы места использования образца insight мини-приложения на панели мониторинга базы данных Azure Data Studio.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 6594aea6a618e2b9c4bd28368462f85c94a5ff0a
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089669"
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Учебник. Включение таблицы места использования примера insight мини-приложения с помощью [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Этот учебник демонстрирует включение мини-приложение представление на панели мониторинга базы данных, предоставляя в краткие представления об использовании пространства для всех таблиц в базе данных. С помощью этого учебника вы узнаете, как:

> [!div class="checklist"]
> * Быстро включите мини-приложение insight, с помощью примера встроенных insight мини-приложения
> * Просмотр сведений о таблице использование пространства
> * Фильтрация данных и просматривать исходные метки на диаграмме insight

## <a name="prerequisites"></a>предварительные требования

В этом руководстве требуется SQL Server или базы данных SQL Azure *TutorialDB*. Чтобы создать *TutorialDB* базы данных, выполните одно из следующих кратких руководств:

- [Подключение и запрос SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и запрос базы данных SQL Azure с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Включить анализ управления на [!INCLUDE[name-sos](../includes/name-sos-short.md)]на панель мониторинга базы данных
[!INCLUDE[name-sos](../includes/name-sos-short.md)] имеет встроенный пример мини-приложение для мониторинга места, используемого таблицами в базе данных.

1. Откройте *параметры пользователя* , нажав клавишу **Ctrl + Shift + P** открыть *палитру команд*.
2. Тип *параметры* в поле поиска и выберите **предпочтения: Откройте параметры пользователя**.
2. Тип *панели мониторинга* поле ввода параметров поиска и найдите **dashboard.database.widgets**.

3. Для настройки **dashboard.database.widgets** необходимо изменить параметры **dashboard.database.widgets** запись в **параметры пользователя** раздела (в столбце Правая сторона). Если не **dashboard.database.widgets** в **параметры пользователя** разделе, наведите указатель мыши **dashboard.database.widgets** текст в столбце параметры по умолчанию и нажмите кнопку значок карандаша, который отображается слева от текста и нажмите кнопку **копирования к параметрам**. Если указано всплывающем **замените в параметрах**, не щелкая его! Перейдите к **параметры пользователя** столбец вправо и найдите **dashboard.database.widgets** раздел и перейдите к следующему шагу.

4. В **dashboard.database.widgets** разделе, добавьте следующий код:

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

6. Панель мониторинга открытую базу данных, щелкните правой кнопкой мыши **TutorialDB** и нажмите кнопку **управление**.

7. Представление *табличное пространство* insight графического элемента, как показано на следующем рисунке: 

   ![Мини-приложения](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Работа с диаграммой insight

[!INCLUDE[name-sos](../includes/name-sos-short.md)]в представление диаграммы предоставляет сведения о фильтрации и при наведении мыши. Чтобы опробовать следующее:

1. Нажмите кнопку и переключите *row_count* условные обозначения диаграммы. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Показать и скрыть ряд данных, как условные обозначения можно включать и выключать.
    
2. Наведите указатель мыши на диаграмме. [!INCLUDE[name-sos](../includes/name-sos-short.md)] Дополнительные сведения о подписи рядов данных и его значение, как показано на следующем снимке экрана.

   ![переключатель диаграммы и условные обозначения](./media/tutorial-table-space-sql-server/insight-table-space-toggle.png)


## <a name="next-steps"></a>Следующие шаги
В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Быстро включите мини-приложение анализ, используя в качестве образца встроенные insight мини-приложения.
> * Просмотрите сведения о таблице место, занятое.
> * Фильтрация данных и просматривать исходные метки на диаграмме insight

Чтобы сведения о создании настраиваемых аналитических сведений мини-приложение, выполните следующему руководству:

> [!div class="nextstepaction"]
> [Создание настраиваемых аналитических сведений мини-приложение](tutorial-build-custom-insight-sql-server.md).
