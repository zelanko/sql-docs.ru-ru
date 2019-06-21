---
title: Включение и отключение сбора данных об использовании и создание отчетов о сбоях
titleSuffix: Azure Data Studio
description: В этой статье описывается управление, если об использовании и сбоях, передает данные собираются и отправляются в корпорацию Майкрософт.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: cf358274f3a16f9c4330ad0f093d2ee32ac746b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66783101"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Включение или отключение сбора данных об использовании [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Как отключить ведение отчетов телеметрии

[!INCLUDE[name-sos](../includes/name-sos-short.md)] собирает данные об использовании и отправляет их в корпорацию Майкрософт для улучшения своих продуктов и услуг. Чтобы узнать больше, прочитайте [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Если вы не хотите отправлять данные об использовании в корпорацию Майкрософт, вы можете задать *telemetry.enableTelemetry* присвоить *false*.

Чтобы отключить все события телеметрии из [!INCLUDE[name-sos](../includes/name-sos-short.md)], из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableTelemetry": false
```

**Важное уведомление**: Этот параметр требует перезапуска [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу. 

## <a name="how-to-disable-crash-reporting"></a>Отключение создания отчетов о сбоях

Чтобы отключить создание отчетов о сбоях из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableCrashReporter": false
```

**Важное уведомление**: Этот параметр требует перезапуска [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу.

## <a name="additional-resources"></a>Дополнительные ресурсы
- [Параметры рабочей области и пользователя](settings.md)
