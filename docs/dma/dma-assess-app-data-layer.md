---
title: Оценка уровня доступа к данным приложения с помощью Помощник по миграции данных
description: Узнайте, как использовать Помощник по миграции данных для оценки уровня доступа к данным приложения.
ms.date: 01/23/2020
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Assess
ms.assetid: ''
author: HJToland3
ms.author: rajpo
ms.custom: seo-lt-2019
ms.openlocfilehash: 24763f190172da637d19df7ce36553b7341bd894
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "76761988"
---
# <a name="assess-an-apps-data-access-layer-with-data-migration-assistant"></a>Оценка уровня доступа к данным приложения с помощью Помощник по миграции данных

Обычно приложения подключаются и сохраняют данные в базе данных. Уровень доступа к данным приложения обеспечивает упрощенный доступ к этим данным. Помощник по миграции данных (DMA) позволили пользователям оценивать свои базы данных и связанные объекты. Последняя версия DMA (v 5.0) предоставляет поддержку для анализа подключения к базе данных и внедренных SQL-запросов в коде приложения.

Рассмотрим следующий сегмент кода C#:

![Пример сегмента кода C#](../dma/media/dma-assess-app-data-layer/dma-sample-c-sharp-code-segment.png)

В этом случае можно увидеть, что приложение использует SQL-запрос для получения имени сотрудника.

![Пример сведений о сегменте кода C#](../dma/media/dma-assess-app-data-layer/dma-sample-c-sharp-code-detail.png)

Как владелец приложения, мне нужно иметь возможность определять различные базы данных, к которым может подключаться приложение, а также запросы, внедренные в уровень доступа к данным приложения. Кроме того, мне нужно указать все изменения, необходимые для модернизировать приложения в службы данных Azure.

## <a name="assess-an-app-with-data-access-migration-toolkit"></a>Оценка приложения с помощью набора средств миграции доступа к данным

Чтобы включить эту оценку, мы недавно предоставили набор средств переноса данных для доступа к данным (ДАМТ), расширение Visual Studio Code. Последняя версия этого расширения (v 0,2) добавляет поддержку для приложений .NET и диалект T-SQL.

1. Загрузите и установите VS Code [отсюда](https://code.visualstudio.com/download).
2. Включите [расширение "набор средств миграции доступа к данным](https://marketplace.visualstudio.com/items?itemName=ms-databasemigration.data-access-migration-toolkit) " из магазина "расширения".

   ![Страница расширения набора средств миграции доступа к данным](../dma/media/dma-assess-app-data-layer/dma-damt-extension-page.png)

3. Откройте проект приложения в Visual Studio Code.

   ![Проект приложения в Visual Studio Code](../dma/media/dma-assess-app-data-layer/dma-app-project-in-vscode.png)

4. Запустите консоль расширения (Ctrl-Шфт-P), а затем запустите команду **доступ к данным: анализ рабочей области** .

   ![Консоль расширения в Visual Studio Code](../dma/media/dma-assess-app-data-layer/dma-vscode-extension-console.png)

5. Выберите диалект SQL Server.

   ![Выбор диалекта SQL Server](../dma/media/dma-assess-app-data-layer/dma-sql-server-dialect.png)

   В конце анализа команда создает отчет о командах и запросах подключения SQL.

   ![Отчет о доступе к данным](../dma/media/dma-assess-app-data-layer/dma-data-access-report.png)

6. Изучите отчет о компонентах подключения к данным и запросах SQL, внедренных в код приложения, который выделяется.

   ![SQL запросы в коде приложения](../dma/media/dma-assess-app-data-layer/dma-sql-queries-in-app-code.png)

   Эти запросы можно проанализировать с помощью DMA для обеспечения совместимости и проблем с контролем четности компонентов на основе целевой платформы SQL.

7. Чтобы оценить уровень данных приложения, экспортируйте отчет как файл JSON.

   ![Экспорт файла. JSON](../dma/media/dma-assess-app-data-layer/dma-json-file-export.png)

   В этом случае созданный файл:

   ![Просмотр содержимого JSON файла](../dma/media/dma-assess-app-data-layer/dma-json-file-contents.png)

   Помощник по миграции данных позволяет оценивать запросы, определенные в приложении, в контексте модернизации базы данных на платформу данных Azure.

8. Запустите Помощник по миграции данных, а затем создайте проект оценки.

   ![Помощник по миграции данных новый проект оценки](../dma/media/dma-assess-app-data-layer/dma-new-assessment-project.png)

9. Выберите экземпляр SQL Server источника.

   ![Помощник по миграции данных выбор источника SQL Server](../dma/media/dma-assess-app-data-layer/dma-select-sql-source.png)

10. Выберите базу данных, к которой подключается приложение.

    ![Перенос доступа к данным выбор базы данных приложения](../dma/media/dma-assess-app-data-layer/dma-select-app-database.png)

    Для упрощения оценки доступа к данным в DMA введена возможность включения JSON файлов с запросами приложений. Далее мы будем включать JSON файл, созданный ранее с запросами приложений.

11. Выберите базу данных и перейдите к файлу JSON, экспортированному из набора средств миграции доступа к данным, чтобы включить запросы из приложения для оценки.

    ![Помощник по миграции данных открыть JSON файл ДМАТ](../dma/media/dma-assess-app-data-layer/dma-open-damt-json-file.png)

12. Запустите оценку.

    ![Помощник по миграции данных начать оценку](../dma/media/dma-assess-app-data-layer/dma-start-assessment.png)

13. Ознакомьтесь с отчетом об оценке. В созданном отчете будут содержаться все проблемы совместимости или четности компонентов, обнаруженные в запросах приложений, как показано ниже.

    ![Отчет об оценке Помощник по миграции данных](../dma/media/dma-assess-app-data-layer/dma-assessment-report.png)

Теперь в дополнение к переходу к базе данных для миграции пользователи также имеют представление с точки зрения приложения.

## <a name="see-also"></a>См. также

* [Общие сведения о Помощник по миграции данных](../dma/dma-overview.md)
* [Помощник по миграции данных: параметры конфигурации](../dma/dma-configurationsettings.md)
* [Помощник по миграции данных: рекомендации](../dma/dma-bestpractices.md)
* [Набор средств для переноса доступа к данным](https://marketplace.visualstudio.com/items?itemName=ms-databasemigration.data-access-migration-toolkit)