---
title: Настройка службы Integration Services в качестве ресурса кластера | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 367835aa-9855-4791-a989-b3d08402ad4c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 01d572424691ae14b8c75fa594327eef3fbd9504
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85434901"
---
# <a name="configure-the-integration-services-service-as-a-cluster-resource"></a>Настройка служб Integration Services на работу в качестве ресурса кластера
  Этот раздел содержит инструкции по настройке службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в качестве ресурса кластера, которые могут пригодиться клиентам, считающим, что преимущества данной конфигурации перевешивают ее недостатки. Тем не менее корпорация [!INCLUDE[msCoName](../includes/msconame-md.md)] не рекомендует настраивать службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в качестве ресурса кластера.  
  
 Чтобы настроить службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в качестве ресурса кластера, необходимо выполнить следующие действия.  
  
-   Установите в кластере службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
     Чтобы установить службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в кластере, следует установить [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на каждом узле в кластере.  
  
-   Настройте службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на работу в качестве ресурса кластера.  
  
     После того как службы Integration Services были установлены на все узлы в кластере, необходимо провести их настройку в качестве ресурса кластера. При настройке службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в качестве ресурса кластера, можно добавить эту службу в ту же группу ресурсов, что и компонент [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)], либо в другую группу. В следующей таблице приводятся возможные преимущества и недостатки для разных вариантов выбора группы ресурсов.  
  
    |Службы Integration Services и SQL Server находятся в одной группе ресурсов|Службы Integration Services и SQL Server находятся в разных группах ресурсов|  
    |-----------------------------------------------------------------------------|-------------------------------------------------------------------------------|  
    |Клиентские компьютеры могут использовать среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] для управления пакетами, хранящимися в базе данных msdb, поскольку компонент [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] и служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] выполняются на одном виртуальном сервере. Такая конфигурация позволяет избежать проблем делегирования, возникающих в двухшаговом сценарии.|Среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] на клиентских компьютерах нельзя использовать для управления пакетами, хранящимися в базе данных msdb. Клиент может соединяться с виртуальным сервером, на котором запущены службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Однако этот компьютер не может делегировать учетные данные виртуальному серверу, на котором запущен [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Такой сценарий называется «двойным прыжком».|  
    |Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] конкурирует с другими службами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] за ресурсы ЦП и другие ресурсы.|Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не конкурирует с другими службами [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] за ресурсы ЦП и другие ресурсы, поскольку разные группы ресурсов установлены на разных узлах.|  
    |Загрузка и сохранение пакетов в базу данных msdb происходит быстрее и создает меньше сетевого трафика, поскольку обе службы выполняются на одном компьютере.|Загрузка и сохранение пакетов в базе данных msdb могут выполняться медленнее и создавать больший сетевой трафик.|  
    |Обе службы одновременно в сети или вне сети.|Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] может быть в сети в то время как компонент находится [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] вне сети. Вследствие этого пакеты, хранящиеся в базе данных msdb компонента [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] , будут недоступны.|  
    |Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не может быть быстро перенесена на другой узел при необходимости.|Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] при необходимости может быть быстрее перенесена на другой узел.|  
  
     После принятия решения относительно того, в какую группу ресурсов стоит добавить службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], необходимо настроить службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на работу в качестве ресурса кластера в этой группе.  
  
-   Настройте службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и хранилище пакетов.  
  
     После того как служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] была настроена на работу в качестве ресурса кластера, следует произвести изменение расположения и содержимого файла конфигурации службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на каждом узле в кластере. После этих изменений и файл конфигурации, и хранилище пакетов будут доступны для всех узлов при отработке отказа. После изменения расположения и содержимого файла конфигурации следует перевести службу в оперативный режим.  
  
-   Переведите службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в режим в сети в качестве ресурса кластера.  
  
 После настройки служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в кластере или на любом сервере может возникнуть необходимость настроить разрешения DCOM прежде, чем можно будет подключиться к службе с клиентского компьютера. Дополнительные сведения см. в разделе [Подключение к удаленному серверу служб Integration Services (службы SSIS Service)](../../2014/integration-services/connect-to-a-remote-integration-services-server-ssis-service.md).  
  
 Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не может делегировать учетные данные. Следовательно, нельзя использовать среду [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] для управления пакетами, хранящимися в базе данных msdb, в том случае, если выполняются следующие условия.  
  
