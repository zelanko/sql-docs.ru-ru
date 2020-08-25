---
title: Расширение SQL Server Profiler
description: Узнайте, как установить и использовать простое расширение SQL Server Profiler (предварительная версия) для трассировки, аналогичное Профилировщику SSMS.
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e3ab5a83f8ea4a8715101debdbdf5d292761d7b6
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88765783"
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

   ![Диспетчер расширений Profiler](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Выберите нужное расширение и **установите** его.
2. Выберите **Перезагрузить**, чтобы включить расширение (требуется только при первой установке расширения).

## <a name="start-profiler"></a>Запуск Profiler

1. Чтобы запустить Profiler, сначала установите подключение к серверу на вкладке "Серверы".
2. После создания подключения нажмите **ALT+P**, чтобы открыть Profiler.
3. Чтобы запустить Profiler, нажмите **ALT+S**. Теперь можно начать просмотр расширенных событий.
    ![Диспетчер расширений Profiler](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Чтобы остановить Profiler, нажмите **ALT+S**. Это сочетание клавиш является переключателем.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о Profiler и расширенных событиях см. в разделе [Расширенные события](../relational-databases/extended-events/extended-events.md).