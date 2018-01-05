---
title: "Учебник: Включение таблицы места использования образца insight мини-приложения в Studio операций SQL (Предварительная версия) | Документы Microsoft"
description: "Этот учебник демонстрирует включение таблицы места использования образца insight мини-приложения на панель мониторинга базы данных SQL Studio операций (Предварительная версия)."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7c51c7d1804baa490e665d316a08d911038c9f11
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="tutorial-enable-the-table-space-usage-sample-insight-widget-using-includename-sosincludesname-sos-shortmd"></a>Учебник: Включите таблицу места использования примера insight мини-приложения с помощью[!INCLUDE[name-sos](../includes/name-sos-short.md)]

Этот учебник демонстрирует включение мини-приложение подробные сведения на панели мониторинга базы данных, представления в быстро об использовании места для всех таблиц в базе данных. С помощью этого учебника вы узнаете, как:

> [!div class="checklist"]
> * Быстро включите анализ мини-приложение с помощью пример мини-приложения для встроенной подробные сведения
> * Просмотр сведений о объем использования таблиц
> * Фильтрация данных и просматривать исходные метки в представление диаграммы

## <a name="prerequisites"></a>предварительные требования

Упражнений этого учебника требуется SQL Server или база данных SQL Azure *TutorialDB*. Для создания *TutorialDB* базы данных, выполните одно из следующих краткие руководства:

- [Подключения и запроса с помощью SQL Server[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключения и запроса с помощью базы данных SQL Azure[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="turn-on-a-management-insight-on-includename-sosincludesname-sos-shortmds-database-dashboard"></a>Включить анализ управления на [!INCLUDE[name-sos](../includes/name-sos-short.md)]в панель мониторинга базы данных
[!INCLUDE[name-sos](../includes/name-sos-short.md)]имеет встроенные образец мини-приложение для отслеживания пространства, используемый в таблицах в базе данных.

1. Откройте **параметры пользователя** , нажав клавишу **Ctrl + Shift + P** Открытие *палитры команд*, тип *параметры* в поле поиска и выберите  **Параметры: Откройте параметры пользователя**.

   ![Открытие пользовательских параметров команды](./media/tutorial-table-space-sql-server/open-user-settings.png)

2. Тип *мониторинга* поле ввода параметров поиска и найдите **dashboard.database.widgets**.

   ![Параметры поиска](./media/tutorial-table-space-sql-server/search-settings.png)

3. Чтобы настроить **dashboard.database.widgets** параметр, наведите указатель мыши на значок карандаша слева от **dashboard.database.widgets** текста, нажмите кнопку **изменить**  >  **Копировать параметры**.

4. С помощью [!INCLUDE[name-sos](../includes/name-sos-short.md)]настроить анализ параметров IntelliSense, *имя* заголовка мини-приложение *gridItemConfig* размера мини-приложение, и *мини-приложение* , выбрав **таблицы пространства db анализ** из раскрывающегося списка, как показано на следующем снимке экрана:

   ![Анализ параметров](./media/tutorial-table-space-sql-server/insight-table-space.png)

5. Нажмите клавишу **Ctrl + S** для сохранения настроек.

6. Панель мониторинга открыть базу данных, щелкнув правой кнопкой мыши **TutorialDB** и нажмите кнопку **управление**.

   ![Откройте панель мониторинга](./media/tutorial-table-space-sql-server/insight-open-dashboard.png)

7. Представление *пространства, используемый в таблицах* как показано на следующем снимке экрана: 

   ![Мини-приложения](./media/tutorial-table-space-sql-server/insight-table-space-result.png)


## <a name="working-with-the-insight-chart"></a>Работа с диаграммой подробные сведения

[!INCLUDE[name-sos](../includes/name-sos-short.md)]в представление диаграммы предоставляет сведения о фильтрации и наведения мыши. Чтобы повторить следующие действия:

1. Нажмите кнопку и включать или выключать *row_count* условных обозначений на диаграмме. [!INCLUDE[name-sos](../includes/name-sos-short.md)]Показать и скрыть ряд данных, как условных обозначений можно включить или выключить.
    
2. Наведите указатель мыши на диаграмме. [!INCLUDE[name-sos](../includes/name-sos-short.md)]Дополнительные сведения о подписи рядов данных и его значение, как показано на следующем снимке экрана.

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