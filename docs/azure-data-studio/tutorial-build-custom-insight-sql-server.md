---
title: Руководство. Создание настраиваемого аналитического мини-приложения
titleSuffix: Azure Data Studio
description: В этом руководстве показано, как создавать настраиваемые аналитические мини-приложения и добавлять их на панели мониторинга баз данных и сервера в Azure Data Studio.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: tutorial
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 34ee9c23569897247f05d6b9b5f9f2610f5d68fc
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959091"
---
# <a name="tutorial-build-a-custom-insight-widget"></a>Руководство. Создание настраиваемого аналитического мини-приложения

В этом руководстве показано, как создавать настраиваемые аналитические мини-приложения с помощью собственных аналитических запросов.

В этом руководстве вы узнаете, как выполнять следующие задачи:
> [!div class="checklist"]
> * выполнение собственного запроса и его просмотр на диаграмме;
> * создание настраиваемого аналитического мини-приложения на основе диаграммы;
> * добавление диаграммы на панель мониторинга сервера или базы данных;
> * добавление сведений в настраиваемое аналитическое мини-приложение.

## <a name="prerequisites"></a>предварительные требования

Для работы с этим руководством требуется SQL Server или база данных SQL Azure *TutorialDB*. Чтобы создать базу данных *TutorialDB*, выполните инструкции, приведенные в одном из следующих кратких руководств:

- [Подключение и отправка запроса к SQL Server с помощью [!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-server.md)
- [Подключение и отправка запроса к базе данных SQL Azure с помощью[!INCLUDE[name-sos-short](../includes/name-sos-short.md)]](quickstart-sql-database.md)


## <a name="run-your-own-query-and-view-the-result-in-a-chart-view"></a>Выполнение собственного запроса и просмотр результата в представлении диаграммы
На этом этапе вы выполните скрипт SQL для запроса текущих активных сеансов.

1. Чтобы открыть новое окно редактора, нажмите клавиши **CTRL+N**. 

2. Измените контекст подключения на **TutorialDB**.

3. Вставьте следующий запрос в редактор запросов:

   ```sql
   SELECT count(session_id) as [Active Sessions]
   FROM sys.dm_exec_sessions
   WHERE status = 'running'
   ```

4. Сохраните запрос в редакторе в файле \*.sql. Для данного руководства сохраните скрипт в файле *activeSession.sql*.

5. Чтобы выполнить запрос, нажмите клавишу **F5**.

6. После того как отобразятся результаты запроса, щелкните **Показать как диаграмму**, а затем перейдите на вкладку **Средство просмотра диаграмм**.

7. Измените **тип диаграммы** на **счетчик**. В результате будет построена диаграмма подсчета.

## <a name="add-the-custom-insight-to-the-database-dashboard"></a>Добавление настраиваемого аналитического мини-приложения на панель мониторинга базы данных

1. Чтобы открыть конфигурацию аналитического мини-приложения, щелкните **Создать аналитику** на вкладке *Средство просмотра диаграмм*:

   ![настройка](./media/tutorial-build-custom-insight-sql-server/create-insight.png)
   
2. Скопируйте конфигурацию аналитики (данные JSON). 

3. Нажмите клавиши **CTRL+запятая**, чтобы открыть *параметры пользователя*.

4. В *параметрах поиска* введите *панель мониторинга*.

5. Щелкните **Изменить** для элемента *dashboard.database.widgets*.

   ![параметры панели мониторинга](./media/tutorial-build-custom-insight-sql-server/dashboard-settings.png)

6. Вставьте данные JSON конфигурации аналитики в *dashboard.database.widgets*. Параметры панели мониторинга базы данных имеют следующий вид:

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

7. Сохраните файл *настроек пользователя* и откройте панель мониторинга базы данных *TutorialDB*, чтобы увидеть мини-приложение активных сеансов:

   ![аналитика активных сеансов](./media/tutorial-build-custom-insight-sql-server/insight-activesession-dashboard.png)

## <a name="add-details-to-custom-insight"></a>Добавление сведений в настраиваемое аналитическое мини-приложение

1. Чтобы открыть новое окно редактора, нажмите клавиши **CTRL+N**.

2. Измените контекст подключения на **TutorialDB**.

3. Вставьте следующий запрос в редактор запросов:

   ```sql
    SELECT session_id AS [SID], login_time AS [Login Time], host_name AS [Host Name], program_name AS [Program Name], login_name AS [Login Name]
    FROM sys.dm_exec_sessions
    WHERE status = 'running'
   ```

4. Сохраните запрос в редакторе в файле \*.sql. Для данного руководства сохраните скрипт в файле *activeSessionDetail.sql*.

5. Нажмите клавиши **CTRL+запятая**, чтобы открыть *параметры пользователя*.

6. Измените раздел *dashboard.database.widgets* в файле параметров:

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

7. Сохраните файл *настроек пользователя* и откройте панель мониторинга базы данных *TutorialDB*. Нажмите кнопку с многоточием (...) рядом со свойством *My-Widget*, чтобы просмотреть сведения:

    ![аналитика активных сеансов](./media/tutorial-build-custom-insight-sql-server/insight-activesession-detail.png)

## <a name="next-steps"></a>Следующие шаги
В этом руководстве вы узнали, как выполнять следующие задачи:
> [!div class="checklist"]
> * выполнение собственного запроса и его просмотр на диаграмме;
> * создание настраиваемого аналитического мини-приложения на основе диаграммы;
> * добавление диаграммы на панель мониторинга сервера или базы данных;
> * добавление сведений в настраиваемое аналитическое мини-приложение.

Чтобы научиться выполнять резервное копирование и восстановление баз данных, пройдите следующее руководство:

> [!div class="nextstepaction"]
> [Резервное копирование и восстановление баз данных](tutorial-backup-restore-sql-server.md)
