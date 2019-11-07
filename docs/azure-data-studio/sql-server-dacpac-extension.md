---
title: Расширение DACPAC-файлов SQL Server
titleSuffix: Azure Data Studio
description: Установка и использование расширения DACPAC SQL Server для Azure Data Studio
ms.custom: seodec18
ms.date: 11/04/2019
ms.reviewer: alayu; sstein
ms.prod: sql
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.openlocfilehash: d33f43f4232e7a9a62365c5bb438c91339f4fd47
ms.sourcegitcommit: 830149bdd6419b2299aec3f60d59e80ce4f3eb80
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/04/2019
ms.locfileid: "73532417"
---
# <a name="sql-server-dacpac-extension"></a>Расширение DACPAC-файлов SQL Server

**Мастер приложений уровня данных** предоставляет мастер с удобным интерфейсом для развертывания и извлечения DACPAC-файлов, а также импорта и экспорта BACPAC-файлов.


## <a name="features"></a>Компоненты

* Развертывание DACPAC-файлов в экземпляре SQL Server
* Извлечение экземпляра SQL Server в DACPAC-файл
* Создание базы данных из BACPAC-файлов
* Экспорт схемы и данных в BACPAC-файл

![Демонстрационный GIF-файл расширения DACPAC](media/extensions/sql-server-dacpac-extension/dacpac-extension-demo.gif)


## <a name="why-would-i-use-the-data-tier-application-wizard"></a>Как использовать мастер приложения уровня данных?

Мастер упрощает управление файлами DACPAC и BACPAC, что облегчает разработку и развертывание элементов уровня данных, поддерживающих приложение. Дополнительные сведения об использовании приложений уровня данных см. в [нашей документации](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).


## <a name="install-the-extension"></a>Установка расширения

1. Щелкните значок расширений, чтобы просмотреть доступные расширения.

    ![Значок "Диспетчер расширений"](media/extensions/extension-manager-icon.png)

2. Найдите расширение **SQL Server DACPAC** и выберите его, чтобы просмотреть сведения. Щелкните **Установить**, чтобы добавить расширение.

3. После установки выберите **Перезагрузить**, чтобы включить расширение в Azure Data Studio (требуется только при первой установке расширения).


## <a name="launch-the-data-tier-application-wizard"></a>Запуск мастера приложений уровня данных

Чтобы запустить мастер, щелкните правой кнопкой мыши папку "Базы данных" или щелкните правой кнопкой мыши нужную базу данных в Обозревателе объектов. Затем щелкните **Мастер приложений уровня данных**.

![меню запуска расширения DACPAC](media/extensions/sql-server-dacpac-extension/dacpac-extension-launch.png)


## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о DACPAC-файлах см. в [нашей документации](https://docs.microsoft.com/sql/relational-databases/data-tier-applications/data-tier-applications?view=sql-server-2017).
Сообщить о проблемах и запросить функции можно [здесь](https://github.com/microsoft/azuredatastudio/issues).