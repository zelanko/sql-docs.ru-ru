---
title: Расширение DACPAC-файлов SQL Server
description: Узнайте, как установить и запустить мастер приложений уровня данных, который упрощает развертывание и извлечение DACPAC-файлов, а также их импорт и экспорт.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
ms.topic: conceptual
author: yualan
ms.author: alayu
ms.reviewer: maghan, sstein
ms.custom: ''
ms.date: 11/04/2019
ms.openlocfilehash: f14aee08f889511af005c4451e4e1431397171a2
ms.sourcegitcommit: cc23d8646041336d119b74bf239a6ac305ff3d31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/23/2020
ms.locfileid: "91123235"
---
# <a name="sql-server-dacpac-extension"></a>Расширение DACPAC-файлов SQL Server

**Мастер приложений уровня данных** предоставляет мастер с удобным интерфейсом для развертывания и извлечения DACPAC-файлов, а также импорта и экспорта BACPAC-файлов.

## <a name="features"></a>Компоненты

* Развертывание DACPAC-файлов в экземпляре SQL Server
* Извлечение экземпляра SQL Server в DACPAC-файл
* Создание базы данных из BACPAC-файлов
* Экспорт схемы и данных в BACPAC-файл

![Демонстрационный GIF-файл расширения DACPAC](media/sql-server-dacpac-extension/dacpac-extension-demo.gif)

## <a name="why-would-i-use-the-data-tier-application-wizard"></a>Как использовать мастер приложения уровня данных?

Мастер упрощает управление файлами DACPAC и BACPAC, что облегчает разработку и развертывание элементов уровня данных, поддерживающих приложение. Дополнительные сведения об использовании приложений уровня данных см. в [нашей документации](../../relational-databases/data-tier-applications/data-tier-applications.md).

## <a name="install-the-extension"></a>Установка расширения

1. Щелкните значок расширений, чтобы просмотреть доступные расширения.

    ![Значок "Диспетчер расширений"](media/add-extensions/extension-manager-icon.png)

2. Найдите расширение **SQL Server DACPAC** и выберите его, чтобы просмотреть сведения. Выберите **Установить**, чтобы добавить расширение.

3. После установки выберите **Перезагрузить**, чтобы включить расширение в Azure Data Studio (требуется только при первой установке расширения).

## <a name="launch-the-data-tier-application-wizard"></a>Запуск мастера приложений уровня данных

Чтобы запустить мастер, щелкните правой кнопкой мыши папку "Базы данных" или щелкните правой кнопкой мыши нужную базу данных в Обозревателе объектов. Затем выберите **Мастер приложений уровня данных**.

![меню запуска расширения DACPAC](media/sql-server-dacpac-extension/dacpac-extension-launch.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о DACPAC-файлах см. в [нашей документации](../../relational-databases/data-tier-applications/data-tier-applications.md).
Сообщить о проблемах и запросить функции можно [здесь](https://github.com/microsoft/azuredatastudio/issues).