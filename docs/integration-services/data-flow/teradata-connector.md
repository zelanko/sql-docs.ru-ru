---
title: Соединитель с Teradata (Microsoft) | Документация Майкрософт
ms.custom: ''
ms.date: 11/22/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ca25b7425ce74cea820e295a6a99bc3a3c1e2817
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "75755855"
---
# <a name="microsoft-connector-for-teradata-preview"></a>Соединитель с Teradata (Microsoft) (предварительная версия)
[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Соединитель с Teradata (Microsoft) позволяет экспортировать данные из баз данных Teradata в пакет служб SSIS и загружать данные в них.

Этот новый соединитель поддерживает базы данных с таблицами с поддержкой 1 МБ.

## <a name="version-support"></a>Поддерживаемые версии

Соединитель с Teradata (Microsoft) поддерживает следующие продукты Microsoft SQL Server:

- Microsoft SQL Server 2019
- Microsoft SQL Server Data Tools (SSDT)

Соединитель с Teradata (Microsoft) использует программный интерфейс Teradata Parallel Transporter для загрузки данных в базу данных Teradata и экспорта данных из нее. Поддерживаются следующие версии:

- Teradata Parallel Transporter (Teradata PT) 16.10
- Teradata Parallel Transporter (Teradata PT) 16.20

В качестве источника данных поддерживаются следующие версии базы данных Teradata:

- Teradata Database 16.20
- Teradata Database 16.10
- Teradata Database 15.10
- Teradata Database 15.00

Руководство по программному интерфейсу Teradata Parallel Transporter см. в [документации Teradata](https://docs.teradata.com/).

## <a name="installation"></a>Установка

### <a name="prerequisite"></a>Предварительные требования

На 32-разрядных компьютерах установите следующие драйверы из [пакета установки средств и служебных программ Teradata для Windows](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package):

- драйвер ODBC Teradata (32-разрядный);
- интерфейс API PT Teradata (32-разрядный).

На 64-разрядных компьютерах установите следующие драйверы:

- драйвер ODBC Teradata (64-разрядный);
- интерфейс API PT Teradata (64-разрядный).

Чтобы установить соединитель для базы данных Teradata, скачайте и запустите установщик со [страницы последней версии соединителя Майкрософт для Teradata](https://www.microsoft.com/download/details.aspx?id=100599). Затем выполните указания мастера установки.

После установки соединителя необходимо перезапустить службу интеграции SQL Server, чтобы убедиться в том, что источник и назначение Teradata работают правильно.

Для выполнения пакета служб SSIS, предназначенного для SQL Server 2017 и более ранних версий, необходимо установить **соединитель Майкрософт с Teradata от Attunity** требуемой версии по следующей ссылке:

- [SQL Server 2017: соединитель с Teradata (Microsoft) от Attunity версии 5.0](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: соединитель с Teradata (Microsoft) от Attunity версии 4.0](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: соединитель с Teradata (Microsoft) от Attunity версии 3.0](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: соединитель с Teradata (Microsoft) от Attunity версии 2.0](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="uninstallation"></a>Удаление

Удалить **соединитель с Teradata (Microsoft)** можно с помощью мастера удаления.

## <a name="next-steps"></a>Дальнейшие действия

- Настройка [диспетчера подключений Teradata](teradata-connection-manager.md)
- Настройка [источника Teradata](teradata-source.md)
- Настройка [назначения Teradata](teradata-destination.md)
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA6iwdw).
