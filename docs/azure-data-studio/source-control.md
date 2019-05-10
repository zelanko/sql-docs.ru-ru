---
title: Система управления версиями
titleSuffix: Azure Data Studio
description: Узнайте, как настроить систему управления версиями в студии данных Azure
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: 7adcae568e97d4bbecd5f901a76dc465dad53ba7
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65089725"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>С помощью системы управления версиями в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поддерживает Git для версии или системы управления версиями.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Поддержка Git в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поставляется с диспетчера системы управления версиями (SCM) Git, но вы по-прежнему нужно [установите Git (версии 2.0.0 или более поздней версии)](https://git-scm.com/download) прежде, чем эти функции доступны. 



## <a name="open-an-existing-git-repository"></a>Откройте существующий репозиторий Git

1. В разделе **файл** меню, выберите **открыть папку...**
2. Перейдите к папке, содержащей файлы, отслеживанием в git и нажмите кнопку **Выбор папки**. Вложенные папки в локальном репозитории, подходит для выбора здесь.


## <a name="initialize-a-new-git-repository"></a>Инициализируйте новый репозиторий git

1. Выберите **системы управления версиями**, затем щелкните значок git.

   ![Значок git системы управления версиями](media/source-control/source-control.png)

1. Введите путь к папке, необходимо инициализировать репозиторий Git и нажмите клавишу **ввод**.

   ![Инициализируйте репозиторий Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Работа с репозиториями Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует его реализация Git из VS Code, но в настоящее время не поддерживает дополнительные поставщики SCM. Дополнительные сведения о работе с Git, после открытия или инициализируйте репозиторий, см. в разделе [поддержку Git в Visual STUDIO Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Дополнительные ресурсы
- [Документация по Git](https://git-scm.com/documentation)
