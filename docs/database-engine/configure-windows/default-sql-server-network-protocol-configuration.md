---
title: Конфигурация сетевого протокола SQL Server по умолчанию | Документы Майкрософт
description: Описание факторов, которые определяют необходимость включения или отключения сетевых протоколов во время установки SQL Server. Сведения о настройке протоколов после установки.
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server], default settings
- default protocols, after install
ms.assetid: 635ea361-a797-4971-bd05-e3415862bc5c
author: markingmyname
ms.author: maghan
ms.openlocfilehash: d5463ac163271cf14f5b52167559bc8f3f53d805
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671117"
---
# <a name="default-sql-server-network-protocol-configuration"></a>Конфигурация сетевого протокола SQL Server по умолчанию
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
Для улучшения защиты при установке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] сетевая возможность подключения в некоторых случаях блокируется. Сетевая функциональность TCP/IP не блокируется, если используется выпуск Enterprise, Standard, Evaluation или Workgroup или если на компьютере установлена предыдущая версия [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Чтобы можно было устанавливать локальные соединения с сервером, при установке SQL Server всегда активируется протокол общей памяти. Служба браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] может быть остановлена в зависимости от параметров и условий установки SQL Server.

Чтобы настроить сетевые протоколы после установки, используйте узел "Сетевая конфигурация [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] " диспетчера конфигурации [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Чтобы настроить автоматический запуск службы браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , используйте узел "Службы [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] " диспетчера конфигурации [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).


## <a name="default-configuration"></a>Конфигурация по умолчанию

Конфигурация SQL Server 2005 после установки описана в следующей таблице.

|Выпуск | Новая установка или установленный экземпляр | Общая память | TCP/IP | Именованные каналы|
| -------- | -- | -- | -- | --  |  
|Enterprise | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Standard | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Интернет | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Разработчик | Новая установка | Активировано | Выключено | Отключено для сетевых подключений.|
|Ознакомительная версия | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|SQL Server Express | Новая установка | Активировано | Выключено | Отключено для сетевых подключений.|
|Все выпуски | Присутствует установленный экземпляр, но выполнение не обновляется. | То же, что и при новой установке | То же, что и при новой установке | То же, что и при новой установке|
|Все выпуски | Обновление | Активировано | Сохраняются параметры установленного экземпляра. | Сохраняются параметры установленного экземпляра.|


>[!NOTE]
> Если экземпляр работает в отказоустойчивом кластере [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], он прослушивает порты каждого IP-адреса, выбранного для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] во время установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
 
>[!NOTE]
> При установке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] с аргументами командной строки можно указать, какие протоколы нужно включить при помощи параметров `TCPENABLED` и `NPENABLED` . Дополнительные сведения см. в разделе [Установка SQL Server из командной строки](../install-windows/install-sql-server-from-the-command-prompt.md).

## <a name="creating-a-connection-string"></a>Создание строки подключения

Примеры строк подключения см. в следующих разделах:
* [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
* [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)



## <a name="ssnoversion_md-browser-settings"></a>[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Параметры браузера

Во время установки можно настроить автоматический запуск службы браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . По умолчанию служба запускается автоматически при выполнении следующих условий:

* при обновлении установки;
* при установке параллельно с другим экземпляром [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)];
* при установке в кластере;
* при установке именованного экземпляра ядра СУБД, включая все экземпляры [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Express;
* при установке именованного экземпляра служб Analysis Services.

## <a name="see-also"></a>См. также:

[Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)

[Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)