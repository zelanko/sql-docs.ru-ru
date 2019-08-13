---
title: Расширение DACPAC-файлов SQL Server
titleSuffix: Azure Data Studio
description: Установка и использование расширения DACPAC-файлов SQL Server (предварительная версия) для Azure Data Studio
ms.custom: seodec18
ms.date: 03/18/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: e40e377310b33034b4abecdc5e58eab17d39695d
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "67959198"
---
# <a name="sql-server-dacpac-extension-preview"></a>Расширение DACPAC-файлов SQL Server (предварительная версия)

**Мастер приложений уровня данных** предоставляет удобный интерфейс для развертывания и извлечения DACPAC-файлов, а также импорта и экспорта BACPAC-файлов.

Сейчас это расширение находится на этапе начальной предварительной версии. Сообщить о проблемах и запросить функции можно [здесь](https://github.com/microsoft/azuredatastudio/issues).

![действия с данными](media/sql-server-dacpac-extension/data-tier-application-actions.png)

 ### <a name="requirements"></a>Требования
 * Для запуска этого мастера требуется активное подключение к экземпляру SQL Server.

 ### <a name="how-do-i-start-the-data-tier-application-wizard"></a>Как запустить мастер приложений уровня данных?
 * Самый простой способ начать работу с мастером — щелкнуть базу данных правой кнопкой мыши в обозревателе объектов и выбрать пункт **Мастер приложений уровня данных**.
 * Если пользователь подключен к экземпляру SQL Server, он также может запустить мастер из палитры команд (CTRL+SHIFT+P), выполнив поиск строки **мастер приложений уровня данных.**

 ### <a name="why-would-i-use-the-data-tier-application-wizard"></a>Как использовать мастер приложений уровня данных?
 Этот мастер был создан, чтобы добавить возможность извлечения и развертывания DACPAC-файлов, а также импорта и экспорта BACPAC-файлов в Azure Data Studio.

## <a name="install-the-sql-server-dacpac-extension"></a>Установка расширения DACPAC-файлов SQL Server

1. Чтобы открыть диспетчер расширений и получить доступ к доступным расширениям, щелкните значок расширений или выберите пункт **Расширения** в меню **Вид**.
2. Выберите расширение DACPAC-файлов SQL Server и щелкните **Установить**.
1. Выберите **Перезагрузить**, чтобы включить расширение (требуется только при первой установке расширения).
2. Перейдите на панель мониторинга управления, щелкнув сервер или базу данных правой кнопкой мыши и выбрав пункт **Управление**.
3. Установленные расширения отображаются в виде вкладок на панели мониторинга управления.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о DACPAC-файлах см. в [нашей документации](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).