---
title: "Обновление пакетов служб Integration Services с помощью мастера обновления пакетов служб SSIS | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Integration Services packages, upgrading
- upgrading Integration Services packages
ms.assetid: 9359275a-48f5-4d1e-8ae7-e797759e3ccf
caps.latest.revision: "22"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ed130489c29f923be47677624b350cb5f6a8894a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard"></a>обновить пакеты служб Integration Services с помощью мастера обновления пакетов служб SSIS
  Пакеты, созданные в более ранних версиях служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , можно обновить до формата служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , используемых [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] . [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] . Мастер можно настроить так, что исходные пакеты останутся без изменений. Поэтому в случае каких-либо трудностей обновления можно продолжать использовать исходные пакеты.  
  
 Мастер миграции пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] устанавливается при установке служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
> [!NOTE]  
>  Мастер миграции пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] доступен в следующих выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: Standard, Enterprise, Developer.  
  
 Дополнительные сведения об обновлении пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Обновление пакетов служб Integration Services](../../integration-services/install-windows/upgrade-integration-services-packages.md).  
  
 В оставшейся части раздела описывается работа с мастером и создание резервных копий исходных пакетов.  
  
## <a name="running-the-ssis-package-upgrade-wizard"></a>Работа с мастером обновления пакетов служб SSIS  
 Мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] можно запустить из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]или из командной строки.  
  
#### <a name="to-run-the-wizard-from-sql-server-data-tools"></a>Запуск мастера из SQL Server Data Tools  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]создайте или откройте проект служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  Находясь в обозревателе решений, правой кнопкой мыши щелкните узел **Пакеты служб SSIS** и выберите команду **Обновить все пакеты** , чтобы обновить все пакеты, принадлежащие этому узлу.  
  
    > [!NOTE]  
    >  При открытии проекта служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , содержащего пакеты служб [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] или более поздней версии, службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] автоматически открывают мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
#### <a name="to-run-the-wizard-from-sql-server-management-studio"></a>Запуск мастера в среде SQL Server Management Studio  
  
-   В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к службам [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], разверните узел **Сохраненные пакеты** , щелкните правой кнопкой мыши узел **Файловая система** или узел **MSDB** и выберите пункт **Обновить пакеты**.  
  
#### <a name="to-run-the-wizard-at-the-command-prompt"></a>Запуск мастера из командной строки  
  
-   Из командной строки запустите файл SSISUpgrade.exe, расположенный в папке **C:\Program Files\Microsoft SQL Server\130\DTS\Binn** .  
  
## <a name="backing-up-the-original-packages"></a>Резервное копирование исходных пакетов  
 Чтобы создать резервные копии исходных пакетов перед их обновлением, исходные пакеты и обновленные пакеты должны храниться в той же папке файловой системы. В зависимости от способа запуска мастера, это место хранения может определяться автоматически.  
  
-   При запуске мастера обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] из среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]мастер автоматически сохраняет исходные и обновленные пакеты в одной папке файловой системы.  
  
-   При запуске мастера обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] из среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или из командной строки можно указать различное место хранения для первоначальных и обновленных пакетов. Чтобы мастер создавал резервные копии исходных пакетов, убедитесь, что исходные и обновленные пакеты хранятся в одной и той же папке файловой системы. Если задать другие параметры хранения, мастер не сможет создать резервные копии исходных пакетов.  
  
 Мастер будет создавать резервные копии исходных пакетов в папке **SSISBackupFolder** . Мастер создает папку **SSISBackupFolder** в папке, которая содержит исходные и обновленные пакеты.  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-management-studio-or-at-the-command-prompt"></a>Создание резервных копий исходных пакетов в среде SQL Server Management Studio или из командной строки  
  
1.  Сохраните исходные пакеты в папке файловой системы.  
  
    > [!NOTE]  
    >  Мастер может создавать резервные копии только для пакетов, хранящихся в файловой системе.  
  
2.  Запустите мастер обновления пакетов служб [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] из среды [!INCLUDE[ssIS](../../includes/ssis-md.md)] или из командной строки.  
  
3.  На странице **Выбор исходного расположения** мастера выберите для свойства **Источник пакета** значение **Файловая система**.  
  
4.  На странице **Выбор целевого расположения** мастера выберите **Сохранить в исходное расположение** , чтобы сохранить обновленные пакеты в ту же папку, где находятся исходные пакеты.  
  
    > [!NOTE]  
    >  Этот параметр становится доступен только в случае, когда исходные и обновленные пакеты хранятся в одной и той же папке.  
  
5.  На странице мастера **Выбор параметров управления пакетами** выберите параметр **Создать резервную копию исходных пакетов** .  
  
#### <a name="to-back-up-the-original-packages-in-sql-server-data-tools"></a>Резервное копирование исходных пакетов в SQL Server Data Tools  
  
1.  Сохраните исходные пакеты в папке файловой системы.  
  
2.  На странице мастера **Выбор параметров управления пакетами** выберите параметр **Создать резервную копию исходных пакетов** .  
  
    > [!WARNING]  
    >  При открытии проекта служб **или более поздней версии в среде** , которое автоматически запускает мастер, параметр [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] Создать резервную копию исходных пакетов [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]не отображается.  
  
3.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]запустите мастер обновления пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
  
