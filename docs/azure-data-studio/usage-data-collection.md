---
title: Включение и отключение сбора данных об использовании и ведения отчетов о сбоях
titleSuffix: Azure Data Studio
description: Эта статья описывает, как управлять сбором и отправкой данных об использовании и сбоях в корпорацию Майкрософт.
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 71ed86e9ad076a41099eaf4e56fe67a25b5f2c21
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67958948"
---
# <a name="enable-or-disable-usage-data-collection-for-includename-sosincludesname-sos-shortmd"></a>Включение или отключение сбора данных об использовании для [!INCLUDE[name-sos](../includes/name-sos-short.md)]

## <a name="how-to-disable-telemetry-reporting"></a>Отключение отчетов телеметрии

[!INCLUDE[name-sos](../includes/name-sos-short.md)] собирает данные об использовании и отправляет их в корпорацию Майкрософт для улучшения наших продуктов и услуг. Дополнительные сведения см. в [заявлении о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Если вы не хотите отправлять данные об использовании в Майкрософт, можно задать для параметра *telemetry.enableTelemetry* значение *false*.

Чтобы отключить все события телеметрии из [!INCLUDE[name-sos](../includes/name-sos-short.md)], добавьте следующий параметр в разделе **Файл**  >  **Настройки**  >  **Параметры**.

```json
    "telemetry.enableTelemetry": false
```

**Внимание**! Для вступления параметра в силу требуется перезапуск [!INCLUDE[name-sos](../includes/name-sos-short.md)]. 

## <a name="how-to-disable-crash-reporting"></a>Отключение отчетов о сбоях

Чтобы отключить отчеты о сбоях, добавьте следующий параметр в разделе **Файл**  >  **Настройки**  >  **Параметры**.

```json
    "telemetry.enableCrashReporter": false
```

**Внимание**! Для вступления параметра в силу требуется перезапуск [!INCLUDE[name-sos](../includes/name-sos-short.md)].

## <a name="additional-resources"></a>Дополнительные ресурсы
- [Рабочая область и параметры пользователя](settings.md)
