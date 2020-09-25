---
title: Расширение SQL Server Profiler
description: Узнайте, как установить и использовать расширение SQL Server Profiler. Простое в использовании решение трассировки SQL Server, аналогичное Профилировщику SSMS.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c76e4cf15edcfeb6cb25b9d205f79ba34386e8d0
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123227"
---
# <a name="sql-server-profiler-extension-preview"></a>Расширение SQL Server Profiler (предварительная версия)

Расширение SQL Server Profiler (предварительная версия) предоставляет простое решение трассировки для SQL Server, аналогичное профилировщику SQL Server Management Studio (SSMS), но созданное на основе Расширенных событий. SQL Server Profiler очень прост в использовании и имеет хорошие значения по умолчанию для наиболее распространенных конфигураций трассировки. Интерфейс оптимизирован для просмотра событий и просмотра соответствующего текста Transact-SQL (T-SQL). В SQL Server Profiler для Azure Data Studio также предполагается наличие правильных значений по умолчанию для сбора действий по выполнению T-SQL с простым пользовательским интерфейсом. Сейчас это расширение находится в режиме предварительной версии.

**Распространенные сценарии использования профилировщика SQL:**

- пошаговое выполнение проблемных запросов для поиска источника проблемы;
- выявление и диагностика медленно работающих запросов;
- перехват серии инструкций Transact-SQL, ведущих к проблеме;
- контроль производительности SQL Server для настройки рабочих нагрузок;
- Анализ счетчиков производительности для диагностики проблем.

## <a name="install-the-sql-server-profiler-extension"></a>Установка расширения SQL Server Profiler

1. Чтобы открыть диспетчер расширений и получить доступ к имеющимся расширениям, щелкните значок расширений или выберите пункт **Расширения** в меню **Вид**.
2. Выберите доступное расширение и просмотрите сведения о нем.

    ![Диспетчер расширений Profiler](media/sql-server-profiler-extension/profiler-extension.png)

3. Выберите нужное расширение и **установите** его.
4. Выберите **Перезагрузить**, чтобы включить расширение (требуется только при первой установке расширения).

## <a name="start-profiler"></a>Запуск Profiler

1. Чтобы запустить Profiler, сначала установите подключение к серверу на вкладке "Серверы".
2. После создания подключения нажмите **ALT+P**, чтобы открыть Profiler.
3. Чтобы запустить Profiler, нажмите **ALT+S**. Теперь можно начать просмотр расширенных событий.

    ![Просмотр Profiler](media/sql-server-profiler-extension/view-profiler.png)

4. Чтобы остановить Profiler, нажмите **ALT+S**. Это сочетание клавиш является переключателем.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о Profiler и расширенных событиях см. в разделе [Расширенные события](../../relational-databases/extended-events/extended-events.md).