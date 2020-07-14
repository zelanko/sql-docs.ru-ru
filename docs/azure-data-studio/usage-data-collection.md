---
title: Включение и отключение сбора данных об использовании и ведения отчетов о сбоях
description: Эта статья описывает, как управлять сбором и отправкой данных об использовании и сбоях в корпорацию Майкрософт.
ms.prod: azure-data-studio
ms.technology: ''
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.custom: seodec18; seo-lt-2019
ms.date: 09/24/2018
ms.openlocfilehash: ad36e319338c90c33e0969f75ee34e980f3d23f5
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85771937"
---
# <a name="enable-or-disable-usage-data-collection-for-azure-data-studio"></a>Включение или отключение сбора данных об использовании для Azure Data Studio

## <a name="how-to-disable-telemetry-reporting"></a>Отключение отчетов телеметрии

Azure Data Studio собирает данные об использовании и отправляет их в корпорацию Майкрософт для улучшения наших продуктов и услуг. Дополнительные сведения см. в [заявлении о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=528096&clcid=0x409).

Если вы не хотите отправлять данные об использовании в Майкрософт, можно задать для параметра *telemetry.enableTelemetry* значение *false*.

Чтобы отключить все события телеметрии из Azure Data Studio, добавьте следующий параметр в разделе **Файл** > **Настройки** > **Параметры**.

```json
    "telemetry.enableTelemetry": false
```

**Внимание**! Для вступления параметра в силу требуется перезапуск Azure Data Studio. 

## <a name="how-to-disable-crash-reporting"></a>Отключение отчетов о сбоях

Чтобы отключить отчеты о сбоях, добавьте следующий параметр в разделе **Файл** > **Настройки** > **Параметры**.

```json
    "telemetry.enableCrashReporter": false
```

**Внимание**! Для вступления параметра в силу требуется перезапуск Azure Data Studio.

## <a name="additional-resources"></a>Дополнительные ресурсы
- [Рабочая область и параметры пользователя](settings.md)
