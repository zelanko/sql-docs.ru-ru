---
title: "Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
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
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 3f12671ace99d5fefc199c7b1c2db31e5b3cfade
ms.openlocfilehash: a689293fadb1a442f94d88cc06a9e7a4ef06650f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/08/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)

SQL Server Management Studio (SSMS) — это интегрированная среда для управления любой инфраструктурой SQL: от SQL Server до Базы данных SQL. SSMS предоставляет средства для настройки, наблюдения и администрирования экземпляров SQL. С помощью SSMS можно развертывать, отслеживать и обновлять компоненты уровня данных, используемые вашими приложениями, а также создавать запросы и скрипты.

Используйте SQL Server Management Studio (SSMS) для создания запросов к базам данных и хранилищам данных, их проектирования и управления ими, где бы они ни находились: на локальном компьютере или в облаке.

**SSMS распространяется бесплатно!**

SSMS 17.x — последняя версия *SQL Server Management Studio*, которая поддерживает SQL Server 2017.

**[![скачать](../ssdt/media/download.png) Скачать SQL Server Management Studio 17.2](https://go.microsoft.com/fwlink/?linkid=854085)**

**[![скачать](../ssdt/media/download.png) Скачать пакет обновления SQL Server Management Studio 17.2 (обновление с версии 17.x до версии 17.2)](https://go.microsoft.com/fwlink/?linkid=854087)**

При установке SSMS 17.x не обновляются и не заменяются версии SSMS 16.x или более ранние. Среда SSMS 17.x устанавливается параллельно с предыдущими версиями, и обе версии остаются доступными для использования.
Если на компьютере есть несколько параллельных установок SSMS, всегда проверяйте, правильную ли версию вы запускаете. Последняя версия называется *Microsoft SQL Server Management Studio 17* и имеет новый значок: 
 
   ![SSMS 17.x](media/download-sql-server-management-studio-ssms/version-icons.png)


> [!NOTE]
> Модуль PowerShell для SQL Server теперь устанавливается отдельно, из коллекции PowerShell.  Дополнительные сведения см. в [инструкциях по скачиванию](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio

**Сведения о версии**

Номер выпуска: 17.2. Номер сборки для этого выпуска: 14.0.17177.0.

## <a name="new-in-this-release"></a>Новое в данном выпуске

SSMS 17.2 — это последняя версия SQL Server Management Studio. Поколение 17.x среды SSMS поддерживает почти все функциональные возможности выпусков SQL Server 2008 — SQL Server 2017. Версия 17.x также поддерживает SQL Analysis Services в режиме PaaS.

Версия 17.2 включает в себя перечисленные ниже возможности.

- Многофакторная идентификация (MFA)
  - Проверка подлинности нескольких пользователей Azure AD с помощью универсальной проверки подлинности с Многофакторной идентификацией (MFA)
  - Было добавлено новое поле ввода учетных данных пользователей для поддержки проверки подлинности нескольких пользователей с помощью универсальной проверки подлинности с Многофакторной идентификацией.
- Диалоговое окно подключения теперь поддерживает следующие 5 способов проверки подлинности:
  - Проверка подлинности Windows.
  - Проверка подлинности SQL Server
  - Active Directory — универсальная с поддержкой MFA
  - Active Directory — пароль
  - Active Directory — встроенная

- При импорте и экспорте базы данных для мастера DacFx теперь можно использовать универсальную проверку подлинности с MFA.
- Сведения о поддержке API см. в описании [интерфейса IUniversalAuthProvider](https://msdn.microsoft.com/library/microsoft.sqlserver.dac.iuniversalauthprovider.aspx).
- Управляемая библиотека ADAL, используемая для универсальной проверки подлинности Azure AD с MFA, обновлена до версии 3.13.9.
- Реализован новый интерфейс командной строки (CLI) с поддержкой параметров администрирования Azure AD для Базы данных SQL и хранилища данных SQL.

 Дополнительные сведения о способах проверки подлинности Active Directory см. в статьях [Универсальная проверка подлинности для Базы данных SQL и хранилища данных SQL (поддержка SSMS для MFA)](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication) и [Настройка Многофакторной идентификации Базы данных SQL Azure для SQL Server Management Studio](https://docs.microsoft.com/azure/sql-database/sql-database-ssms-mfa-authentication-configure).

- В окне вывода приводятся записи, связанные с запросами, которые выполнялись во время развертывания узлов обозревателя объектов.
- Включен конструктор представлений для Баз данных SQL Azure.
- Изменились параметры скриптов для объектов в обозревателе объектов SQL Server Management Studio.
  - Ранее после первоначальной установки создаваемые скрипты по умолчанию предназначались для последней версии SQL Server (в настоящее время это версия SQL Server 2017).
  - В SQL Server Management Studio 17.2 был добавлен новый параметр: *Использовать параметры сценариев согласно источнику*. Если он имеет значение *Истина*, создаваемый скрипт будет предназначен для той же версии, типа ядра и выпуска ядра, которые используются на сервере, где находится объект, для которого создается скрипт.
  - Параметр *Использовать параметры сценариев согласно источнику* имеет значение *Истина* по умолчанию, поэтому в новой установке SQL Server Management Studio скрипты объектов будут автоматически создаваться для того же целевого ядра, что и на исходном сервере.
  - Если присвоить параметру *Использовать параметры сценариев согласно источнику* значение *Ложь*, будут использоваться обычные, то есть использовавшиеся ранее параметры назначения скриптов.
  - Кроме того, все параметры написания скриптов были перемещены в отдельный раздел *Параметры версий*. Они больше не приводятся в разделе *Общие параметры скрипта*.

- Добавлена поддержка национальных облаков при восстановлении по URL-адресу.
- Отчеты QueryStoreUI теперь поддерживают дополнительные метрики (число строк, DOP, время CLR и другие) из sys.query_store_runtime_stats.
- Технология IntelliSense теперь поддерживается для Базы данных SQL Azure.
    - https://connect.microsoft.com/SQLServer/feedback/details/3100677/ssms-2016-would-be-nice-to-have-intellisense-on-azure-sql-databases
- Безопасность: в диалоговом окне подключения по умолчанию отключено доверие к сертификатам сервера и включен запрос шифрования для подключений к Базе данных SQL Azure.
- Общие усовершенствования, касающиеся поддержки SQL Server в Linux:
 - Снова появился узел компонента Database Mail.
 - Устранены некоторые проблемы, связанные с путями.
 - Повышена стабильность работы монитора активности.
 - В диалоговом окне "Свойства соединения" правильно указывается платформа.
- Отчет панели мониторинга производительности по серверу теперь доступен как отчет по умолчанию.
  - Возможность подключения к SQL Server 2008 и более поздним версиям.
  - Во вложенном отчете об отсутствующих индексах используются оценки, которые помогают определять наиболее полезные индексы.
  - В историческом вложенном отчете по статистике ожидания операции ожидания теперь объединяются по категориям. Ожидания в режиме простоя или спящем режиме по умолчанию отфильтровываются.
  - Новый исторический вложенный отчет о кратковременных блокировках.
- В узле showplan можно выполнять поиск по свойствам плана. Вы можете легко находить любое свойство оператора, например имя таблицы. Чтобы использовать эту возможность при просмотре плана, выполните одно из указанных ниже действий.
  - Щелкните план правой кнопкой мыши, а затем в контекстном меню выберите пункт "Найти узел".
  - Нажмите клавиши CTRL+F.

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

SQL Server Management Studio 17.2:<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=854085&clcid=0x40a)

SQL Server Management Studio 17.2 (обновление с версии 17.x до версии 17.2):<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=854087&clcid=0x40a)

## <a name="release-notes"></a>Заметки о выпуске

Ниже перечислены проблемы и ограничения, имеющиеся в выпуске 17.2.

- В окнах запросов, в которых используется проверка подлинности "Active Directory — универсальная с поддержкой MFA", может возникать ошибка наподобие следующей при попытке выполнить запрос после того, как окно было открыто в течение часа или больше:

   `Msg 0, Level 11, State 0, Line 0
The connection is broken and recovery is not possible. The client driver attempted to recover the connection one or more times and all attempts failed. Increase the value of *ConnectRetryCount* to increase the number of recovery attempts.`

   При повторном выполнении запроса эта ошибка возникать не должна.

- При использовании в Azure AD универсальной проверки подлинности с MFA перечисленные ниже функциональные возможности SSMS не поддерживаются.
  - В конструкторе **новой таблицы или представления** выводится запрос на вход в старом стиле и не поддерживается проверка подлинности Azure AD.
  - Функция **Изменить первые 200 строк** не поддерживает проверку подлинности Azure AD.
  - Компонент **Зарегистрированный сервер** не поддерживает проверку подлинности Azure AD.
  - **Помощник по настройке ядра СУБД** не поддерживает проверку подлинности Azure AD. Имеется известная проблема, вследствие которой пользователю выводится сообщение об ошибке *Не удалось загрузить файл или сборку Microsoft.IdentityModel.Clients.ActiveDirectory…* вместо правильного сообщения *Помощник по настройке ядра СУБД не поддерживает Базу данных SQL Microsoft Azure. (DTAClient)*.

**Службы Analysis Services**

- В обозревателе объектов SSAS не отображается имя пользователя для проверки подлинности Windows в свойствах подключения Analysis Services Azure.
Дополнительные сведения см. в [журнале изменений SSMS](sql-server-management-studio-changelog-ssms.md).

## <a name="previous-releases"></a>Предыдущие выпуски

[Предыдущие выпуски SQL Server Management Studio](../ssms/sql-server-management-studio-changelog-ssms.md#previous-ssms-releases)

## <a name="feedback"></a>Отзывы

![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)

## <a name="see-also"></a>См. также:

- [Руководство: SQL Server Management Studio](tutorials/tutorial-sql-server-management-studio.md)
- [Документация по SQL Server Management Studio](sql-server-management-studio-ssms.md)
- [Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)
- [Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)

