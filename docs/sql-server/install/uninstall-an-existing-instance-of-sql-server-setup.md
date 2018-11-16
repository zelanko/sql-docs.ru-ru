---
title: Удаление существующего экземпляра SQL Server (программа установки) | Документация Майкрософт
ms.custom: ''
ms.date: 01/27/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- removing instances of SQL Server
- uninstalling instances of SQL Server
- removing SQL Server
- instances of SQL Server, uninstalling
- uninstalling SQL Server
ms.assetid: 3c64b29d-61d7-4b86-961c-0de62261c6a1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e9b113a9ef0ca0905fa90833a5c9568a9318834a
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51698820"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a>Удаление существующего экземпляра SQL Server (программа установки)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В данной статье описан процесс удаления изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Шаги, перечисленные в этой статье, помогут подготовить систему для повторной установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  >[!IMPORTANT]
  > Удаление экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]должно производиться локальным администратором, имеющим разрешение на вход в систему в качестве службы.  
  
 > [!NOTE]
 > Для удаления отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется функция удаления узла, предоставляемая программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которая удаляет каждый узел по отдельности. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../../sql-server/failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
 Перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]с помощью данной процедуры следует учесть следующие обстоятельства:  
  
-   Прежде чем производить удаление компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с компьютера, на котором установлен минимально необходимый объем оперативной памяти, необходимо удостовериться, что файл подкачки имеет достаточный размер. Он должен вдвое превышать размер физической памяти. Нехватка виртуальной памяти может привести к неполному удалению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Если существует несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет автоматически удален при удалении последнего экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
     Если необходимо удалить все компоненты [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо вручную удалить браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из списка **Программы и компоненты** в оснастке **Панель управления**.  
  
1.  При удалении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] удаляются файлы данных tempdb, добавленные во время процесса установки. Файлы с именем, удовлетворяющим шаблону tempdb_mssql_*.ndf, удаляются, если они существуют в каталоге системной базы данных.  
  
### <a name="before-you-uninstall"></a>Перед началом удаления  
  
1.  **Резервное копирование данных.** Хотя это не является обязательным действием, могут быть базы данных, которые нужно сохранить в текущем состоянии. Кроме того, может потребоваться сохранить изменения, внесенные в системные базы данных. В этих случаях перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]необходимо создать резервную копию данных. В качестве альтернативного решения можно сохранить копию файлов данных и файлов журналов в папке с именем, отличным от MSSQL. Папка MSSQL будет удалена в ходе удаления SQL Server.  
  
     Необходимо сохранить следующие файлы баз данных.  
  
    -   Master.mdf  
  
    -   Mastlog.ldf  
  
    -   Model.mdf  
  
    -   Modellog.ldf  
  
    -   Msdbdata.mdf  
  
    -   Msdblog.ldf  
  
    -   Mssqlsystemresource.mdf  
  
    -   Mssqlsustemresource.ldf  
  
    -   Tempdb.mdf  
  
    -   Templog.ldf  
  
    -   ReportServer[$ИмяЭкземпляра]\(база данных по умолчанию для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]).  
  
    -   ReportServer[$ИмяЭкземпляра]TempDB (временная база данных по умолчанию для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]).  
  
2.  **Удалите локальные группы безопасности.** Перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]удалите локальные группы безопасности для компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  **Остановите все** **службы[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].** Перед удалением компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рекомендуется остановить все службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Наличие активных соединений может помешать удалению компонентов.  
  
4.  **Выбор учетной записи с необходимыми разрешениями.** Выполните вход на сервер с учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или с учетной записью, обладающей аналогичным набором разрешений. Например, можно войти на сервер с учетной записью, входящей в локальную группу администраторов.  
  
### <a name="to-uninstall-an-instance-of-includessnoversionincludesssnoversion-mdmd"></a>To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Чтобы начать процесс удаления, перейдите на страницу **Панель управления** , а затем на страницу **Программы и компоненты**.  
  
2.  Щелкните правой кнопкой мыши пункт **SQL Server 2016** и выберите **Удалить**. Нажмите кнопку **Удалить**. Будет запущен мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Для проверки конфигурации компьютера будут выполнены правила поддержки установки. Чтобы продолжить, нажмите кнопку **Далее**.  
  
3.  На странице «Выбор экземпляра» воспользуйтесь раскрывающимся списком, чтобы указать удаляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , или укажите параметр для удаления только общих компонентов и средств управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы продолжить, нажмите кнопку **Далее**.  
  
4.  На странице «Выбор компонентов» укажите компоненты, которые нужно удалить из указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Для проверки успешного завершения операции запустятся правила удаления.  
  
5.  На странице **Все готово для удаления** просмотрите список компонентов и функций, подлежащих удалению. Нажмите кнопку **Удалить** , чтобы начать удаление  
  
6.  Сразу после удаления последнего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другие программы, связанные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , по-прежнему будут отображаться в списке программ на странице **Программы и компоненты**. Однако, если закрыть страницу **Установка и удаление программ**, при последующем открытии **Установка и удаление программ**список будет обновлен и будет содержать только установленные программы.  
  
### <a name="if-the-uninstallation-fails"></a>Если удаление не было выполнено успешно  
  
1.  Если процесс удаления не завершился успешно, попробуйте исправить проблему, вызвавшую сбой. В следующих статьях приводятся сведения, которые помогут понять причину неудавшегося удаления.  
  
    -   [Как определить проблемы установки SQL Server 2008, используя файлы журнала установки](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  Если вам не удалось исправить проблему, вы можете связаться с поддержкой [!INCLUDE[msCoName](../../includes/msconame-md.md)] . В некоторых случаях, например при неумышленном удалении важных файлов, перед переустановкой на компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потребоваться переустановка операционной системы.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
