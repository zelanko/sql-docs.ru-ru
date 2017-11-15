---
title: "Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт"
ms.custom: 
ms.date: 10/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установить SSMS, скачать SSMS, последняя версия SSMS"
- "Среда SQL Server Management Studio"
- ssms.exe
- sql man studio
- sql management studio
- "установка sql management studio"
- "скачать sql management studio"
- "ms sql management studio"
- "установить sql management studio"
- "скачать ssms"
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: "145"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Active
ms.openlocfilehash: 0c9f20a8c5f251728ce8050e9c6fc2cab4b55a55
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)

SQL Server Management Studio (SSMS) — это интегрированная среда для управления любой инфраструктурой SQL: от SQL Server до Базы данных SQL. SSMS предоставляет средства для настройки, наблюдения и администрирования экземпляров SQL. С помощью SSMS можно развертывать, отслеживать и обновлять компоненты уровня данных, используемые вашими приложениями, а также создавать запросы и скрипты.

Используйте SQL Server Management Studio (SSMS) для создания запросов к базам данных и хранилищам данных, их проектирования и управления ими, где бы они ни находились: на локальном компьютере или в облаке.

**SSMS распространяется бесплатно!**

SSMS 17.x — последняя версия *SQL Server Management Studio*, которая поддерживает SQL Server 2017.

