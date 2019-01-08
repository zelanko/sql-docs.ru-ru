---
title: Расширение SQL Server Profiler
titleSuffix: Azure Data Studio
description: Установка и использование расширения SQL Server Profiler (Предварительная версия) для Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: b883883cbe201de32020e86ca2cd38746caf46be
ms.sourcegitcommit: 189a28785075cd7018c98e9625c69225a7ae0777
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/07/2018
ms.locfileid: "53030618"
---
# <a name="sql-server-profiler-extension-preview"></a>Расширение SQL Server Profiler (Предварительная версия)

Расширение SQL Server Profiler (Предварительная версия) обеспечивает простое аналогичную Profiler SQL Server Management Studio (SSMS) за исключением SQL Server решение трассировки, созданные с помощью события Xevent. SQL Server Profiler очень прост в использовании и хорошо значениями по умолчанию для распространенных конфигураций, трассировку. UX оптимизирован для просмотра событий и просмотра связанный текст Transact-SQL (T-SQL). SQL Server Profiler для Azure Data Studio также предполагается, что значения хороший по умолчанию для сбора действий выполнения T-SQL с помощью простой в использовании пользовательский интерфейс. Это расширение сейчас доступна Предварительная версия.

**Стандартные способы SQL Profiler-использования:**

- пошаговое выполнение проблемных запросов для поиска источника проблемы;
- выявление и диагностика медленно работающих запросов;
- Перехват серии инструкций Transact-SQL, ведущих к проблеме.
- Мониторинг производительности SQL Server для настройки рабочих нагрузок.
- Анализ счетчиков производительности для диагностики проблем.


## <a name="install-the-sql-server-profiler-extension"></a>Установка расширения SQL Server Profiler

1. Чтобы открыть диспетчер расширений и доступа доступных расширений, щелкните значок расширения или выберите **расширения** в **представление** меню.
2. Выберите доступное расширение и просмотреть соответствующие данные.

   ![Диспетчер расширений профилировщика](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. Выберите нужное расширение и **установить** его.
2. Выберите **перезагрузить** для включения расширения (только обязательно при первоначальной установке расширения).

## <a name="start-profiler"></a>Запуск Profiler

1. Чтобы запустить Profiler, сначала подключение к серверу на вкладке "серверы".
2. После подключения, введите **Alt + P** для запуска Profiler.
3. Чтобы запустить Profiler, введите **Alt + s.** Вы можете теперь сразу расширенных событий.
    ![Диспетчер расширений профилировщика](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Чтобы остановить Profiler, введите **Alt + s.** Это сочетание клавиш является переключателем.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о Profiler и расширенных событий, см. в разделе [расширенных событий](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events).





