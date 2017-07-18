---
title: "Загрузка SQL Server Management Studio (SSMS) | Документация Майкрософт"
ms.custom: 
ms.date: 06/27/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "установить SSMS, скачать SSMS, последняя версия SSMS"
- SQL Server Management Studio
- ssms.exe
- sql man studio
- sql management studio
- "sql management studio установка"
- "скачать sql management studio"
- "ms sql management studio"
- "установить sql management studio"
- ssms download
- sql server ssms
- ssms express
ms.assetid: adafeeef-4255-4924-8042-02f503d599ca
caps.latest.revision: 145
author: stevestein
ms.author: sstein
manager: craigg
ms.translationtype: HT
ms.sourcegitcommit: 47182ebd082dfae0963d761e54c4045be927d627
ms.openlocfilehash: 8c43f57c6d40d3f2c29f220581dddcf74bf96287
ms.contentlocale: ru-ru
ms.lasthandoff: 07/11/2017

---
# <a name="download-sql-server-management-studio-ssms"></a>Скачивание SQL Server Management Studio (SSMS)
SQL Server Management Studio (SSMS) — это интегрированная среда для управления любой инфраструктурой SQL, от SQL Server до баз данных SQL. SSMS предоставляет инструменты для настройки, мониторинга и администрирования экземпляров SQL в месте их развертывания. С помощью SSMS вы можете развертывать, отслеживать и обновлять компоненты уровня данных, используемые вашими приложениями, а также создавать запросы и скрипты. 

В этом выпуске представлена улучшенная совместимость с предыдущими версиями SQL Server, отдельный веб-установщик и всплывающие уведомления в SSMS, сообщающие о выходе новых выпусков.  
  
