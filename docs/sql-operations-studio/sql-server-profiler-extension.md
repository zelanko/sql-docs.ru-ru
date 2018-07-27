---
title: SQL Operations Studio (Предварительная версия) расширения SQL Server Profiler | Документация Майкрософт
description: Расширение SQL Server Profiler для SQL Operations Studio (Предварительная версия)
ms.custom: tools|sos
ms.date: 07/19/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 190d54a4525a476b2c42c22d447264a1d95e7bc4
ms.sourcegitcommit: 4b21840f20195d70f255465666f7b409ba839d18
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/19/2018
ms.locfileid: "39147039"
---
# <a name="sql-server-profiler-extension"></a>Расширение SQL Server Profiler

Profiler SQL Server, которые расширение предоставляет простое решение SQL Server трассировки аналогичную Profiler SQL Server Management Studio (SSMS) за исключением построен с помощью события Xevent. SQL Server Profiler очень прост в использовании и хорошо значениями по умолчанию для распространенных конфигураций, трассировку. UX оптимизирован для просмотра событий и просмотра связанный текст Transact-SQL (T-SQL). SQL Server Profiler для SQL Operations Studio также предполагается, что значения хороший по умолчанию для сбора действий выполнения T-SQL с помощью простой в использовании пользовательский интерфейс.

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





