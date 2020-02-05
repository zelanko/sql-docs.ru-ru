---
title: Система управления версиями
titleSuffix: Azure Data Studio
description: Сведения о настройке системы управления версиями в Azure Data Studio
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: markingmyname
ms.author: maghan
ms.reviewer: alayu; sstein
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: c278bcf6cff451396b3d677b203f207b68fd6dc5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67959281"
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>Использование системы управления версиями в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поддерживает Git для управления версиями/исходным кодом.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Поддержка Git в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поставляется вместе с диспетчером системы управления версиями (SCM) Git, но вам все равно нужно [установить Git (версии 2.0.0 или более поздней)](https://git-scm.com/download), чтобы получить доступ к этим функциям. 



## <a name="open-an-existing-git-repository"></a>Открытие существующего репозитория Git

1. В меню **Файл** выберите **Открыть папку...**
2. Перейдите в папку с файлами, отслеживаемыми Git, и щелкните элемент **Выбрать папку**. Здесь можно выбрать вложенные папки в локальном репозитории.


## <a name="initialize-a-new-git-repository"></a>Инициализация нового репозитория Git

1. Выберите **Система управления версиями**, а затем щелкните значок Git.

   ![Значок Git для системы управления версиями](media/source-control/source-control.png)

1. Введите путь к папке, которую нужно инициализировать в качестве репозитория Git, и нажмите клавишу **ВВОД**.

   ![инициализировать репозиторий Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Работа с репозиториями Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует свою реализацию Git от VS Code, но сейчас не поддерживает дополнительные поставщики SCM. Дополнительные сведения о работе с Git после открытия или инициализации репозитория см. в разделе [Поддержка Git в VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Дополнительные ресурсы
- [Документация по Git](https://git-scm.com/documentation)
