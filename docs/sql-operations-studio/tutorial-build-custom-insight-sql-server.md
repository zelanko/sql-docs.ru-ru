---
title: 'Учебник: Построение пользовательского представления мини-приложение в Studio операций SQL (Предварительная версия) | Документы Microsoft'
description: Демонстрирует построение пользовательского представления мини-приложения и добавить их к панели мониторинга сервера и базы данных в SQL Studio операций (Предварительная версия).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: tutorial
author: erickangMSFT
ms.author: erickang
manager: craigg
ms.openlocfilehash: fc57d6abd04a4672aad1026701489f15dfd69d66
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Учебник: Построение пользовательского представления мини-приложения

Этот учебник посвящен использовать анализ запросов для построения пользовательского представления мини-приложения.

С помощью этого учебника вы узнаете, как:
> [!div class="checklist"]
> * Выполнить собственный запрос и просмотреть его в диаграмме
> * Построение пользовательского представления мини-приложение из диаграммы
> * Добавьте диаграмму на панели мониторинга сервера или базы данных
> * Добавление сведений о пользовательских insight мини-приложения

## <a name="prerequisites"></a>предварительные требования

Упражнений этого учебника требуется SQL Server или база данных SQL Azure *TutorialDB*. Для создания *TutorialDB* базы данных, выполните одно из следующих краткие руководства:

- [Подключения и запроса с помощью SQL Server [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключения и запроса с помощью базы данных SQL Azure [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Запустите новый запрос и просмотрите результаты в виде диаграммы
На этом этапе выполните сценарий sql для запроса текущих активных сеансов.

1. Чтобы открыть новый редактор, нажмите клавишу **Ctrl + N**. 

2. Изменить контекст подключения к **TutorialDB**.

3. Вставьте следующий запрос в редакторе запросов:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Сохранить запрос в редакторе и \*SQL-файл. Для этого учебника сохраните сценарий как *activeSession.sql*.

5. Чтобы выполнить запрос, нажмите клавишу **F5**.

6. После отображения результатов запроса нажмите кнопку **представления в виде диаграммы**, нажмите кнопку **средства просмотра диаграмм** вкладки.

7. Изменение **тип диаграммы** для **число**. Эти параметры визуализации диаграммы count.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Добавьте пользовательские представления панели мониторинга баз данных

1. Чтобы открыть представление конфигурации мини-приложение, щелкните **создать анализ** на *средства просмотра диаграмм*:

   ![настройка](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Скопируйте конфигурацию insight (данные JSON). 

3. Нажмите клавишу **Ctrl + запятая** Открытие *параметры пользователя*.

4. Тип *мониторинга* в *параметры поиска*.

5. Нажмите кнопку **изменить** для *dashboard.database.widgets*.

   ![Параметры панели мониторинга](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Вставьте анализ конфигурации JSON в *dashboard.database.widgets*. Панель мониторинга базы данных параметры выглядит следующим образом:

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

## <a name="add-details-to-custom-insight"></a>Добавление сведений о пользовательских подробные сведения

1. Чтобы открыть новый редактор, нажмите клавишу **Ctrl + N**.

2. Изменить контекст подключения к **TutorialDB**.

3. Вставьте следующий запрос в редакторе запросов:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Сохранить запрос в редакторе и \*SQL-файл. Для этого учебника сохраните сценарий как *activeSessionDetail.sql*.

5. Нажмите клавишу **Ctrl + запятая** Открытие *параметры пользователя*.

6. Изменение существующих *dashboard.database.widgets* узла в файле параметров:

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

7. Сохранить *параметры пользователя* и откройте файл *TutorialDB* панель мониторинга базы данных. Нажмите кнопку с многоточием (...) рядом с *Мои Widget* чтобы Показать подробные сведения:

    ![Анализ activesession](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Следующие шаги
В этом учебнике вы узнали, как:
> [!div class="checklist"]
> * Выполнить собственный запрос и просмотреть его в диаграмме
> * Построение пользовательского представления мини-приложение из диаграммы
> * Добавьте диаграмму на панели мониторинга сервера или базы данных
> * Добавление сведений о пользовательских insight мини-приложения

Резервное копирование и восстановление баз данных, выполните следующее руководство:

> [!div class="nextstepaction"]
> [Резервное копирование и восстановление баз данных](tutorial-backup-restore-sql-server.md).