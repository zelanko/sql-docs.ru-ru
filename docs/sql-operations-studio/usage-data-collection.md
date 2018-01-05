---
title: "Включить или отключить сбор данных об использовании и приводит к сбою создания отчетов для операций SQL Studio (Предварительная версия) | Документы Microsoft"
description: "В этой статье описывается управление, если сбоев, данные отчетов и об использовании собираются и отправляются в корпорацию Майкрософт."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ae620951028ba8e0e82f89c4251238c92bc614ca
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Включение или отключение сбора данных об использовании[!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Отключение телеметрии отчетов

[!INCLUDE[name-sos](../includes/name-sos-short.md)]собирает данные об использовании и отправляет их в корпорацию Майкрософт для улучшения своих продуктов и услуг. Дополнительные сведения см. в статье [заявление о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Если вы не хотите отправлять данные об использовании в корпорацию Майкрософт, можно установить *telemetry.enableTelemetry* параметру *false*.

Чтобы отключить все события телеметрии из [!INCLUDE[name-sos](../includes/name-sos-short.md)], из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableTelemetry": false
```

**Важное замечание**: этот параметр требует перезагрузки [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу. 

## <a name="how-to-disable-crash-reporting"></a>Отключение создания отчетов о сбоях

Отключение создания отчетов о сбоях, из **файл** > **предпочтения** > **параметры**, добавьте следующий параметр:

```json
    "telemetry.enableCrashReporter": false
```

**Важное замечание**: этот параметр требует перезагрузки [!INCLUDE[name-sos](../includes/name-sos-short.md)] вступили в силу.

## <a name="additional-resources"></a>Дополнительные ресурсы
- [Рабочей области и параметры пользователей](settings.md)