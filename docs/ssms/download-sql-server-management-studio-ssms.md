---
title: Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
ms.technology: ssms
ms.topic: conceptual
keywords:
- установить SSMS, скачать SSMS, последняя версия SSMS
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- установка sql management studio
- скачать sql management studio
- ms sql management studio
- установить sql management studio
- скачать ssms
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
author: dnethi
ms.author: dinethi
ms.custom: ''
ms.date: 07/26/2019
ms.openlocfilehash: 46174db6dc0008dbeb9490cc96cf41cdef1bc3ed
ms.sourcegitcommit: a1ddeabe94cd9555f3afdc210aec5728f0315b14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/28/2019
ms.locfileid: "70123107"
---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md.md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

SQL Server Management Studio (SSMS) — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до баз данных SQL Azure. SSMS предоставляет средства для настройки, наблюдения и администрирования экземпляров SQL Server и баз данных. С помощью SSMS можно развертывать, отслеживать и обновлять компоненты уровня данных, используемые вашими приложениями, а также создавать запросы и скрипты.

Используйте SSMS для создания запросов к базам данных и хранилищам данных, их проектирования и управления ими, где бы они ни находились: на локальном компьютере или в облаке.

SSMS распространяется бесплатно!

## <a name="download-ssms-182"></a>Скачать SSMS 18.2

**Вышла версия SSMS 18.2. Это новейшая общедоступная версия *SQL Server Management Studio* с поддержкой [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]!**

**[![скачать](../ssdt/media/download.png) Скачать SQL Server Management Studio 18.2](https://go.microsoft.com/fwlink/?linkid=2099720)**

SSMS 18.2 является последней общедоступной версией SSMS. Если у вас установлена предыдущая общедоступная версия SSMS 18, при установке SSMS 18.2 она обновляется до версии 18.2. Если у вас установлена предыдущая *предварительная версия* SSMS 18.x, перед установкой SSMS 18.2 ее необходимо удалить.

**Сведения о версии**

- Номер выпуска: 18.2  
- Номер сборки: 15.0.18142.0  
- Дата выпуска: 25 июля 2019 г.  

Если у вас есть замечания или предложения или вы хотите сообщить о проблеме, обратитесь к группе SSMS на [UserVoice](https://aka.ms/sqlfeedback).

При установке SSMS 18.x не обновляются и не заменяются версии SSMS 17.x или более ранние. Среда SSMS 18.x устанавливается параллельно с предыдущими версиями, и обе версии остаются доступными для использования.

Если на компьютере есть несколько параллельных установок SSMS, следует всегда проверять, правильную ли версию вы запускаете. Последняя версия называется **Microsoft SQL Server Management Studio 18**.

## <a name="available-languages-ssms-182"></a>Доступные языки (SSMS 18.2)

Этот выпуск SSMS можно установить на следующих языках.

SQL Server Management Studio 18.2:  
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2099720&clcid=0x40a)

> [!NOTE]
> Модуль SQL Server PowerShell устанавливается отдельно из коллекции PowerShell. Дополнительные сведения см. в статье [Загрузка модуля PowerShell (SQL Server)](download-sql-server-ps-module.md).

## <a name="new-in-this-release-ssms-182"></a>Новые возможности в этом выпуске (SSMS 18.2)

|  Добавления  |  Сведения  |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Always Encrypted | Обновлен поставщик анклава для поддержки аттестации Azure. |
| Редактор и IntelliSense | Добавлена поддержка классификации данных  |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Диалоговое окно индекса SSMS — добавлен новый параметр индекса OPTIMIZE_FOR_SEQUENTIAL_KEY |
| OPTIMIZE_FOR_SEQUENTIAL_KEY | Добавлена поддержка IntelliSense |
| Выполнение запроса или результаты | Добавлено "Время завершения" в сообщениях для отслеживания завершения запросов. |
| Выполнение запроса или результаты  | Разрешено отображение дополнительных данных (результат в тексте) и их сохранение в ячейках (результат в сетке). Теперь SSMS допускает до 2 млн символов для обоих вариантов (начиная с 256 и 64 тыс. соответственно). Это также устраняет проблему, из-за которой пользователи не могут получить более 43 680 символов из ячеек сетки. |
| Инструкция ShowPlan | Добавлен новый атрибут в QueryPlan, когда включена встроенная скалярная функция UDF (ContainsInlineScalarTsqlUdfs). |
| Службы Integration Services (SSIS) | Оптимизация производительности для планировщика пакетов служб SSIS в Azure |
|  |  |

Дополнительные сведения о новых возможностях в этом выпуске см. в [заметках о выпуске SSMS](release-notes-ssms.md).

## <a name="supported-sql-offerings-ssms-182"></a>Поддерживаемые предложения SQL (SSMS 18.2)

* Эта версия SSMS работает со всеми [поддерживаемыми версиями SQL Server 2008–[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) и предоставляет превосходную поддержку новейших облачных функций базы данных SQL Azure и хранилища данных SQL Azure.
* Кроме того, SSMS 18.x можно установить одновременно с SSMS 17.x, SSMS 16.x или SQL Server 2014 и более ранними версиями.
* Службы SQL Server Integration Services (SSIS) — среда SSMS версии 17.x и более поздней не поддерживает подключение к устаревшим службам SQL Server Integration Services. Для подключения к более ранней версии служб Integration Services используйте соответствующую версию SSMS. Например, используйте SSMS 16.x для подключения к службам SQL Server 2016 Integration Services. Версии SSMS 17.x и SSMS 16.x можно установить параллельно на одном компьютере. Начиная с выпуска SQL Server 2012 база данных каталога SSIS (SSISDB) является рекомендуемым средством для хранения, выполнения и мониторинга пакетов служб Integration Services, а также управления ими. Дополнительные сведения см. в разделе [Каталог служб SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-182"></a>Поддерживаемые операционные системы (SSMS 18.2)

При использовании последнего пакета обновления этот выпуск SSMS поддерживает следующие 64-разрядные платформы:

- Windows 10 (64-разрядная) <sup>*</sup>
- Windows 8.1 (64-разрядная)
- Windows Server 2019 (64-разрядная версия)
- Windows Server 2016 (64-разрядная версия) <sup>*</sup>
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

<sup>*</sup> Требуется версия 1607 (10.0.14393) или более поздняя

> [!NOTE]
> SSMS работает только на Windows. Если вам требуется средство, которое работает на платформах, отличных от Windows, рассмотрите Azure Data Studio. Azure Data Studio — это новое кроссплатформенное средство для macOS, Linux, а также Windows. Дополнительные сведения см. в разделе [Azure Data Studio](../azure-data-studio/what-is.md).

## <a name="release-notes-ssms-182"></a>Заметки о выпуске (SSMS 18.2)

В этом выпуске есть несколько [известных проблем](release-notes-ssms.md#known-issues-181).

Дополнительные сведения об этом выпуске см. в [заметках о выпуске SSMS](release-notes-ssms.md).

## <a name="previous-ssms-releases"></a>Предыдущие выпуски SSMS

[Предыдущие выпуски SQL Server Management Studio](../ssms/release-notes-ssms.md#previous-ssms-releases)

[!INCLUDE[get-help-sql-tools](../includes/paragraph-content/get-help-sql-tools.md)]

## <a name="see-also"></a>См. также раздел

- [Учебник. SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Документация по SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
