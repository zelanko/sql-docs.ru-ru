---
title: Система управления версиями в Studio операций SQL (Предварительная версия) | Документы Microsoft
description: Подробные сведения о настройке системы управления версиями в Studio операций SQL (Предварительная версия).
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 73fec13868004469b02f3117b9b8d70e1ec26ff3
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
#  <a name="using-source-control-in-includename-sosincludesname-sos-shortmd"></a>С помощью системы управления версиями в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поддерживает Git для версии или системы управления версиями.


## <a name="git-support-in-includename-sosincludesname-sos-shortmd"></a>Поддержка Git в [!INCLUDE[name-sos](../includes/name-sos-short.md)]

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поставляется с диспетчер системы управления версиями Git (SCM), но все еще нуждаются в [установите Git (версии 2.0.0 или более поздней версии)](https://git-scm.com/download) перед доступны следующие возможности. 



## <a name="open-an-existing-git-repository"></a>Откройте существующий репозиторий Git

1. В разделе **файл** последовательно выберите пункты **открыть папку...**
2. Перейдите к папке, содержащей файлы, отслеживается git и нажмите кнопку **Выбор папки**. Вложенные папки в ваш локальный репозиторий можно здесь.


## <a name="initialize-a-new-git-repository"></a>Инициализировать новый репозиторий git

1. Выберите **системы управления версиями**, затем выберите значок git.

   ![Значок git системы управления версиями](media/source-control/source-control.png)

1. Введите путь к папке, необходимо инициализировать в качестве репозитория Git и нажмите клавишу **ввод**.

   ![инициализировать репозиторий Git](media/source-control/initialize-git-repository.png)

## <a name="working-with-git-repositories"></a>Работа с помощью репозиториев Git

[!INCLUDE[name-sos](../includes/name-sos-short.md)] наследует его реализация Git VS Code, но в настоящее время не поддерживает дополнительные поставщики диспетчера управления Службами. Дополнительные сведения о работе с Git после открытия или инициализировать репозиторий см. в разделе [поддержки Git в VS Code](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).


## <a name="additional-resources"></a>Дополнительные ресурсы
- [Документация по Git](https://git-scm.com/documentation)
