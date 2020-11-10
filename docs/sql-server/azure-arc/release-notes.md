---
title: SQL Server с поддержкой Azure Arc — заметки о выпуске
description: Последние заметки о выпуске
author: anosov1960
ms.author: sashan
ms.reviewer: mikeray
ms.date: 10/29/2020
ms.topic: conceptual
ms.prod: sql
ms.openlocfilehash: 3dcbc6b17d5abe87aabe923d70746d65595b9de6
ms.sourcegitcommit: dc3ea1696b8a4332934568439aed6cce4e9737eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/03/2020
ms.locfileid: "93244656"
---
# <a name="release-notes---azure-arc-enabled-sql-server-preview"></a>Заметки о выпуске — SQL Server с поддержкой Azure Arc (предварительная версия)

> [!NOTE]
> В отношении технологии (как предварительной версии функции), описанной в этой статье, действуют [дополнительные условия использования предварительных версий Microsoft Azure](https://azure.microsoft.com/support/legal/preview-supplemental-terms/).

## <a name="september-2020"></a>Сентябрь 2020 г.

SQL Server с поддержкой Azure Arc выпущен как общедоступная предварительная версия. SQL Server с поддержкой Azure Arc распространяет службы Azure на экземпляры SQL Server, размещенные за пределами Azure в центре обработки данных клиента, в пограничной зоне или в среде с несколькими облаками.

Дополнительные сведения см. в [Обзор SQL Server с поддержкой Azure Arc](overview.md).

### <a name="known-issues"></a>Известные проблемы

В отношении сентябрьского выпуска действуют следующие ограничения.

* Колонка **Регистрация SQL Server с поддержкой Azure Arc** не поддерживает настройку пользовательских тегов. Чтобы добавить пользовательские теги, откройте ресурс **SQL Server — Azure Arc** после регистрации и измените теги на странице **Обзор**.

* Для подключения экземпляров SQL Server к Azure Arc требуется учетная запись с широким набором разрешений. Подробности см. в [Необходимые разрешения](overview.md#required-permissions).

## <a name="october-2020"></a>Октябрь 2020 г.

Обновление за октябрь содержит следующие улучшения.

* Колонка «Регистрация SQL Server с поддержкой Azure Arc» теперь содержит вкладку **Теги**. Теги включены в скрипт регистрации и отражаются в ресурсе(ах) **SQL Server — Azure Arc**. Подробности см. в [Подключение SQL Server к Azure Arc](connect.md).

* Запись **Работоспособность среды** теперь поддерживает активацию **Оценка SQL** с портала путем развертывания *CustomScriptExtension*. Дополнительные сведения см. в статье о [настройке Оценки SQL](assess.md#run-on-demand-sql-assessment).

### <a name="known-issues"></a>Известные проблемы

В отношении октябрьского выпуска действуют следующие ограничения.

* Для подключения экземпляров SQL Server к Azure Arc требуется учетная запись с широким набором разрешений. Подробности см. в [Необходимые разрешения](overview.md#required-permissions).

## <a name="next-steps"></a>Следующие шаги

**Хотите попробовать?**  Быстро приступайте к работе с помощью [Руководства по началу работы с SQL Server с поддержкой Azure Arc](https://aka.ms/AzureArcSqlServerJumpstart).
