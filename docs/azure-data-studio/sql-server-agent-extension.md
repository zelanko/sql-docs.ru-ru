---
title: Расширение агента SQL Server
titleSuffix: Azure Data Studio
description: Установка и использование расширения агента SQL Server (предварительная версия) для Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 05356cc815fdba22d55ee339d60994f2c9423373
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67959180"
---
# <a name="sql-server-agent-extension-preview"></a>Расширение агента SQL Server (предварительная версия)

Расширение агента SQL Server (предварительная версия) — это расширение для управления заданиями и конфигурациями агента SQL Server и устранения связанных с ними неполадок. Сейчас это расширение находится в режиме предварительной версии.

Ниже указаны основные действия, выполняемые с помощью расширения.
- Вывод списка заданий агента SQL Server, настроенных в SQL Server
- Просмотр журнала заданий с результатами выполнения заданий
- Базовое управление заданиями для запуска и остановки заданий

## <a name="install-the-sql-server-agent-extension"></a>Установка расширения агента SQL Server

1. Чтобы открыть диспетчер расширений и получить доступ к имеющимся расширениям, щелкните значок расширений или выберите пункт **Расширения** в меню **Вид**.
2. Выберите доступное расширение и просмотрите сведения о нем.

   ![Установка агента](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Выберите нужное расширение и **установите** его.
2. Выберите **Перезагрузить**, чтобы включить расширение (требуется только при первой установке расширения).
1. Перейдите на панель мониторинга управления, щелкнув сервер или базу данных правой кнопкой мыши и выбрав пункт **Управление**.
2. Установленные расширения отображаются в виде вкладок на панели мониторинга управления:

   ![Просмотр агента](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Просмотр заданий

При подключении к расширению агента SQL Server первое, что вы увидите, — это список всех заданий агента.

   ![Просмотр заданий](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об агенте SQL Server см. в [нашей документации](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017).


