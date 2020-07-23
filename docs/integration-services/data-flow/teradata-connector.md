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
ms.openlocfilehash: a33855bdd5871f39911210c1fa5afe38414268ce
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917736"
---
# <a name="microsoft-connector-for-teradata"></a>Соединитель с Teradata (Microsoft)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]

Соединитель с Teradata (Microsoft) позволяет экспортировать данные из баз данных Teradata в пакет служб SSIS и загружать данные в них.

Этот новый соединитель поддерживает базы данных с таблицами с поддержкой 1 МБ.

## <a name="version-support"></a>Поддерживаемые версии

Соединитель с Teradata (Microsoft) поддерживает следующие продукты Microsoft SQL Server:

- Microsoft SQL Server 2019
- Microsoft SQL Server Data Tools (SSDT) 15.8.1 или более поздней версии для Visual Studio 2017
- Microsoft SQL Server Data Tools (SSDT) для Visual Studio 2019

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

На 32-разрядных компьютерах установите следующие драйверы из [пакета установки средств и служебных программ Teradata для Windows](https://downloads.teradata.com/download/tools/teradata-tools-and-utilities-windows-installation-package):

- драйвер ODBC Teradata (32-разрядный);
- интерфейс API PT Teradata (32-разрядный).

На 64-разрядных компьютерах установите следующие драйверы:

- драйвер ODBC Teradata (64-разрядный);
- интерфейс API PT Teradata (64-разрядный).

Чтобы установить соединитель для базы данных Teradata, скачайте и запустите установщик со [страницы последней версии соединителя Майкрософт для Teradata](https://www.microsoft.com/download/details.aspx?id=100599). Затем выполните указания мастера установки.

После установки соединителя необходимо перезапустить службу интеграции SQL Server, чтобы убедиться в том, что источник и назначение Teradata работают правильно.

## <a name="design-and-execute-ssis-packages"></a>Проектирование и выполнение пакетов служб SSIS

Соединитель с Teradata (Microsoft) имеет интерфейс, аналогичный соединителю Attunity Teradata. Пользователь может создавать новые пакеты на основе предыдущего интерфейса, используя SSDT для VS 2017 или VS 2019 с *SQL Server 2019 в качестве целевой платформы*.

Целевой и конечный объекты Teradata находятся в категории "Общие".

![Компонент Teradata](media/teradata-component.png)

Диспетчер подключений Teradata указан как TERADATA.

![Тип диспетчера подключений Teradata](media/teradata-connection-manager-type.png)

Существующие пакеты служб SSIS, разработанные с помощью соединителя Attunity Teradata, будут автоматически обновлены для использования соединителя с Teradata (Microsoft). Также будут изменены значки.

Для выполнения пакета служб SSIS, *предназначенного для SQL Server 2017 и более ранних версий*, необходимо установить **соединитель Майкрософт с Teradata от Attunity** требуемой версии по следующей ссылке.

- [SQL Server 2017: соединитель с Teradata (Microsoft) от Attunity версии 5.0](https://www.microsoft.com/download/details.aspx?id=55179)
- [SQL Server 2016: соединитель с Teradata (Microsoft) от Attunity версии 4.0](https://www.microsoft.com/download/details.aspx?id=52950)
- [SQL Server 2014: соединитель с Teradata (Microsoft) от Attunity версии 3.0](https://www.microsoft.com/download/details.aspx?id=44582)
- [SQL Server 2012: соединитель с Teradata (Microsoft) от Attunity версии 2.0](https://www.microsoft.com/download/details.aspx?id=29283)

Для проектирования пакета служб SSIS в SSDT, *предназначенного для SQL Server 2017 и более ранних версий*, вам потребуется **соединитель с Teradata (Microsoft)** и **соединитель с Teradata (Microsoft) от Attunity** требуемой версии.

## <a name="limitationsandknownissues"></a>Ограничения и известные проблемы

- В редакторе источника и целевого объекта Teradata свойство  **База данных по умолчанию**  не действует. В качестве обходного решения введите имя базы данных в раскрывающемся списке, чтобы отфильтровать таблицу или представление.

- В редакторе источника и целевого объекта Teradata шаг сопоставления не работает при вводе  \<database>.<table/view>. В качестве обходного решения введите  \<database>.<table/view>, а затем щелкните раскрывающийся список.

- В редакторе источника Teradata представление не отображается, если выбран режим доступа к данным "Имя таблицы — экспорт одной таблицы на тип". В качестве обходного решения используйте расширенный редактор источника Teradata.

- В редакторе целевого объекта Teradata атрибуту PackMaximum невозможно присвоить значение True. В противном случае возникает ошибка.

## <a name="uninstallation"></a>Удаление

Удалить **соединитель с Teradata (Microsoft)** можно с помощью мастера удаления.

## <a name="next-steps"></a>Дальнейшие действия

- Настройка [диспетчера подключений Teradata](teradata-connection-manager.md)
- Настройка [источника Teradata](teradata-source.md)
- Настройка [назначения Teradata](teradata-destination.md)
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA6iwdw).
