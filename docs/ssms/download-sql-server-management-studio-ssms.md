---
title: Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт
ms.custom: ''
ms.date: 12/19/2018
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f186989b4b6edad18333bd93cc89a69c65c2a977
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590028"
---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

> [!div class="nextstepaction"]
> [Помогите улучшить документацию по SQL Server!](https://80s3ignv.optimalworkshop.com/optimalsort/36yyw5kq-0)

SQL Server Management Studio (SSMS) — это интегрированная среда для управления любой инфраструктурой SQL: от SQL Server до базы данных SQL Azure. SSMS предоставляет средства для настройки, наблюдения и администрирования экземпляров SQL. С помощью SSMS можно развертывать, отслеживать и обновлять компоненты уровня данных, используемые вашими приложениями, а также создавать запросы и скрипты.

Используйте SQL Server Management Studio (SSMS) для создания запросов к базам данных и хранилищам данных, их проектирования и управления ими, где бы они ни находились: на локальном компьютере или в облаке.

**SSMS распространяется бесплатно!**

**[Доступна общедоступная предварительная версия 6 SSMS 18.0](#ssms-180-preview-6). Это новейшее поколение *SQL Server Management Studio* с поддержкой [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]!**

## <a name="ssms-1791-is-the-current-general-availability-ga-version-of-ssms"></a>SSMS 17.9.1 является текущей общедоступной версией SSMS

**[![скачать](../ssdt/media/download.png) Скачать SQL Server Management Studio 17.9.1](https://go.microsoft.com/fwlink/?linkid=2043154)**
<br>**[![скачать](../ssdt/media/download.png) Скачать пакет обновления SQL Server Management Studio 17.9.1 (обновление с версии 17.x до 17.9.1)](https://go.microsoft.com/fwlink/?linkid=2043430)**

**Сведения о версии**

- Номер выпуска: 17.9.1<br>
- Номер сборки: 14.0.17289.0<br>
- Дата выпуска: 21 ноября 2018 г.

### <a name="available-languages-ssms-1791"></a>Доступные языки (SSMS 17.9.1)

> [!NOTE]
> При установке на следующие платформы для использования неанглоязычных локализованных выпусков SSMS 17.x требуется [обновление для системы безопасности KB 2862966](https://support.microsoft.com/kb/2862966): Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.

[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2043154&clcid=0x40a)

Дополнительные сведения о SSMS 17.9.1 см. в разделе [Журнал изменений SSMS 17.9.1](sql-server-management-studio-changelog-ssms.md#ssms-1791-latest-ga-release).

## <a name="ssms-installation-tips-and-issues-ssms-1791"></a>Советы по установке SSMS и связанные проблемы (SSMS 17.9.1)

### <a name="minimize-installation-reboots"></a>Минимизация перезагрузок при установке

* Выполните следующие действия, чтобы уменьшить вероятность того, что программе установки SSMS потребуется перезагрузка после установки:
  * Убедитесь, что используется последняя версия распространяемого пакета Visual C++ 2013. Требуется версия 12.0.40649.5 (или более поздняя). Нужна только 64-разрядная версия.
  * Убедитесь, что на компьютере используется платформа .NET Framework 4.6.1 (или более поздней версии).
  * Закройте все экземпляры Visual Studio, открытые на компьютере.
  * Убедитесь, что на компьютере установлены все последние обновления операционной системы.
  * Указанные действия обычно требуется выполнить всего один раз. В некоторых ситуациях перезагрузка необходима для дополнительных обновлений до того же основного номера версии SSMS. Все компоненты SSMS, необходимые для промежуточных обновлений, уже установлены на компьютере.

## <a name="ssms-180-preview-6"></a>SSMS 18.0 (предварительная версия 6)

**Доступна общедоступная предварительная версия 6 SSMS 18.0. Это новейшее поколение *SQL Server Management Studio* с поддержкой [!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]!**

**[![скачать](../ssdt/media/download.png) Скачать SQL Server Management Studio 18.0 (предварительная версия 6)](https://go.microsoft.com/fwlink/?linkid=2052501)**

*Предварительная версия 6* — это новейшая общедоступная предварительная версия SSMS 18.0. Если на компьютере установлена предыдущая предварительная версия SSMS 18.0, перед установкой предварительной версии 6 ее необходимо удалить.

**Сведения о версии**

- Номер выпуска: 18.0 (предварительная версия 6)<br>
- Номер сборки: 15.0.18075.0<br>
- Дата выпуска: 18 декабря 2018 г.

Если у вас есть замечания или предложения или вы хотите сообщить о проблеме, обратитесь к группе SSMS на [UserVoice](https://aka.ms/sqlfeedback).

При установке SSMS 18.x не обновляются и не заменяются версии SSMS 17.x или более ранние. Среда SSMS 18.x устанавливается параллельно с предыдущими версиями, и обе версии остаются доступными для использования.

Если на компьютере есть несколько параллельных установок SSMS, всегда проверяйте, правильную ли версию вы запускаете. Последняя версия называется *Microsoft SQL Server Management Studio 18*:
 

## <a name="available-languages-ssms-180-preview-6"></a>Доступные языки (SSMS 18.0, предварительная версия 6)

Этот выпуск SSMS можно установить на следующих языках.

SQL Server Management Studio 18.0 (предварительная версия 6):<br>
[Китайский (упрощенное письмо)](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x804) | [Китайский (традиционное письмо)](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=2052501&clcid=0x40a)

Пакет обновления SQL Server Management Studio 18.0 (обновление до версии 18.0):<br>
В настоящее время варианты обновления недоступны. Если на компьютере установлена предыдущая предварительная версия SSMS 18.0, перед установкой предварительной версии 6 ее необходимо удалить.

> [!NOTE]
> Модуль SQL Server PowerShell устанавливается отдельно из коллекции PowerShell. Дополнительные сведения см. в статье [Загрузка модуля PowerShell (SQL Server)](download-sql-server-ps-module.md).


## <a name="new-in-this-release-ssms-180-preview-6"></a>Новые возможности в этом выпуске (SSMS 18.0, предварительная версия 6)

SSMS 18.0 (предварительная версия 6) — это новейшая версия SQL Server Management Studio. Поколение 18.x среды SSMS поддерживает почти все функциональные возможности выпусков SQL Server 2008–SQL Server 2019 (предварительная версия).

Дополнительные сведения о новых возможностях в этом выпуске см. в разделе [Журнал изменений SSMS](sql-server-management-studio-changelog-ssms.md).


## <a name="supported-sql-offerings-ssms-180-preview-6"></a>Поддерживаемые предложения SQL (SSMS 18.0, предварительная версия 6)

* Эта версия SSMS работает со всеми [поддерживаемыми версиями SQL Server 2008–[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]](https://support.microsoft.com/lifecycle?C2=1044) и предоставляет превосходную поддержку новейших облачных функций базы данных SQL Azure и хранилища данных SQL Azure.
* Кроме того, SSMS 18.x можно установить одновременно с SSMS 17.x, SSMS 16.x или SQL Server 2014 и более ранними версиями.
* Службы SQL Server Integration Services (SSIS) — среда SSMS версии 17.x и более поздней не поддерживает подключение к устаревшим службам SQL Server Integration Services. Для подключения к более ранней версии служб Integration Services используйте соответствующую версию SSMS. Например, используйте SSMS 16.x для подключения к службам SQL Server 2016 Integration Services. Версии SSMS 17.x и SSMS 16.x можно установить параллельно на одном компьютере. Начиная с выпуска SQL Server 2012 база данных каталога SSIS (SSISDB) является рекомендуемым средством для хранения, выполнения и мониторинга пакетов служб Integration Services, а также управления ими. Дополнительные сведения см. в разделе [Каталог служб SSIS](../integration-services/catalog/ssis-catalog.md).

## <a name="supported-operating-systems-ssms-180-preview-6"></a>Поддерживаемые операционные системы (SSMS 18.0, предварительная версия 6)

При использовании последнего пакета обновления этот выпуск SSMS поддерживает следующие 64-разрядные платформы:

- Windows 10 (64-разрядная) *
- Windows Server 2016 *
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

\* Требуется версия 1607 (10.0.14939) или более поздняя

> [!NOTE]
> SSMS работает только на Windows. Если вам требуется средство, которое работает на платформах, отличных от Windows, рассмотрите Azure Data Studio. Azure Data Studio — это новое кроссплатформенное средство для macOS, Linux, а также Windows. Дополнительные сведения см. в разделе [Azure Data Studio](../azure-data-studio/what-is.md).
  



## <a name="release-notes-ssms-180-preview-6"></a>Заметки о выпуске (SSMS 18.0, предварительная версия 6)

Ниже приведены известные проблемы в SSMS 18.0 (предварительная версия 6).

SSMS

- При двойном щелчке на SQL-файле запускается SSMS, но не открывается скрипт.
  - Обходное решение: перетащите SQL-файл в редактор SSMS.



## <a name="previous-releases"></a>Предыдущие выпуски

[Предыдущие выпуски SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Отзывы

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [Форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools)

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

## <a name="see-also"></a>См. также:

- [Учебник. SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Документация по SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]

Если у вас есть замечания или предложения или вы хотите сообщить о проблеме, обратитесь к группе SSMS на [UserVoice](https://aka.ms/sqlfeedback).
