---
title: Учебник. Создание настраиваемых аналитических сведений мини-приложения
titleSuffix: Azure Data Studio
description: Этот учебник демонстрирует создание настраиваемых аналитических сведений мини-приложения и добавить их к панели мониторинга базы данных и сервера в Azure Data Studio.
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: tutorial
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ab545d4d058780503778fb470bc5802ecae9d077
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157041"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Учебник. Создание настраиваемых аналитических сведений мини-приложения

Этот учебник демонстрирует использование собственных insight запросов для создания настраиваемых аналитических сведений мини-приложения.

С помощью этого учебника вы узнаете, как:
> [!div class="checklist"]
> * Запустить собственный запрос и просмотреть его в диаграмме
> * Создание настраиваемых аналитических сведений мини-приложение из диаграммы
> * Добавьте диаграмму на панели мониторинга сервера или базы данных
> * Добавление сведений о настраиваемых аналитических сведений мини-приложение

## <a name="prerequisites"></a>предварительные требования

В этом руководстве требуется SQL Server или базы данных SQL Azure *TutorialDB*. Чтобы создать *TutorialDB* базы данных, выполните одно из следующих кратких руководств:

- [Подключение и запрос SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и запрос базы данных SQL Azure с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Запустите новый запрос и просмотрите результаты в виде диаграммы
На этом шаге запустите сценарий sql для запроса текущих активных сеансов.

1. Чтобы открыть новый редактор, нажмите клавишу **Ctrl + N**. 

2. Изменить контекст подключения к **TutorialDB**.

3. Вставьте следующий запрос в редакторе запросов:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Сохранить запрос в редакторе, чтобы \*SQL-файл. Для этого руководства сохраните сценарий как *activeSession.sql*.

5. Чтобы выполнить запрос, нажмите клавишу **F5**.

6. После отображения результатов запроса, нажмите кнопку **представление в виде диаграммы**, затем нажмите кнопку **средства просмотра диаграмм** вкладки.

7. Изменение **тип диаграммы** для **число**. Эти параметры визуализации диаграммы count.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Добавление настраиваемых аналитических сведений на панель мониторинга базы данных

1. Чтобы открыть конфигурацию insight мини-приложение, нажмите кнопку **создать Insight** на *средства просмотра диаграмм*:

   ![настройка](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Скопируйте конфигурацию insight (данные JSON). 

3. Нажмите клавишу **Ctrl + запятая** открыть *параметры пользователя*.

4. Тип *панели мониторинга* в *параметры поиска*.

5. Нажмите кнопку **изменить** для *dashboard.database.widgets*.

   ![Параметры панели мониторинга](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Вставьте JSON-ФАЙЛ конфигурации insight в *dashboard.database.widgets*. Панель мониторинга базы данных параметров выглядит следующим образом:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql"
                }
            }
        }
    ]
   ```

7. Сохранить *параметры пользователя* и откройте файл *TutorialDB* мониторинга базы данных, чтобы просмотреть активные сеансы мини-приложения:

   ![Анализ activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Добавление сведений о настраиваемых аналитических сведений

1. Чтобы открыть новый редактор, нажмите клавишу **Ctrl + N**.

2. Изменить контекст подключения к **TutorialDB**.

3. Вставьте следующий запрос в редакторе запросов:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Сохранить запрос в редакторе, чтобы \*SQL-файл. Для этого руководства сохраните сценарий как *activeSessionDetail.sql*.

5. Нажмите клавишу **Ctrl + запятая** открыть *параметры пользователя*.

6. Изменения в существующий *dashboard.database.widgets* узла в файле параметров:

   ```json
    "dashboard.database.widgets": [
        {
            "name": "My-Widget",
            "gridItemConfig": {
                "sizex": 2,
                "sizey": 1
            },
            "widget": {
                "insights-widget": {
                    "type": {
                        "count": {
                            "dataDirection": "vertical",
                            "dataType": "number",
                            "legendPosition": "none",
                            "labelFirstColumn": false,
                            "columnsAsLabels": false
                        }
                    },
                    "queryFile": "{your file folder}/activeSession.sql",
                    "details": {
                        "queryFile": "{your file folder}/activeSessionDetail.sql",
                        "label": "SID",
                        "value": "Login Name"
                    }
                }
            }
        }
    ]
   ```

7. Сохранить *параметры пользователя* и откройте файл *TutorialDB* панель мониторинга базы данных. Нажмите кнопку с многоточием (...) рядом с полем *Мои мини-приложение* Отображение сведений:

    ![Анализ activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Следующие шаги
В этом руководстве вы узнали, как:
> [!div class="checklist"]
> * Запустить собственный запрос и просмотреть его в диаграмме
> * Создание настраиваемых аналитических сведений мини-приложение из диаграммы
> * Добавьте диаграмму на панели мониторинга сервера или базы данных
> * Добавление сведений о настраиваемых аналитических сведений мини-приложение

Чтобы узнать, как резервное копирование и восстановление баз данных, выполните следующему руководству:

> [!div class="nextstepaction"]
> [Резервное копирование и восстановление баз данных](tutorial-backup-restore-sql-server.md).
