---
title: Добавление расширений
titleSuffix: Azure Data Studio
description: Добавление расширений из Marketplace в Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 10/03/2019
ms.openlocfilehash: 6f0a2ab021873a2a9414bfbcdb7aed63c2d31056
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72166719"
---
# <a name="extend-the-functionality-of-includename-sosincludesname-sos-shortmd"></a>Расширение функциональности [!INCLUDE[name-sos](../includes/name-sos-short.md)]

Расширения в [!INCLUDE[name-sos](../includes/name-sos-short.md)] позволяют легко расширять функциональные возможности базовой установки [!INCLUDE[name-sos](../includes/name-sos-short.md)]. 

Расширения предоставляются командой Azure Data Studio (Майкрософт), а также сторонним сообществом (в том числе вами). Дополнительные сведения о создании расширений см. в статье [Создание расширений](extension-authoring.md).


## <a name="add-azure-data-studio-extensions"></a>Добавление расширений Azure Data Studio

1. Получите доступ к доступным расширениям, выбрав значок "Расширения" или щелкнув **Расширения** в меню **Представление**.

    ![Значок "Диспетчер расширений"](media/extensions/extension-manager-icon.png)

    Чтобы быстро получить доступ к диспетчеру расширений, можно также нажать клавиши `Ctrl+Shift+X` (в Windows или Linux) или `Command+Shift+X` (в macOS).

2. Выберите доступное расширение и просмотрите сведения о нем.
    ![сведения о расширении](media/extensions/extension-details.png)

3. Выберите нужное расширение и **установите** его.

4. После установки выберите **Перезагрузить**, чтобы включить расширение в Azure Data Studio (требуется только при первой установке расширения).

Если при получении доступа к диспетчеру расширений в Azure Data Studio возникают проблемы, вы можете скачать необходимое расширение на [вики-сайте GitHub](https://github.com/microsoft/azuredatastudio/wiki/List-of-Extensions).


## <a name="access-installed-azure-data-studio-extensions"></a>Доступ к установленным расширениям Azure Data Studio

Каждое расширение предоставляет особые дополнительные возможности в Azure Data Studio. Поэтому точки входа в расширения могут быть разными. Сведения о том, как получить доступ к возможностям установленного расширения, см. в документации по нему.
