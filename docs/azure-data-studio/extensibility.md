---
title: Добавляет дополнительные функции по расширяемости
titleSuffix: Azure Data Studio
description: Дополнительные сведения о модели расширяемости и областях ключа расширяемости для расширения функциональных возможностей студии данных Azure
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b595a353859ed7d69ccb6ad61ef6e5dc2a7073f3
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63238966"
---
# <a name="getting-started-with-includename-sosincludesname-sos-shortmd-extensibility"></a>Приступая к работе с [!INCLUDE[name-sos](../includes/name-sos-short.md)] расширяемости

[!INCLUDE[name-sos](../includes/name-sos.md)] есть несколько механизмов расширения для настройки пользовательского интерфейса и сделать эти настройки доступными сообществу пользователей всего. Ядро [!INCLUDE[name-sos](../includes/name-sos.md)] платформы построен на основе Visual Studio Code, поэтому большинство интерфейсов API расширяемости Visual Studio Code доступно. Кроме того мы предоставляем дополнительные возможности расширения для действий управления данных.

Ниже приведены некоторые из ключевых точек расширения.

- API расширяемости Visual Studio Code
- Расширение Azure Data Studio, средства разработки
- Управление публикации панели вкладок панели мониторинга
- Insights с функциями и действия
- Azure Data Studio расширяемости API-интерфейсов
- Интерфейсы API поставщика пользовательских данных

## <a name="visual-studio-code-extensibility-apis"></a>API расширяемости Visual Studio Code

