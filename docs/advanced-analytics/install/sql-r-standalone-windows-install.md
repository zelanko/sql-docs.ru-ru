---
title: "Установка SQL Server 2016 R Server (изолированный) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2018
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: r
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
caps.latest.revision: 
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.workload: On Demand
ms.openlocfilehash: 48f28b7a8d357e80e7defb6d6a8d446041380fbf
ms.sourcegitcommit: 8e897b44a98943dce0f7129b1c7c0e695949cc3b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/21/2018
---
# <a name="install-sql-server-2016-r-server-standalone"></a>Установка SQL Server 2016 R Server (изолированный)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

В этой статье описывается программа установки SQL Server 2016 позволяет установить автономную версию **сервера SQL Server 2016 R**. При наличии Enterprise Edition или Software Assurance, установка изолированный сервер R на рабочем сервере является бесплатной.

## <a name="bkmk_prereqs"> </a> Контрольный список действий перед установкой

SQL Server 2016 является обязательным. Если у вас есть 2017 г. SQL Server, установите [обучения машины 2017 г сервера SQL Server (автономный)](sql-machine-learning-standalone-windows-install.md) вместо него.

Если установлен любой из предыдущих версий средств Revolution Analytics или пакетов, сначала их необходимо удалить. 

## <a name="get-the-installation-media"></a>Получение установочного носителя

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> Требование для установки исправления 

Корпорация Майкрософт выявила проблему с определенной версией двоичных файлов среды выполнения Microsoft VC++ 2013, которые SQL Server устанавливает в качестве необходимого компонента. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server выполните инструкции, приведенные в [заметках о выпуске SQL Server](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch), чтобы узнать, требуется ли на вашем компьютере исправление для двоичных файлов среды выполнения VC.  

## <a name="run-setup"></a>Запуск программы установки

Для локальных установок необходимо запускать программу установки с правами администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.

1. Запустите мастер установки SQL Server 2016. Рекомендуется установить пакет обновления 1 или более поздней версии.

2. На **установки** щелкните **Установка нового R Server (автономный)**.
    
     ![Запустите программу установки отдельного сервера R](media/2016-setup-installation-rsvr.png "запустите программу установки отдельного сервера R")
    
3.  На странице **Выбор компонентов** уже должен быть выбран следующий параметр:
    
    **R Server (изолированный)**  
    
    ![Выбор для автономного сервера R компонентов](media/2016setup-rserver-features.png "Выбор для автономного сервера R компонентов")
    
    Все прочие параметры можно игнорировать. 
    
    > [!NOTE]
    > Следует избегать установки **Общие средства** при запуске программы установки на компьютере, где R Services уже установлен для анализа в базе данных SQL Server. Это создает повторяющиеся библиотеки.
    > 
    > В то время как R-скриптов, запускаемых на сервере SQL Server находятся под управлением SQL Server, так как не будет конфликтовать с память, занятая другими службами компонента database engine, изолированный сервер R нет такого ограничения и может повлиять на другие операции базы данных.
    > 
    > Мы рекомендуем установки R Server (изолированного) на компьютере, отличном от SQL Server R Services (в базе данных).

4.  Примите условия лицензии, чтобы скачать и установить Microsoft R Open. Когда кнопка **Принять** станет недоступна, можно нажать кнопку **Далее**.
    
    Установка этих компонентов, и все необходимые компоненты, которые могут понадобиться, может занять некоторое время.
    
5.  На странице **Все готово для установки** проверьте выбранные параметры и нажмите кнопку **Установить**.

## <a name="default-installation-folders"></a>Папки установки по умолчанию

При установке с помощью программы установки SQL Server R Server библиотек R устанавливаются в папки, связанные с версией SQL Server, которая использовалась для установки. В этой папке также будут найти образцы данных, документация для базовых пакетов R и документацию для средств R и среды выполнения.

Тем не менее если установлен Microsoft R Server с помощью отдельного установщика Windows (не программа установки SQL) или при обновлении с помощью отдельного установщика Windows, библиотеки R установлены в другую папку.

Несмотря на то, что не рекомендуется, если на одном компьютере также установлен экземпляр SQL Server со службами R Services (в базе данных), вторая копия библиотеки R и средства устанавливаются в другую папку.

В следующей таблице перечислены пути для каждой установки.

|Версия| Метод установки | Папка по умолчанию|
|----|----|----|
|R Server (Standalone) |Мастер установки SQL Server 2016|`C:\Program Files\Microsoft SQL Server\130\R_SERVER`|
|R Server (Standalone) |Автономный установщик Windows|`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Сервер машинного обучения (автономный) |  Мастер установки SQL Server 2017 г., с параметром языка R |`C:\Program Files\Microsoft SQL Server\140\R_SERVER`|
|Сервер машинного обучения (автономный) |  Мастер установки SQL Server 2017 г., с параметром языка Python |`C:\Program Files\Microsoft SQL Server\140\PYTHON_SERVER`|
|Сервер машинного обучения (автономный) |  Автономный установщик Windows |`C:\Program Files\Microsoft\R Server\R_SERVER`|
|Службы R (в базе данных) |Мастер установки SQL Server 2016|`C:\Program Files\Microsoft SQL Server\MSSQL13.<instance_name>\R_SERVICES`|
|Службы машинного обучения (в базе данных) |Мастер установки SQL Server 2017 г., с параметром языка R|`C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\R_SERVICES`  |
|Службы машинного обучения (в базе данных) |Мастер установки SQL Server 2017 г., с параметром языка Python| `C:\Program Files\Microsoft SQL Server\MSSQL14.<instance_name>\PYTHON_SERVICES` |

## <a name="development-tools"></a>Средства разработки

Разработки (IDE) не установлена как часть установки. Не требуются дополнительные средства, как все стандартные средства будут включены, будет предоставлено с распределением R или Python.

Рекомендуется сначала ознакомиться с новыми версиями [!INCLUDE[rsql_rtvs](../../includes/rsql-rtvs-md.md)] или [Python для Visual Studio](https://docs.microsoft.com/en-us/visualstudio/python/installing-python-support-in-visual-studio). Visual Studio поддерживает как R и Python, а также средства разработки баз данных, возможность подключения к SQL Server и средств бизнес-Аналитики. Тем не менее можно использовать любой предпочтительная среда разработки, включая RStudio.
  
## <a name="get-help"></a>Получить справку

Нужна помощь с установку или обновление? Ответы на часто задаваемые вопросы и известные проблемы см. в следующей статье:

* [Обновление и установка часто задаваемые вопросы — Machine Services обучения](../r/upgrade-and-installation-faq-sql-server-r-services.md)

Чтобы проверить состояние установки экземпляра и устранить распространенные проблемы, попробуйте следующие пользовательские отчеты.

* [Пользовательские отчеты для служб SQL Server R](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>Следующие шаги

Разработчики R можно начать работу с несколько простых примеров и основные сведения о работе с SQL Server R. Следующий шаг см. по следующим ссылкам:

+ [Учебник: Запускать в T-SQL](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md).
+ [Учебник: Анализ в базе данных для разработчиков R](../tutorials/sqldev-in-database-r-for-sql-developers.md)

Чтобы просмотреть примеры машинного обучения, основанные на реальных сценариев, в разделе [машинного обучения учебники](../tutorials/machine-learning-services-tutorials.md).

