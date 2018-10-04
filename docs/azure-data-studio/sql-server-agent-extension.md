---
title: Расширение агента SQL Server Data Studio Azure | Документация Майкрософт
description: Расширение агента SQL Server (Предварительная версия) для Azure Data Studio
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: 5804aa146ddf79f6c3c4ccba48edd86d297c5c72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039202"
---
# <a name="sql-server-agent-extension-preview"></a>Расширение агента SQL Server (Предварительная версия)

Расширение агента SQL Server (Предварительная версия) — это расширение для управления и устранения неполадок задания агента SQL и конфигурации. Это расширение сейчас доступна Предварительная версия.

Следующие основные действия.
- Список заданий на агента SQL Server настроен на сервере SQL Server
- Просмотр журнала заданий с результатами выполнения задания
- Основные задания для запуска и остановки заданий

## <a name="install-the-sql-server-agent-extension"></a>Установите расширение агента SQL Server

1. Чтобы открыть диспетчер расширений и доступа доступных расширений, щелкните значок расширения или выберите **расширения** в **представление** меню.
2. Выберите доступное расширение, чтобы просмотреть подробные сведения.

   ![Установка агента](media/extensions/sql-server-agent-extension/install-sql-agent.png)

1. Выберите нужное расширение и **установить** его.
2. Выберите **перезагрузить** для включения расширения (только обязательно при первоначальной установке расширения).
1. Перейдите к панели мониторинга управления, щелкнув правой кнопкой мыши сервер или базу данных и выбрав **управление**.
2. Установленные расширения отображаются как вкладки на панели мониторинга управления:

   ![Представление агента](media/extensions/sql-server-agent-extension/view-sql-agent.png)

## <a name="view-jobs"></a>Просмотр заданий

При подключении к расширению агента SQL Server, первое, что вы см. в статье приведен список всех заданий агента.

   ![Просмотр заданий](media/extensions/sql-server-agent-extension/job-view.png)

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения об агенте SQL Server, [см. в нашей документации.](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent?view=sql-server-2017)


