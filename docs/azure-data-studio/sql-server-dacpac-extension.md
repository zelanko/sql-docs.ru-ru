---
title: Расширение DACPAC-файл SQL Server
titleSuffix: Azure Data Studio
description: Установить и использовать расширение DACPAC-файл SQL Server (Предварительная версия) для Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e40e377310b33034b4abecdc5e58eab17d39695d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959198"
---
# <a name="sql-server-dacpac-extension-preview"></a>Расширение DACPAC-файлов SQL Server (предварительная версия)

**Data-tier Application Wizard** предоставляет удобные возможности для развертывания и извлечение DACPAC-файлы и импорта и экспорта файлов .bacpac.

Эта возможность сейчас доступна его начальной Предварительная версия. Пожалуйста, сообщить о проблемах и запросы функций [здесь.](https://github.com/microsoft/azuredatastudio/issues)

![действия с данными](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Требования
 * Этот мастер требуется активное подключение к экземпляру SQL Server для запуска.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Как запустить мастер приложения уровня данных?
 * Главная точка входа для мастера — базу данных в обозревателе объектов щелкните правой кнопкой мыши, а затем нажмите кнопку **мастер приложения уровня данных**.
 * Если пользователь подключен к экземпляру SQL Server, пользователь также мастер можно запустить на палитре команд (Ctrl + Shift + P), выполнив поиск **мастер приложения уровня данных.**

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Почему предпочтительнее использовать мастер приложений уровня данных?
 Этот мастер создан для добавления возможности для извлечения и развертывания DACPAC-файлы и импортировать, экспортировать файлы .bacpac студии данных Azure.

## <a name="install-the-sql-server-dacpac-extension"></a>Установите расширение DACPAC-файл SQL Server

1. Чтобы открыть диспетчер расширений и доступа доступных расширений, щелкните значок расширения или выберите **расширения** в **представление** меню.
2. Выберите расширение dacpac в SQL Server и нажмите кнопку **установить**.
1. Выберите **перезагрузить** для включения расширения (только обязательно при первоначальной установке расширения).
2. Перейдите к панели мониторинга управления, щелкнув правой кнопкой мыши сервер или базу данных и выбрав **управление**.
3. Установленные расширения отображаются как вкладки на панели мониторинга управления:

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о dacpac, [см. в нашей документации.](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017)