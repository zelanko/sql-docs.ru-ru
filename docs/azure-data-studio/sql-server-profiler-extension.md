---
title: Расширение SQL Server Profiler
titleSuffix: Azure Data Studio
description: Установка и использование расширения "SQL Server Profiler" (предварительная версия) для Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 4fcb16d2ec3c267dc2927f22a029709a434416c9
ms.sourcegitcommit: 76fb3ecb79850a8ef2095310aaa61a89d6d93afd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776515"
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

Дополнительные сведения о Profiler и расширенных событиях см. в разделе [Расширенные события](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





