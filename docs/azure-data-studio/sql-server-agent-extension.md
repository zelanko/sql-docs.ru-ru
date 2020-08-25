---
title: Расширение агента SQL Server
description: Узнайте, как установить и использовать расширение агента SQL Server (предварительная версия) для Azure Data Studio, которое предназначено для управления заданиями и конфигурациями агента SQL Server.
ms.custom: seodec18
ms.date: 09/24/2018
ms.reviewer: alayu, maghan, sstein
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: 207388fed1ea2465fb965457640b5e1fb0d162cf
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2020
ms.locfileid: "88766163"
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

Дополнительные сведения об агенте SQL Server см. в [нашей документации](../ssms/agent/sql-server-agent.md?view=sql-server-2017).