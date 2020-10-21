---
title: Источник Power Query | Документация Майкрософт
description: Узнайте, как настроить источник Power Query в потоке данных SQL Server Integration Services (SSIS).
ms.date: 12/27/2019
ms.prod: sql
ms.prod_service: integration-services
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.designer.powerqueryconnmgr.f1
- sql13.ssis.designer.powerquerysource.queries.f1
- sql13.ssis.designer.powerquerysource.connmgrs.f1
- sql14.ssis.designer.powerqueryconnmgr.f1
- sql14.ssis.designer.powerquerysource.queries.f1
- sql14.ssis.designer.powerquerysource.connmgrs.f1
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: fc7f3e5ef6561338f6177f1810f6af2b92c7064a
ms.sourcegitcommit: cfa04a73b26312bf18d8f6296891679166e2754d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92192690"
---
# <a name="power-query-source-preview"></a>Источник Power Query (предварительная версия)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

В этой статье описывается настройка свойств источника Power Query в потоке данных SQL Server Integration Services (SSIS). Power Query — это технология, которая позволяет подключаться к различным источникам данных и преобразовывать данные с помощью Excel или Power BI Desktop. Дополнительные сведения см. в статье [Power Query — обзор и обучение](https://support.office.com/article/power-query-overview-and-learning-ed614c81-4b00-4291-bd3a-55d80767f81d). Чтобы настроить скрипт, сформированный Power Query, его можно скопировать и вставить в источник Power Query в потоке данных SSIS.
  
> [!NOTE]
> В текущем предварительном выпуске источник Power Query можно использовать только в SQL Server 2017 и 2019 и Azure-SSIS Integration Runtime (IR) в Фабрике данных Azure (ADF). Скачать и установить последнюю версию источника Power Query для SQL Server 2017 и 2019 можно [здесь](https://www.microsoft.com/download/details.aspx?id=100619). Источник Power Query для Azure-SSIS IR установлен предварительно. Чтобы подготовить Azure-SSIS IR, ознакомьтесь со статьей [Подготовка Integration Runtime Azure–SSIS в Фабрике данных Azure](/azure/data-factory/tutorial-deploy-ssis-packages-azure).

## <a name="configure-the-power-query-source"></a>Настройка источника Power Query

Чтобы открыть **редактор источников Power Query** в SSDT, перетащите **источник Power Query** c панели элементов SSIS в конструктор потоков данных и дважды щелкните его.  

![Источник PQ](media/power-query-source/pq-source.png)

Три вкладки показаны в левой части. На вкладке **Запросы** из раскрывающегося меню можно выбрать режим запроса.
-   Режим **Один запрос** позволяет скопировать и вставить один скрипт Power Query из Excel или Power BI Desktop.
-   Режим **Один запрос из переменной** позволяет указать переменную строки, которая содержит выполняемый запрос.

![Одна вкладка запросов источника PQ](media/power-query-source/pq-source-queries-tab-single.png)

На вкладке **Диспетчеры подключений** можно добавить или удалить диспетчеры подключений Power Query, которые содержат учетные данные для доступа к источнику данных. Если нажать кнопку **Detect Data Source** (Определить источник данных), определятся и перечислятся источники данных, указанные в запросе, чтобы назначить соответствующие имеющиеся диспетчеры подключений Power Query или создать их.

![Вкладка определения диспетчеров подключений источника PQ](media/power-query-source/pq-source-connection-managers-tab-detect.png)

![Вкладка добавления диспетчеров подключений источника PQ](media/power-query-source/pq-source-connection-managers-tab-add.png)

Наконец, на вкладке **Столбцы** можно изменить сведения о выходном столбце.

![Вкладка "Столбцы" источника PQ](media/power-query-source/pq-source-columns-tab.png)

## <a name="configure-the-power-query-connection-manager"></a>Настройка диспетчера подключений Power Query

При проектировании потока данных с помощью источника Power Query на SSDT вы можете создать диспетчер подключений Power Query следующими способами.
- Создайте его косвенно на вкладке **Диспетчеры подключений** в источнике Power Query, нажав кнопки **Добавить**/**Detect Data Source** (Определить источник данных) и выбрав **<New connection...>** из раскрывающегося меню, как описано выше.
- Создайте его напрямую, щелкнув правой кнопкой мыши панель пакета **Диспетчеры подключений** и выбрав **Создать подключение...** из раскрывающегося меню.

![Панель добавления диспетчеров подключений источника PQ](media/power-query-source/pq-source-connection-managers-panel-add.png)

В диалоговом окне **Добавление диспетчера соединений со службами SSIS** дважды щелкните **PowerQuery** в списке типов диспетчеров подключений.

![Диалоговое окно добавления на панели диспетчеров подключений источника PQ](media/power-query-source/pq-source-connection-managers-panel-add-dialog.png)

В **редакторе диспетчера подключений Power Query** необходимо указать **тип источника данных**, **путь к источнику данных** и **вид проверки подлинности**, а также назначить соответствующие учетные данные для доступа. Сейчас в раскрывающемся меню доступно 22 **типа источника данных**.

![Тип редактора диспетчера подключений источника PQ](media/power-query-source/pq-source-connection-manager-editor-kind.png)

Некоторые из этих источников (**Oracle**, **DB2**, **MySQL**, **PostgreSQL**, **Teradata**, **Sybase**) требуют дополнительных установок драйверов ADO.NET, которые можно получить из статьи [Требования к источнику данных (Power Query)](/power-bi/desktop-data-source-prerequisites). Вы можете использовать пользовательский интерфейс установки для их установки в Azure-SSIS IR (ознакомьтесь со статьей [Пользовательская установка для среды выполнения интеграции Azure–SSIS](/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup)).

Для параметра **Путь к источнику данных** вы можете ввести зависящие от источника данных свойства, формирующие строку подключения без сведений о проверке подлинности. Например, путь для источника данных **SQL** формируется как `<Server>;<Database>`. Вы можете нажать кнопку **Изменить**, чтобы назначить значения зависящим от источника данных свойствам, образующим путь.

![Путь редактора диспетчера подключений источника PQ](media/power-query-source/pq-source-connection-manager-editor-path.png)

Наконец, для параметра **Вид проверки подлинности** вы можете выбрать **Анонимный**/**Проверка подлинности Windows**/**Пароль для имени пользователя**/**Ключ** из раскрывающегося меню, ввести соответствующие учетные данные для доступа и нажать кнопку **Проверить подключение**, чтобы убедиться, что источник Power Query был правильно настроен.

![Проверка подлинности в редакторе диспетчера подключений источника PQ](media/power-query-source/pq-source-connection-manager-editor-authentication.png)

### <a name="current-limitations"></a>Текущие ограничения

-   В настоящее время источник данных **Oracle** нельзя использовать в среде Azure-SSIS IR, так как драйвер Oracle ADO.NET нельзя установить в ней. Вместо этого необходимо установить драйвер Oracle ODBC и использовать источник данных **ODBC** для подключения к Oracle (см. пример **ORACLE STANDARD ODBC** в статье [Пользовательская установка для среды выполнения интеграции Azure-SSIS](/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup)).

-   В Azure-SSIS IR в настоящее время нельзя использовать **веб**-источник данных с выборочной установкой. Используйте его без выборочной установки.

## <a name="next-steps"></a>Дальнейшие действия
Узнайте, как запускать пакеты SSIS в Azure-SSIS IR в качестве первоклассных действий в конвейерах ADF. Ознакомьтесь со статьей [Запуск пакета Integration Services с помощью действия "Выполнить пакет SSIS" в фабрике данных Azure](/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).