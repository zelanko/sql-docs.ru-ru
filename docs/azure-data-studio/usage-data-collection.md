---
title: Включить или отключить сбор данных об использовании и отчеты для Azure Data Studio о сбоях | Документация Майкрософт
description: В этой статье описывается управление, если об использовании и сбоях, передает данные собираются и отправляются в корпорацию Майкрософт.
ms.custom: tools|sos
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0a5adf802ab07e05f1041b1385044e2d580db32
ms.sourcegitcommit: 35e4c71bfbf2c330a9688f95de784ce9ca5d7547
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/16/2018
ms.locfileid: "49356485"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Включение или отключение сбора данных об использовании [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Как отключить ведение отчетов телеметрии

[!INCLUDE[name-sos](../includes/name-sos-short.md)] собирает данные об использовании и отправляет их в корпорацию Майкрософт для улучшения своих продуктов и услуг. Чтобы узнать больше, прочитайте [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Если вы не хотите отправлять данные об использовании в корпорацию Майкрософт, вы можете задать *telemetry.enableTelemetry* присвоить *false*.

Чтобы отключить все события телеметрии из [!INCLUDE[name-sos](../includes/name-sos-short.md)], из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableTelemetry": false
```

**Важное уведомление**: этот параметр требует перезапуска [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу. 

## <a name="how-to-disable-crash-reporting"></a>Отключение создания отчетов о сбоях

Чтобы отключить создание отчетов о сбоях из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableCrashReporter": false
```

**Важное уведомление**: этот параметр требует перезапуска [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу.

## <a name="additional-resources"></a>Дополнительные ресурсы
- [Параметры рабочей области и пользователя](settings.md)
