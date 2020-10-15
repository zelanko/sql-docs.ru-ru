---
title: Совместимость с платформой приложения уровня данных
description: Ознакомьтесь с сообщением об ошибке, которое может появиться при попытке выполнения действий в SQL Server Data Tools (SSDT), использующих несовместимые версии платформы DAC Framework.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 5f8e7f4a-f157-442a-8fe5-32b8774776dc
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 6515eb1fb2c088681cc033aab59066f3c680f9dc
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91986857"
---
# <a name="dac-framework-compatibility"></a>Совместимость с платформой приложения уровня данных

При попытке выполнить действие, которое использует платформу приложений уровня данных, SQL Server Data Tools (SSDT) проверяет версию DACFx на компьютере. Если SSDT не работает с установленной версией DACFx, отображается следующая ошибка:

**На этом компьютере установлены несовместимые версии SQL Server Data Tools и компонентов среды выполнения базы данных**

Можно загрузить более новую версию SSDT со страницы [Установка последней версии SQL Server Data Tools](./download-sql-server-data-tools-ssdt.md).