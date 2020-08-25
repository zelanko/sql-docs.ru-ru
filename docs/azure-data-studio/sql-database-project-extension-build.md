---
title: Сборка и публикация проекта
description: Сборка и публикация с помощью расширения проектов баз данных SQL Server
ms.custom: seodec18
ms.date: 06/25/2020
ms.reviewer: drskwier, maghan, sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: dzsquared
ms.author: drskwier
ms.openlocfilehash: 191b10fd32d7c49c3f4a4e81c109e52fb2a1a81c
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/13/2020
ms.locfileid: "88171373"
---
# <a name="build-and-publish-a-project"></a>Сборка и публикация проекта

Процесс сборки в расширении проектов баз данных SQL для Azure Data Studio позволяет создавать *DACPAC* в средах Windows, macOS и Linux. Проект затем можно развернуть в локальной или облачной среде с помощью процесса публикации.

## <a name="prerequisites"></a>Предварительные требования
- Установите и настройте [расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md).


## <a name="build-a-database-project"></a>Создание проекта базы данных

 В мини-приложении **Проекты** **Обозревателя** щелкните правой кнопкой мыши корневой узел *.sqlproj* и выберите **Сборка**.

 Автоматически отобразится область вывода с выходными данными процесса сборки.  Успешная сборка будет завершаться следующим сообщением: 

 ``` ... exited with code: 0 ```

## <a name="publish-a-database-project"></a>Публикация проекта базы данных

После успешной компиляции проекта с помощью процесса сборки базу данных можно опубликовать в экземпляре SQL Server. Чтобы опубликовать проект базы данных, в мини-приложении **Проекты** **Обозревателя** щелкните правой кнопкой мыши корневой узел *.sqlproj* и выберите **Опубликовать**.

В появившемся диалоговом окне **публикации базы данных** укажите соединение сервера и имя создаваемой базы данных.

## <a name="next-steps"></a>Дальнейшие действия

- [Расширение проектов баз данных SQL для Azure Data Studio](sql-database-project-extension.md)
- [Создание проектов баз данных SQL из командной строки](sql-database-project-extension-build-from-command-line.md)
