---
title: Соединитель с Oracle (Microsoft) | Документация Майкрософт
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a0ad547d26c86c43b0009cdf20acae33ed7e8ab7
ms.sourcegitcommit: 57e20b7d02853ec9af46b648106578aed133fb45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69553242"
---
# <a name="microsoft-connector-for-oracle"></a>Соединитель с Oracle (Microsoft)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Соединитель с Oracle (Microsoft) позволяет экспортировать данные из источника данных Oracle в пакет служб SSIS и загружать их в него.

## <a name="version-support"></a>Поддерживаемые версии

Соединитель с Oracle (Microsoft) поддерживает следующие продукты Microsoft SQL Server:

- все версии SQL Server, начиная с SQL Server 2019;
- SQL Server Data Tools (SSDT)

Поддерживаются следующие версии Oracle Database и источника данных Oracle:

- Oracle 10.x;
- Oracle 11.x;
- Oracle 12c;
- Oracle 18c (без поддержки проверки подлинности Windows).

Oracle Database поддерживается всеми операционными системами и платформами.
> [!NOTE]
>
> Клиент Oracle не является обязательным для соединителя с Oracle Database (Microsoft) в SQL Server 2019.

## <a name="installation"></a>Установка

Если необходимо запустить пакет в SQL Server, [здесь](https://www.microsoft.com/en-us/download/details.aspx?id=58228) можно скачать соединитель с Oracle Database (Microsoft). Затем выполните указания мастера установки.

После установки соединителя необходимо перезапустить службу интеграции SQL Server, чтобы убедиться, что источник и назначение Oracle работают правильно.

Если вам нужно разработать пакет с помощью соединителя, скачивать соединитель не нужно. Он входит в состав в SQL Server Data Tools (SSDT) начиная с версии 15.9.0.

## <a name="uninstallation"></a>Удаление

Удалить соединитель с Oracle Database (Microsoft) из SQL Server можно с помощью мастера удаления.

## <a name="design-ssis-package-with-previous-version"></a>Разработка пакета служб SSIS для прежних версий

Соединитель с Oracle Database (Microsoft) входит в состав SQL Server Data Tools начиная с версии 15.9.0, поэтому при проектировании пакетов SSIS, предназначенных для SQL Server 2019, его установка не требуется.

При проектировании пакета служб SSIS, предназначенного для SQL Server 2017 и более ранних версий, необходимо установить соединитель с Oracle от Attunity для требуемой версии.

**Ссылки для скачивания:**

- [SQL Server 2017: соединитель с Oracle (Microsoft) от Attunity версии 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=55179)
- [SQL Server 2016: соединитель с Oracle (Microsoft) от Attunity версии 4.0](https://www.microsoft.com/en-us/download/details.aspx?id=52950)
- [SQL Server 2014: соединитель с Oracle (Microsoft) от Attunity версии 3.0](https://www.microsoft.com/en-us/download/details.aspx?id=44582)
- [SQL Server 2012: соединитель с Oracle (Microsoft) от Attunity версии 2.0](https://www.microsoft.com/en-us/download/details.aspx?id=29283)

## <a name="next-steps"></a>Следующие шаги

- Настройка [диспетчера подключений Oracle](oracle-connection-manager.md).
- Настройка [источника Oracle](oracle-source.md).
- Настройка [назначения Oracle](oracle-destination.md).
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA5u35j).
