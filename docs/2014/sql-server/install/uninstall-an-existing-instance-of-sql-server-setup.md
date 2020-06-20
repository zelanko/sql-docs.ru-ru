---
title: Удаление существующего экземпляра SQL Server (программа установки) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 35970f3a78cad4a17fcfdcfb2d7b9aa91c9dd6e7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85062430"
---
# <a name="uninstall-an-existing-instance-of-sql-server-setup"></a>Удаление существующего экземпляра SQL Server (программа установки)
  В данной статье описан процесс удаления изолированного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Шаги, перечисленные в этом разделе, помогут подготовить систему для повторной установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  Удаление экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]должно производиться локальным администратором, имеющим разрешение на вход в систему в качестве службы.  
  
> [!NOTE]  
>  Для удаления отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используется функция удаления узла, предоставляемая программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , которая удаляет каждый узел по отдельности. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](../failover-clusters/install/add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
 Перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью данной процедуры следует учесть следующие обстоятельства.  
  
-   Прежде чем производить удаление компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с компьютера, на котором установлен минимально необходимый объем оперативной памяти, необходимо удостовериться, что файл подкачки имеет достаточный размер. Он должен вдвое превышать размер физической памяти. Нехватка виртуальной памяти может привести к неполному удалению [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Если существует несколько экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет автоматически удален при удалении последнего экземпляра [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] .  
  
     Если необходимо удалить все компоненты [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], необходимо вручную удалить браузер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из списка **Программы и компоненты** в оснастке **Панель управления**.  
  
### <a name="before-you-uninstall"></a>Перед началом удаления  
  
1.  **Создайте резервную копию данных.** Хотя это не является обязательным действием, могут быть базы данных, которые нужно сохранить в текущем состоянии. Кроме того, может потребоваться сохранить изменения, внесенные в системные базы данных. В этих случаях перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]необходимо создать резервную копию данных. В качестве альтернативного решения можно сохранить копию файлов данных и файлов журналов в папке с именем, отличным от MSSQL. Папка MSSQL будет удалена в ходе удаления SQL Server.  
  
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
  
    -   `ReportServer[$InstanceName]`(Это [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] база данных по умолчанию.)  
  
    -   ReportServer[$ИмяЭкземпляра]TempDB (временная база данных по умолчанию для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] )  
  
2.  **Удалите локальные группы безопасности.** Перед удалением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]удалите локальные группы безопасности для компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
3.  **Остановите все**  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **службы**. Перед удалением компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рекомендуется остановить все службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Наличие активных соединений может помешать удалению компонентов.  
  
4.  **Выбор учетной записи с необходимыми разрешениями.** Выполните вход на сервер с учетной записью службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или с учетной записью, обладающей аналогичным набором разрешений. Например, можно войти на сервер с учетной записью, входящей в локальную группу администраторов.  
  
### <a name="to-uninstall-an-instance-of-ssnoversion"></a>To Uninstall an Instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
1.  Чтобы начать процесс удаления, перейдите на страницу **Панель управления** , а затем на страницу **Программы и компоненты**.  
  
2.  Щелкните правой кнопкой мыши **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]** и выберите **Удалить**. Нажмите кнопку **Удалить**. Будет запущен мастер установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
     Для проверки конфигурации компьютера будут выполнены правила поддержки установки. Чтобы продолжить, нажмите кнопку **Далее**.  
  
3.  На странице «Выбор экземпляра» воспользуйтесь раскрывающимся списком, чтобы указать удаляемый экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , или укажите параметр для удаления только общих компонентов и средств управления [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Чтобы продолжить, нажмите кнопку **Далее**.  
  
4.  На странице «Выбор компонентов» укажите компоненты, которые нужно удалить из указанного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
     Для проверки успешного завершения операции запустятся правила удаления.  
  
5.  На странице **Все готово** для удаления просмотрите список компонентов и функций, подлежащих удалению. Нажмите кнопку **Удалить** , чтобы начать удаление  
  
6.  Сразу после удаления последнего экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] другие программы, связанные с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , по-прежнему будут отображаться в списке программ на странице **Программы и компоненты**. Однако, если закрыть страницу **Установка и удаление программ**, при последующем открытии **Установка и удаление программ**список будет обновлен и будет содержать только установленные программы.  
  
### <a name="if-the-uninstallation-fails"></a>Если удаление не было выполнено успешно  
  
1.  Если процесс удаления не завершился успешно, попробуйте исправить проблему, вызвавшую сбой. В следующих статьях приводятся сведения, которые помогут понять причину неудавшегося удаления.  
  
    -   [Как определить проблемы установки SQL Server 2008, используя файлы журнала установки](https://support.microsoft.com/kb/955396/en-us)  
  
    -   [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
2.  Если вам не удалось исправить проблему, вы можете связаться с поддержкой [!INCLUDE[msCoName](../../includes/msconame-md.md)] . В некоторых случаях, например при неумышленном удалении важных файлов, перед переустановкой на компьютере [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может потребоваться переустановка операционной системы.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и чтение файлов журналов программы установки SQL Server](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