**[![скачать](../ssdt/media/download.png) Скачать SQL Server Management Studio 17.3](https://go.microsoft.com/fwlink/?linkid=858904)**

**[![скачать](../ssdt/media/download.png) Скачать пакет обновления SQL Server Management Studio 17.3 (обновление с версии 17.x до 17.3)](https://go.microsoft.com/fwlink/?linkid=858906)**

При установке SSMS 17.x не обновляются и не заменяются версии SSMS 16.x или более ранние. Среда SSMS 17.x устанавливается параллельно с предыдущими версиями, и обе версии остаются доступными для использования.
Если на компьютере есть несколько параллельных установок SSMS, всегда проверяйте, правильную ли версию вы запускаете. Последняя версия называется *Microsoft SQL Server Management Studio 17* и имеет новый значок: 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Модуль PowerShell для SQL Server теперь устанавливается отдельно, из коллекции PowerShell.  Дополнительные сведения см. в [инструкциях по скачиванию](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio

**Сведения о версии**

Номер выпуска: 17.3

Номер сборки для этого выпуска: 14.0.17199.0

## <a name="new-in-this-release"></a>Новое в данном выпуске

SSMS 17.3 — это новейшая версия SQL Server Management Studio. Поколение 17.x среды SSMS поддерживает почти все функциональные возможности выпусков SQL Server 2008 — SQL Server 2017. Версия 17.x также поддерживает SQL Analysis Services в режиме PaaS.

Версия 17.3 включает следующее.

- Добавлен новый мастер импорта неструктурированных файлов, работающий на базе интеллектуальной платформы, которая упрощает процесс импорта CSV-файлов и не требует от пользователей многочисленных действий или специализированных знаний. Дополнительные сведения см. в разделе [Мастер импорта неструктурированных файлов в SQL](../relational-databases/import-export/import-flat-file-wizard.md).
- В обозреватель объектов добавлен узел XEvent Profiler. Дополнительные сведения см. в разделе [Использование SSMS XEvent Profiler](../relational-databases/extended-events/use-the-ssms-xe-profiler.md).
- Обновлена фильтрация и классификация ожиданий в отчете об истории ожиданий из панели мониторинга производительности.
- Добавлена проверка синтаксиса функции Predict.
- Добавлена проверка синтаксиса запросов в функции управления внешними библиотеками.
- Добавлена поддержка SMO для управления внешними библиотеками.
- Добавлена поддержка запуска PowerShell в окне "Зарегистрированные серверы" (требуется новый модуль PowerShell для SQL).
- AlwaysOn: добавлена [поддержка маршрутизации запросов только для чтения](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md) для групп доступности.
- Добавлена возможность отправлять в окно вывода данные трассировки по входам с использованием проверки подлинности "Active Directory — универсальная с поддержкой MFA". По умолчанию эта функция отключена, и ее нужно включить в параметрах пользователя, последовательно выбрав "Сервис" > "Параметры" > "Службы Azure" > "Облако Azure" > "Уровень трассировки для окна вывода ADAL". 
- Хранилище запросов 
  - Пользовательский интерфейс хранилища запросов доступен, даже когда служба QDS отключена, при условии, что она записала какие-либо данные.
  - Пользовательский интерфейс хранилища запросов теперь предоставляет классификацию ожиданий во всех существующих отчетах. За счет этого пользователям будут доступны сценарии "Топ ожидающих запросов" и многие другие.
- Включать заголовки параметров сценариев стало необязательно. По умолчанию эта возможность отключена, и ее можно включить в параметрах пользователя, последовательно выбрав "Сервис" > "Параметры" > "Обозреватель объектов SQL Server" > "Сценарии" > "Включить заголовок с параметрами сценариев". Это связано с [элементом Connect 3139199](https://connect.microsoft.com/SQLServer/feedback/details/3139199).
- Удалена фирменная символика "RC".

Полный список изменений см. в статье [Среда SQL Server Management Studio (SSMS) — журнал изменений](../ssms/sql-server-management-studio-changelog-ssms.md).

Дополнительные сведения о сборе пользовательских данных см. в разделе [Заявление о конфиденциальности SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx).

## <a name="supported-sql-offerings"></a>Поддерживаемые предложения SQL

* Эта версия SSMS работает со всеми [поддерживаемыми версиями SQL Server (SQL Server 2008 — SQL Server 2017)](https://support.microsoft.com/lifecycle?C2=1044) и предоставляет превосходную поддержку новейших облачных функций базы данных SQL Azure и хранилища данных SQL Azure.
* SQL Server 2000 или SQL Server 2005 напрямую не блокируются, однако некоторые функции могут работать неправильно.
* Кроме того, SSMS 17.X можно установить одновременно с SSMS 16.X или SQL Server 2014 SSMS и более ранними версиями.

## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы
  
При использовании последнего пакета обновления этот выпуск SSMS поддерживает следующие 64-разрядные платформы:
- Windows 10 (64-разрядная)
- Windows 8.1 (64-разрядная)
- Windows 8 (64-разрядная)
- Windows 7 с пакетом обновления 1 (64-разрядная)
- Windows Server 2016 *
- Windows Server 2012 R2 (64-разрядная версия)
- Windows Server 2012 (64-разрядная версия)
- Windows Server 2008 R2 (64-разрядная версия)

\* Среда SSMS 17.X основана на изолированной оболочке Visual Studio 2015, которая была выпущена до Windows Server 2016. Корпорация Майкрософт уделяет большое внимание совместимости приложений и гарантирует, что уже выпущенные приложения продолжат работать в последних выпусках Windows. Чтобы минимизировать проблемы с запуском SSMS в Windows Server 2016, убедитесь, что для SSMS установлены все последние обновления. При возникновении каких-либо проблем с SSMS в Windows Server 2016, обратитесь в службу поддержки. Служба поддержки определит, связана ли проблема с SSMS, с Visual Studio или с совместимостью SSMS и Windows. Затем ваш запрос будет перенаправлен соответствующей группе для дальнейшего изучения.

## <a name="ssms-installation-tips-and-issues"></a>Советы по установке SSMS и связанные с ней проблемы

### <a name="minimize-installation-reboots"></a>Минимизация перезагрузок при установке

* Выполните следующие действия, чтобы уменьшить вероятность того, что программе установки SSMS потребуется перезагрузка после установки:
  * Убедитесь, что используется последняя версия распространяемого пакета Visual C++ 2013. Требуется версия 12.00.40649.5 (или более поздняя). Нужна только 64-разрядная версия.
  * Убедитесь, что на компьютере используется платформа .NET Framework 4.6.1 (или более поздней версии).
  * Закройте все остальные экземпляры Visual Studio, открытые на компьютере.
  * Убедитесь, что на компьютере установлены все последние обновления операционной системы.
  * Указанные действия обычно требуется выполнить всего один раз. В некоторых ситуациях перезагрузка необходима для дополнительных обновлений до того же основного номера версии SSMS. Все необходимые компоненты SSMS для промежуточных обновлений уже будут установлены на компьютере.

* Ознакомиться со списком известных проблем и способами их обхода можно в статье [Заметки о выпуске SQL Server Management Studio](../ssms/sql-server-management-studio-release-notes.md)

## <a name="available-languages"></a>Доступные языки

> [!NOTE]
> При установке на следующие платформы для использования неанглоязычных локализованных выпусков SSMS требуется [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) : Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2.

Этот выпуск SSMS можно установить на следующих языках.

SQL Server Management Studio 17.3:<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=858904&clcid=0x40a)

Пакет обновления SQL Server Management Studio 17.3 (обновление с версии 17.x до 17.3):<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=858906&clcid=0x40a)

## <a name="release-notes"></a>Заметки о выпуске

Ниже перечислены проблемы и ограничения, имеющиеся в выпуске 17.3.

**Общие ошибки SSMS**

- При использовании универсальной многофакторной проверки подлинности в Azure AD следующие функциональные возможности SSMS не поддерживаются.
   - Для проверки подлинности Azure AD не поддерживается помощник по настройке ядра СУБД. Имеется известная проблема, когда пользователь получает довольно непонятное сообщение об ошибке "Не удалось загрузить файл или сборку Microsoft.IdentityModel.Clients.ActiveDirectory…" вместо ожидаемого сообщения "Помощник по настройке ядра СУБД не поддерживает базу данных SQL Microsoft Azure. (DTAClient)".
- При попытке проанализировать запрос в DTA появляется сообщение об ошибке "Объект должен реализовать IConvertible. (mscorlib)".
- В списке отчетов хранилища запросов из обозревателя объектов отсутствуют *Регрессионные запросы*.
   - Обходное решение: щелкните правой кнопкой мыши узел **Хранилище запросов** и выберите **Просмотр регрессионных запросов**.

**Integration Services (IS)**

- Для выполнения пакетов в Scale Out указан некорректный [путь_выполнения] в элементе [каталог].[сообщения_событий]. Путь [execution_path] начинается с "\Package", а не с имени объекта исполняемого файла пакета. При просмотре обзорного отчета по выполнению пакетов в SSMS ссылка "Путь выполнения" в обзоре выполнения не работает. Обходное решение: щелкните "Просмотреть сообщения" в обзорном отчете, чтобы проверить все сообщения событий.



## <a name="previous-releases"></a>Предыдущие выпуски

[Предыдущие выпуски SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Отзывы

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>См. также:

- [Руководство: SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Документация по SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)