-   Служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] выполняются на отдельных серверах или виртуальных серверах.  
  
-   Клиент, запускающий среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] , находится на третьем компьютером.  
  
 Клиент может соединяться с виртуальным сервером, на котором запущены службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Однако этот компьютер не может делегировать учетные данные виртуальному серверу, на котором запущен [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Такой сценарий называется «двойным прыжком».  
  
### <a name="to-install-integration-services-on-a-cluster"></a>Установка служб Integration Services на кластере  
  
1.  Установите и настройте кластер, содержащий один или несколько узлов.  
  
2.  Установите службы, поддерживающие работу в кластере, например компонент [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)](необязательно).  
  
3.  Установите службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] на каждом из узлов.  
  
### <a name="to-configure-integration-services-as-a-cluster-resource"></a>Настройка служб Integration Services в качестве ресурса кластера  
  
1.  Откройте **администратор кластера**.  
  
2.  В дереве консоли разверните папку «Группы».  
  
3.  На панели результатов выберите группу, к которой планируется добавить службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
    -   Чтобы добавить службу Integrations Services в качестве ресурса кластера в ту же группу ресурсов, что и [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выберите группу, к которой принадлежит [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
    -   Чтобы добавить службу Integrations Services в качестве ресурса кластера в группу ресурсов, в которую не входит [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выберите группу, к которой [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] не принадлежит.  
  
4.  В меню **Файл** выберите пункт **Создать**, а затем **Ресурс**.  
  
5.  На странице **Создание ресурса** в мастере ресурсов введите имя и выберите **тип службы** **"Общая служба"** . Не изменяйте значение поля **Группа**. Нажмите кнопку **Далее**.  
  
6.  На странице **Возможные владельцы** добавьте или удалите узлы кластера, которые являются возможными владельцами ресурса. Нажмите кнопку **Далее**.  
  
7.  Чтобы добавить зависимости на странице **Зависимости** , выберите ресурс в списке **Доступные ресурсы**, а затем нажмите **Добавить**. При отработке отказа как [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , так и общий диск, на котором сохраняются пакеты служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , должны быть переведены в режим "в сети" раньше, чем служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . После выбора зависимостей нажмите кнопку **Далее**.  
  
     Дополнительные сведения см. в разделе [Добавление зависимостей к ресурсу SQL Server](../sql-server/failover-clusters/windows/add-dependencies-to-a-sql-server-resource.md).  
  
8.  На странице **Общие параметры службы** введите в качестве имени службы значение **MsDtsServer** . Щелкните **Далее**.  
  
9. На странице **Репликация реестра** нажмите **Добавить** , чтобы добавить раздел реестра, который идентифицирует расположение файла конфигурации для службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Файл должен быть расположен на общем диске, находящемся в той же группе ресурсов, что и служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
10. В диалоговом окне **Раздел реестра** введите **SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS\ServiceConfigFile**. Нажмите кнопку **ОК**, а затем — кнопку **Готово**.  
  
     Теперь служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] добавлена как ресурс кластера.  
  
### <a name="to-configure-the-integration-services-service-and-package-store"></a>Настройка службы Integration Services и хранилища пакетов  
  
1.  Найдите файл конфигурации %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn\MsDtsSrvr.ini.xml. Скопируйте его на общий диск той группы, в которую была добавлена служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
2.  Создайте на общем диске новую папку с именем **Packages** , которая будет служить хранилищем пакетов. Предоставьте подходящим группам и пользователям разрешения на просмотр содержимого и на запись в созданную папку.  
  
3.  Откройте файл конфигурации с общего диска в редакторе текста или XML. Измените значение элемента `ServerName`, указав имя виртуального [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], относящегося к той же группе ресурсов.  
  
4.  Измените значение `StorePath` элемента на полный путь к папке **packages** , созданной на общем диске на предыдущем шаге.  
  
5.  Измените значение **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\100\SSIS\ServiceConfigFile** в реестре, указав полный путь и имя файла конфигурации службы на общем диске.  
  
### <a name="to-bring-the-integration-services-service-online"></a>Приведение службы Integration Services в режим в сети  
  
-   В **Администраторе кластера**выберите службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , щелкните ее правой кнопкой мыши и выберите из контекстного меню пункт **Перевести в режим "в сети"** . Теперь служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] доступна как ресурс кластера.  
  
  