Так как ядро [!INCLUDE[name-sos](../includes/name-sos.md)] платформы построен на основе Visual Studio Code, находятся сведения об API расширяемости Visual Studio Code [создания расширений](https://code.visualstudio.com/docs/extensions/overview) и [расширения API](https://code.visualstudio.com/docs/extensionAPI/overview) Документация по веб-сайта Visual Studio Code.

## <a name="manage-dashboard-tab-panel-contributions"></a>Управление публикации панели вкладок панели мониторинга

Дополнительные сведения см. в разделе [вклада точек](#contribution-points) и [переменные контекста](#context-variables).

## <a name="azure-data-studio-extensibility-apis"></a>Azure Data Studio расширяемости API-интерфейсов

Дополнительные сведения см. в разделе [API расширяемости](extensibility-apis.md).


## <a name="contribution-points"></a>Точки вклада

В этом разделе рассматриваются различные точки публикации, которые определены в манифесте расширения package.json.

Технология IntelliSense поддерживается внутри azuredatastudio.

## <a name="contributes-dashboard"></a>Предоставляет панели мониторинга

Contribute вкладку, контейнер, анализ мини-приложения на панель мониторинга.

![Панель мониторинга](media/extensibility/dashboard-page.png)

`dashboard.tabs`

Dashboard.Tabs создает разделы вкладку в панели мониторинга. Ожидается, что объект или массив объектов.  

```json
"dashboard.tabs": [
{
    "id": "test-tab1",
    "title": "Test 1",
    "description": "The test 1 displays a list of widgets.",
    "when": "connectionProvider == 'MSSQL' && !mssql:iscloud",
    "alwaysShow": true,
    "container": {
        ...
    }
}
]
```

`dashboard.containers`

Вместо указания встроенного контейнера панели мониторинга (внутри dashboard.tab). Вы можете зарегистрировать контейнеров с помощью dashboard.containers. Он принимает объект или массив объекта.

```json
"dashboard.containers": [
{
    "id": "innerTab1",
    "container": {
        ...
    }
},
{
    "id": "innerTab2",
    "container": {
       ...
    }
}
]
```

Для ссылки на зарегистрированный контейнер, укажите идентификатор контейнера

```json
"dashboard.tabs": [
{
    ...
    "container": {
        "innerTab1": {             
        }
    }
}
]

```

`dashboard.insights`

Вы можете зарегистрировать аналитические данные, используя dashboard.insights. Это похоже на [руководства: Создание настраиваемых аналитических сведений мини-приложения](https://docs.microsoft.com/sql/sql-operations-studio/tutorial-build-custom-insight-sql-server)

```json
"dashboard.insights": {
"id": "my-widget"
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
```


### <a name="dashboard-container-types"></a>Типы контейнеров панели мониторинга

В настоящее время существует четыре типа поддерживаемых контейнера:

1. `widgets-container`

    ![Мини-приложения контейнера](media/extensibility/widgets-container.png)

    Список мини-приложений, которые будут отображаться в контейнере. Это потоковый макет. Он принимает список мини-приложений.

    ```json
    "container": {
        "widgets-container": [
        {
            "widget": {
                "query-data-store-db-insight": {
                }
            }
        },
        {
            "widget": {
                "explorer-widget": {
                }
            }
        }
      ]
    }
    ```

2. `webview-container`

    ![контейнер веб-представления](media/extensibility/webview-container.png)

    Веб-представления будут отображаться в весь контейнер. Ожидается, что идентификатор веб-представления, следует убедиться, что то же самое идентификатор вкладки

    ```json
    "container": {
        "webview-container": null
    }
    ```

3. `grid-container`

   ![контейнер сетки](media/extensibility/grid-container.png)

   Список мини-приложения или любимую, которое будет отображаться в сетке размещения

    ```json
    "container": {
        "grid-container": [
        {
            "name": "widget 1",
            "widget": {
                "explorer-widget": {
                }
            },
            "row":0,
            "col":0
        },
        {
            "name": "widget 2",
            "widget": {
                "tasks-widget": {
                    "backup", 
                    "restore",
                    "configureDashboard",
                    "newQuery"
                }
            },
            "row":0,
            "col":1
        },
        {
            "name": "Webview 1",
            "webview": {
                "id": "google"
            },
            "row":1,
            "col":0,
            "colspan":2
        },
        {
            "name": "widget 3",
            "widget": {
                "explorer-widget": {}
            },
            "row":0,
            "col":3,
            "rowspan":2
        },
    ]
    ```

4.  `nav-section`

    ![разделу](media/extensibility/nav-section.png)

    В разделе навигации отображается в контейнере

    ```json
    "container": {
        "nav-section": [
            {
                "id": "innerTab1",
                "title": "inner-tab1",
                "icon": {
                    "light": "./icons/tab1Icon.svg",
                    "dark": "./icons/tab1Icon_dark.svg"
                }
                "container": {
                    ...
                }
            },
            {
                "id": "innerTab2",
                "title": "inner-tab2",
                "icon": {
                    "light": "./icons/tab2Icon.svg",
                    "dark": "./icons/tab2Icon_dark.svg"
                }
                "container": {
                    ...
                }
            }
        ]
    }
    ```



## <a name="context-variables"></a>Переменные контекста

Общие сведения о контексте, в Visual Studio Code и впоследствии Studio данных Azure см. в разделе [расширяемости](https://code.visualstudio.com/docs/extensionAPI/extension-points#_example).

В студии данных Azure у нас есть определенном контексте вокруг подключения базы данных, доступные для расширений.

### <a name="dashboard"></a>Панель мониторинга

На панели мониторинга мы предоставляем приведенные ниже переменные контекста:

|переменная контекста| description|
|:---|:---|
|`connectionProvider` | Строка, содержащая идентификатор для поставщика текущего соединения. Например: `connectionProvider == 'MSSQL'`.|
|`serverName`|Строка, содержащая имя сервера для текущего соединения. Например: `serverName == 'localhost'`.|
|`databaseName` | Строка, содержащая имя базы данных текущего соединения. Например: `databaseName == 'master'`.|
|`connection` | Объект подключения полностью профиля для текущего соединения (IConnectionProfile)|
|`dashboardContext` | Строка контекста страницы панели мониторинга включен в данный момент. «Базы данных» или «сервер». Например: `dashboardContext == 'database'`|
