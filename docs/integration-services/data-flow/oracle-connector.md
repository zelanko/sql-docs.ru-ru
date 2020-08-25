---
description: Соединитель с Oracle (Microsoft)
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
ms.openlocfilehash: a5bb5631a398e398b45b84a0ee70b51f49c90988
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88430756"
---
# <a name="microsoft-connector-for-oracle"></a>Соединитель с Oracle (Microsoft)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Соединитель с Oracle (Microsoft) позволяет экспортировать данные из источника данных Oracle в пакет служб SSIS и загружать их в него.

## <a name="version-support"></a>Поддерживаемые версии

Соединитель с Oracle (Microsoft) поддерживает следующие продукты Microsoft SQL Server:

- Версии начиная с Накопительного обновления 1 (CU1) для SQL Server 2019.
- SQL Server Data Tools (SSDT) 15.9.3 или более поздней версии для Visual Studio 2017
- Microsoft SQL Server Data Tools (SSDT) для Visual Studio 2019

Поддерживаются следующие версии Oracle Database и источника данных Oracle:

- Oracle 10.x;
- Oracle 11.x;
- Oracle 12c;
- Oracle 18c (без поддержки проверки подлинности Windows).
- Oracle 19c (без поддержки проверки подлинности Windows)

Oracle Database поддерживается всеми операционными системами и платформами.
> [!NOTE]
>
> Клиент Oracle не является обязательным для соединителя с Oracle Database (Microsoft) в SQL Server 2019.

## <a name="installation"></a>Установка

Чтобы установить соединитель для базы данных Oracle, скачайте и запустите установщик со [страницы последней версии соединителя Майкрософт для Oracle](https://www.microsoft.com/download/details.aspx?id=58228). Затем выполните указания мастера установки.

После установки соединителя необходимо перезапустить службу интеграции SQL Server, чтобы убедиться в том, что источник и назначение Oracle работают правильно.

Для выполнения пакета SSIS, предназначенного для SQL Server 2017 и более ранних версий, помимо **соединителя Майкрософт для Oracle**, необходимо установить **клиент Oracle** и **соединитель Майкрософт для Oracle от Attunity** соответствующих версий по следующим ссылкам:

- [SQL Server 2017: соединитель с Oracle (Microsoft) от Attunity версии 5.0](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: соединитель с Oracle (Microsoft) от Attunity версии 4.0](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: соединитель с Oracle (Microsoft) от Attunity версии 3.0](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: соединитель с Oracle (Microsoft) от Attunity версии 2.0](https://www.microsoft.com/download/details.aspx?id=29283)

## <a name="limitations-and-known-issues"></a>Ограничения и известные проблемы

- Представления не указаны в списке источников Oracle *Имя таблицы или представления*. В качестве временного решения используйте команду SQL и выполните действие по выбору * из представления или по заданию имени представления для свойства [Oracle Source].[TableName] в расширенном редакторе.

## <a name="uninstallation"></a>Удаление

Удалить соединитель Майкрософт для базы данных Oracle из SQL Server можно с помощью мастера удаления.

## <a name="next-steps"></a>Дальнейшие действия

- Настройка [диспетчера подключений Oracle](oracle-connection-manager.md).
- Настройка [источника Oracle](oracle-source.md).
- Настройка [назначения Oracle](oracle-destination.md).
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA5u35j).