![Скачать](../ssdt/media/download.png) SSMS можно совершенно бесплатно! **[Скачать SQL Server Management Studio 17.1](https://go.microsoft.com/fwlink/?linkid=849819)** SSMS 17.X — последняя версия SQL Server Management Studio, которая поддерживает SQL Server 2017. 

![скачать](../ssdt/media/download.png) **[Скачать пакет обновления SQL Server Management Studio 17.1 (обновление с версии 17.0 до версии 17.1)](https://go.microsoft.com/fwlink/?linkid=849821)**

> [!NOTE]
> Модуль PowerShell для SQL Server теперь устанавливается отдельно, из коллекции PowerShell.  Дополнительные сведения см. в [инструкциях по скачиванию](download-sql-server-ps-module.md).

## <a name="sql-server-management-studio"></a>Среда SQL Server Management Studio   
**Сведения о версии**  
  
Номер выпуска: 17.1  
Номер сборки для этого выпуска: 14.0.17119.0

## <a name="new-in-this-release"></a>Новое в данном выпуске  

SSMS 17.1 — первое обновление поколения 17.X среды SQL Server Management Studio.  Поколение 17.X поддерживает почти все функциональные возможности выпусков SQL Server 2008–SQL Server 2017.  Версия 17.X также поддерживает SQL Analysis Service PaaS.

Версия 17.1 включает:

* исправления нескольких ошибок, о которых сообщили пользователи; 
* новое средство управления масштабированием Integration Services.

Полный список изменений см. в разделе   
                [Среда SQL Server Management Studio (SSMS) — журнал изменений](../ssms/sql-server-management-studio-changelog-ssms.md)  
   
Дополнительные сведения о сборе данных об использовании см. в разделе   
                [Заявление о конфиденциальности SQL Server](http://www.microsoft.com/privacystatement/en-us/SQLServer/Default.aspx) 
  
## <a name="supported-sql-offerings"></a>Поддерживаемые предложения SQL
  
* Эта версия SSMS работает со всеми [поддерживаемыми версиями SQL Server (SQL Server 2008–SQL Server 2017)](https://support.microsoft.com/lifecycle?C2=1044) и предоставляет превосходную поддержку новейших облачных функций базы данных SQL Azure и хранилища данных SQL Azure.  
* SQL Server 2000 или SQL Server 2005 напрямую не блокируются, однако некоторые функции могут работать неправильно.  
* Кроме того, SSMS 17.X можно установить одновременно с SSMS 16.X или SQL Server 2014 SSMS и более ранними версиями. 
  
## <a name="supported-operating-systems"></a>Поддерживаемые операционные системы
  
При использовании последнего пакета обновления этот выпуск SSMS поддерживает следующие платформы:   
- Windows 10
- Windows 8.1
- Windows 8
- Windows 7 с пакетом обновления 1 (SP1)
- Windows Server 2016
- Windows Server 2012 (64-разрядная версия) 
- Windows Server 2012 R2 (64-разрядная версия) 
- Windows Server 2008 R2 (64-разрядная версия)  

>[!NOTE]
>SSMS 17.X основана на изолированной оболочке Visual Studio 2015, которая была выпущена до Windows Server 2016. Корпорация Майкрософт уделяет большое внимание совместимости приложений и гарантирует, что уже выпущенные приложения продолжат работать в последних выпусках Windows. Чтобы минимизировать проблемы с запуском SSMS в Windows Server 2016, убедитесь, что для SSMS установлены все последние обновления. При возникновении каких-либо проблем с SSMS в Windows Server 2016, обратитесь в службу поддержки. Служба поддержки определит, связана ли проблема с SSMS, с Visual Studio или с совместимостью SSMS и Windows. Затем ваш запрос будет перенаправлен соответствующей группе для дальнейшего изучения.

## <a name="ssms-installation-tips-and-issues"></a>Советы по установке SSMS и связанные с ней проблемы

>[!NOTE]
> Установка SSMS 17.x не обновляет и не заменяет предыдущие версии SSMS.  Среда SSMS 17.x устанавливается параллельно с предыдущими версиями, и обе версии остаются доступными для использования.
> Если на компьютере есть несколько параллельных установок SSMS, следует всегда проверять, правильную ли версию вы запускаете.
>  ![SSMS 17.x](media/ssms-start-menu.png)

**Минимизация перезагрузок при установке**
- Выполните следующие действия, чтобы уменьшить вероятность того, что программе установки SSMS потребуется перезагрузка после установки.
  - Убедитесь, что используется последняя версия распространяемого пакета Visual C++ 2013. Требуется версия 12.00.40649.5 (или более поздняя). Нужна только 64-разрядная версия.
  - Убедитесь, что на компьютере используется платформа .NET Framework 4.6.1 (или более поздней версии).
  - Закройте все остальные экземпляры Visual Studio, открытые на компьютере.
  - Убедитесь, что на компьютере установлены все последние обновления операционной системы.
  - Указанные действия обычно требуется выполнить всего один раз. В некоторых ситуациях перезагрузка необходима для дополнительных обновлений до того же основного номера версии SSMS. Все необходимые компоненты SSMS для промежуточных обновлений уже будут установлены на компьютере.

- Ознакомиться со списком известных проблем и способами их обхода можно в статье [Заметки о выпуске SQL Server Management Studio](../ssms/sql-server-management-studio-release-notes.md)

## <a name="available-languages"></a>Доступные языки  
> При установке на следующие платформы для использования неанглоязычных локализованных выпусков SSMS требуется [пакет обновления безопасности KB 2862966](https://support.microsoft.com/en-us/kb/2862966) : Windows 8, Windows 7, Windows Server 2012 и Windows Server 2008 R2. 
  
Этот выпуск SSMS можно установить на следующих языках.

SQL Server Management Studio 17.1:<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=849819&clcid=0x40a)

SQL Server Management Studio 17.1 (обновление с версии 17.0 до версии 17.1):<br>
[Китайский (КНР)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x804) | [Китайский (Тайвань)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x404) | [Английский (США)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x409) | [Французский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40c) | [Немецкий](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x407) | [Итальянский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x410) | [Японский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x411) | [Корейский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x412) | [Португальский (Бразилия)](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x416) | [Русский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x419) | [Испанский](https://go.microsoft.com/fwlink/?linkid=849821&clcid=0x40a)

## <a name="previous-releases"></a>Предыдущие выпуски  
[Предыдущие выпуски SQL Server Management Studio](../ssms/previous-sql-server-management-studio-releases.md)  
  
## <a name="feedback"></a>Отзывы  
  
![needhelp_person_icon](../ssms/media/needhelp_person_icon.png) [форум клиентских средств SQL](https://social.msdn.microsoft.com/Forums/en-US/home?forum=sqltools) |  [Опубликуйте информацию о проблеме или предложение на Microsoft Connect](https://connect.microsoft.com/SQLServer/Feedback)  
  
## <a name="see-also"></a>См. также  
[Руководство: SQL Server Management Studio](http://msdn.microsoft.com/en-us/d2bade70-07cf-4d94-b5d2-88aecb538ed1)  
[Документация по SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(v=sql.130).aspx)  
[Microsoft SQL Server](https://msdn.microsoft.com/library/bb545450.aspx)  
[Дополнительные обновления и пакеты обновления](https://technet.microsoft.com/sqlserver/ff803383.aspx)  
[Скачать SQL Server Data Tools (SSDT)](../ssdt/download-sql-server-data-tools-ssdt.md)  



