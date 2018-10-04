---
title: 'Руководство: Включение пять медленных запросов пример мини-приложение - Studio данных Azure | Документация Майкрософт'
description: Этот учебник демонстрирует включение пять самые медленные запросы пример мини-приложения на панели мониторинга базы данных.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 839f72a83d45f49004f0bbfb876baadbeaafdeea
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039130"
---
# <a name="tutorial-add-the-five-slowest-queries-sample-widget-to-the-database-dashboard"></a>Учебник: Добавление *пять медленных запросов* пример мини-приложения на панель мониторинга базы данных

Этот учебник демонстрирует процесс добавления одной из [!INCLUDE[name-sos](../includes/name-sos-short.md)]на встроенный пример мини-приложения для *панель мониторинга базы данных* позволяет быстро просматривать пять медленных запросов базы данных. Вы также узнаете, как для просмотра сведений о медленных запросов и планов запросов с использованием [!INCLUDE[name-sos](../includes/name-sos-short.md)]в функции. С помощью этого учебника вы узнаете, как:

> [!div class="checklist"]
> * Включить Store запросов в базе данных
> * Добавление мини-приложение, предварительно созданные insight на панель мониторинга базы данных
> * Просмотр сведений о медленных запросов базы данных
> * Просмотр планов выполнения запросов для медленных запросов

[!INCLUDE[name-sos](../includes/name-sos-short.md)] включает в себя несколько insight мини-приложения out-of--box. Этот учебник демонстрирует добавление *-data-store-db анализ запросов* мини-приложения, но шаги по существу одинаковы для добавления любого мини-приложения.

## <a name="prerequisites"></a>предварительные требования

В этом руководстве требуется SQL Server или базы данных SQL Azure *TutorialDB*. Чтобы создать *TutorialDB* базы данных, выполните одно из следующих кратких руководств:

- [Подключение и запрос SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и запрос базы данных SQL Azure с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)



## <a name="turn-on-query-store-for-your-database"></a>Включить Store запросов для базы данных

Мини-приложение в этом примере требуется *Query Store* требуется включить.

1. Щелкните правой кнопкой мыши **TutorialDB** базы данных (в **СЕРВЕРЫ** боковой панели) и выберите **новый запрос**.
2. Вставьте следующую инструкцию Transact-SQL (T-SQL) в редакторе запросов, а затем нажмите кнопку **запуска**:

   ```sql
    ALTER DATABASE TutorialDB SET QUERY_STORE = ON
   ```

## <a name="add-the-slow-queries-widget-to-your-database-dashboard"></a>Добавить мини-приложение Медленные запросы на панель мониторинга базы данных

Для добавления *медленно мини-приложение запросов* к панели мониторинга, изменение *dashboard.database.widgets* в вашей *параметры пользователя* файл.

1. Откройте *параметры пользователя* , нажав клавишу **Ctrl + Shift + P** открыть *палитру команд*.
2. Тип *параметры* в поле поиска и выберите **предпочтения: открыть параметры пользователя**.

   ![Открытые пользовательские параметры команды](./media/tutorial-qds-sql-server/open-user-settings.png)

2. Тип *панели мониторинга* в поиске параметров поле и найдите **dashboard.database.widgets**.

   ![Параметры поиска](./media/tutorial-qds-sql-server/search-settings.png)

3. Для настройки **dashboard.database.widgets** необходимо изменить параметры **dashboard.database.widgets** запись в **параметры пользователя** раздела (в столбце Правая сторона). Если не **dashboard.database.widgets** в **параметры пользователя** разделе, наведите указатель мыши **dashboard.database.widgets** текст в столбце параметры по умолчанию и нажмите кнопку значок карандаша, который отображается слева от текста и нажмите кнопку **копирования к параметрам**. Если указано всплывающем **замените в параметрах**, не щелкая его! Перейдите к **параметры пользователя** столбец вправо и найдите **dashboard.database.widgets** раздел и перейдите к следующему шагу.

4. В **dashboard.database.widgets** разделе, добавьте следующий код:

   ```json
        {
            "name": "slow queries widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "query-data-store-db-insight": null
            }
        },
    ```

