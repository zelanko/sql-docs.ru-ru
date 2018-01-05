---
title: "Операции SQL Studio пользователя (Предварительная версия) и параметры рабочей области | Документы Microsoft"
description: "Как изменить Studio операций SQL (Предварительная версия) пользователя и параметры рабочей области."
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: article
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2edea069c05e7ac0316042250f336f1a8c455af0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="user-and-workspace-settings"></a>Пользователь и параметры рабочей области

Его можно легко настроить [!INCLUDE[name-sos](../includes/name-sos-short.md)] по выбору параметров. Почти каждая часть [!INCLUDE[name-sos](../includes/name-sos-short.md)]в редактор, пользовательский интерфейс и поведение функциональной имеет параметры можно изменить.

[!INCLUDE[name-sos](../includes/name-sos-short.md)]предоставляет две различные области для параметров:

* **Пользователь** эти параметры применяются глобально ко всем экземплярам [!INCLUDE[name-sos](../includes/name-sos-short.md)] его открыть.
* **Рабочая область** параметры рабочей области Параметры, относящиеся к папке на компьютере и доступны, только когда открыт папку на боковой панели обозревателя. Параметры, определенные в этой области переопределения области пользователя.

## <a name="creating-user-and-workspace-settings"></a>Создание пользователей и параметры рабочей области

Команда меню **файл** > **предпочтения** > **параметры** (**кода**  >  **Установки** > **параметры** на Mac) предоставляет точку входа для настройки параметров пользователя и рабочей области. Предоставляется список параметров по умолчанию. Копирование параметров, которые необходимо внести изменения в соответствующий `settings.json` файл. В правой части вкладки позволяют быстро переключаться между пользователем и рабочей области файлов параметров.

Можно также открыть параметры пользователя и рабочей области из **палитры команд** (**Ctrl + Shift + P**) с **предпочтения: Откройте параметры пользователя** и  **Предпочтений: Откройте рабочую область параметров** или используйте сочетание клавиш (**Ctrl +**).

Следующий пример отключает номера строк в редакторе и настраивает строк перенос автоматически в зависимости от размера редактор текста.

![Пример параметров](media/settings/sample-settings.png)

Изменения параметров загружаются по [!INCLUDE[name-sos](../includes/name-sos-short.md)] после измененного `settings.json` сохранить файл.

>**Примечание:** параметры рабочей области полезны для конкретного проекта параметры общего доступа в группе.

## <a name="settings-file-locations"></a>Расположения файлов параметров

В зависимости от используемой платформы файла параметров пользователя находится здесь:

* **Windows**`%APPDATA%\sqlops\User\settings.json`
* **Mac**`$HOME/Library/Application Support/sqlops/User/settings.json`
* **Linux**`$HOME/.config/sqlops/User/settings.json`

Файл параметров рабочей области находится в разделе `.[!INCLUDE[name-sos](../includes/name-sos-short.md)]` в папке проекта.


## <a name="additional-resources"></a>Дополнительные ресурсы

Поскольку [!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует параметры пользователя и рабочей области находится функциональные возможности из кода Visual Studio, подробные сведения о параметрах в [параметры для кода Visual Studio](https://code.visualstudio.com/docs/getstarted/settings) статьи.