1. Если это добавляется новое мини-приложение в первый раз **dashboard.database.widgets** раздел должен выглядеть примерно следующим образом:

   ```json
   "dashboard.database.widgets": [
       {
           "name": "slow queries widget",
           "gridItemConfig": {
               "sizex": 2,
               "sizey": 1
           },
           "widget": {
               "query-data-store-db-insight": null
           }
       },
       {
           "name": "Tasks",
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 1
           },
           "widget": {
               "tasks-widget": {}
           }
       },
       {
           "gridItemConfig": {
               "sizex": 1,
               "sizey": 2
           },
           "widget": {
               "explorer-widget": {}
           }
       }
   ]
   ```

1. Нажмите клавишу **Ctrl + S** сохранить измененный **параметры пользователя**.

6. Откройте *панель мониторинга базы данных* , перейдя по адресу **TutorialDB** в **СЕРВЕРЫ** боковой панели, щелкните правой кнопкой мыши и выберите **управление**.

   ![Открытие панели мониторинга](./media/tutorial-qds-sql-server/insight-open-dashboard.png)

7. Анализ мини-приложения отображается в панели мониторинга: 

   ![QDS мини-приложения](./media/tutorial-qds-sql-server/insight-qds-result.png)


## <a name="view-insight-details-for-more-information"></a>Просмотр сведений о insight Дополнительные сведения

1. Чтобы просмотреть дополнительные сведения о мини-приложение insight, нажмите кнопку с многоточием (**...** ) в правом верхнем углу и выберите **Показать подробности**.
2. Чтобы отобразить дополнительные сведения для элемента, выберите любой элемент в **данные диаграммы** списка.

   ![Диалоговое окно детализации Insight](./media/tutorial-qds-sql-server/insight-details-dialog.png)

3. Щелкните правой кнопкой мыши ячейку справа от **query_sql_txt** в **сведений об элементе** и нажмите кнопку **Копировать ячейку**.

4. Закрыть **Insights** области.

## <a name="view-the-query-plan"></a>Просмотреть план запроса 

1. Откройте новый редактор запросов, нажав клавишу **Ctrl + N**.

2. Вставьте текст запроса из предыдущих шагов в редакторе.

3. Нажмите кнопку **объяснить**.

   ![Объяснить Insight QDS](./media/tutorial-qds-sql-server/insight-qds-explain.png)

4. Просмотрите план выполнения запроса:

   ![showplan](./media/tutorial-qds-sql-server/showplan.png)

## <a name="save-and-open-a-query-plan"></a>Сохранение и открытие план запроса 

1. Откройте диалоговое окно детализации insight.
2. Выберите один из элементов запроса.
2. Щелкните правой кнопкой мыши **query_plan** значение и выберите **Копировать ячейку**

   ![План Insights QDS](./media/tutorial-qds-sql-server/insight-qds-plan.png)

3. Нажмите клавишу **Ctrl + N** открыть новый редактор.

4. Вставьте скопированный план в редакторе.

5. Нажмите клавишу **Ctrl + S** сохраните файл и измените расширение файла для *.sqlplan*. *.sqlplan* не отображается в раскрывающемся списке расширение файла, поэтому просто введите его в. Для этого учебника назовите файл *slowquery.sqlplan*.

6. План запроса открывается в [!INCLUDE[name-sos](../includes/name-sos-short.md)]в средство просмотра плана запроса:

   ![План Insights QDS](./media/tutorial-qds-sql-server/sqlplan.png)


## <a name="next-steps"></a>Следующие шаги
В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Включить Store запросов в базе данных
> * Добавление мини-приложение информацию на панель мониторинга базы данных
> * Просмотр сведений о медленных запросов базы данных
> * Просмотр планов выполнения запросов для медленных запросов


Чтобы узнать, как включить **использование табличного пространства** пример аналитических сведений, работы с руководством далее:

> [!div class="nextstepaction"]
> [Включить мини-приложение insight образец таблицы пространства](tutorial-table-space-sql-server.md)
