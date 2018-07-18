---
title: Задания агента SQL Server для пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- jobs [Integration Services]
- automatic package execution
- scheduling packages [Integration Services]
- SQL Server Agent [Integration Services]
ms.assetid: ecf7a5f9-b8a7-47f1-9ac0-bac07cb89e31
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9a49866dc625e45427566ebf33af6239dd067ce1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37330014"
---
# <a name="sql-server-agent-jobs-for-packages"></a>Пакеты служб из заданий агента SQL Server
  Выполнение пакетов служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] можно автоматизировать и запланировать в расписании при помощи агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Можно задать расписание выполнения пакетов, равернутых на сервере служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , хранимых в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], в хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , или в файловой системе.  
  
## <a name="sections-in-this-topic"></a>Подразделы данного раздела  
 Этот раздел состоит из следующих подразделов.  
  
-   [Планирование заданий в агенте SQL Server](#jobs)  
  
-   [Планирование пакетов служб Integration Services](#packages)  
  
-   [Устранение неполадок при работе с запланированным пакетами](#trouble)  
  
##  <a name="jobs"></a> Scheduling Jobs in SQL Server Agent  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — это устанавливаемая [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служба, которая позволяет автоматизировать задания и планировать их выполнение посредством запуска заданий агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для автоматического запуска заданий должна быть запущена служба агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Configure SQL Server Agent](../../ssms/agent/configure-sql-server-agent.md).  
  
 Узел **агента SQL Server** отображается в обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] при подключении к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
 Для автоматизации повторяющейся задачи необходимо создать задание в диалоговом окне **Создать задание** . Дополнительные сведения см. в разделе [Реализация заданий](../../ssms/agent/implement-jobs.md).  
  
 После создания задания необходимо добавить как минимум один шаг. Задание может содержать несколько шагов, причем на каждом из шагов могут решаться различные задачи. Дополнительные сведения см. в статье [Manage Job Steps](../../ssms/agent/manage-job-steps.md).  
  
 После создания задания и шагов задания можно создать расписание для его запуска. Однако можно создать и задание без расписания, которое будет запускаться вручную. Дополнительные сведения см. в разделе [Создание и присоединение расписаний к заданиям](../../ssms/agent/create-and-attach-schedules-to-jobs.md).  
  
 Можно добавить заданию некоторые функции уведомления, например, чтобы по окончании задания отправлялось сообщение по электронной почте определенному оператору, или выдавались какие-либо предупреждения. Дополнительные сведения см. в статье [Предупреждения](../../ssms/agent/alerts.md).  
  
##  <a name="packages"></a> Scheduling Integration Services Packages  
 После создания задания служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для планирования пакетов [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] необходимо добавить к нему хотя бы один шаг и задать для этого шага тип **Пакет SQL Server Integration Services**. Задание может содержать несколько шагов, причем на всех шагах могут выполняться различные пакеты.  
  
 Запуск пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] из шага задания аналогичен запуску пакета с помощью программ **dtexec** (dtexec.exe) и **DTExecUI** (dtexecui.exe). Вместо задания для пакета параметров времени выполнения с помощью параметров командной строки или из диалогового окна **Программа выполнения пакетов** они задаются в диалоговом окне **Создание шага задания** . Дополнительные сведения о параметрах запуска пакета см. в разделе [dtexec Utility](dtexec-utility.md).  
  
 Дополнительные сведения см. в разделе [Планирование пакета с помощью агента SQL Server](../schedule-a-package-by-using-sql-server-agent.md).  
  
 Видеоролик о том, как использовать агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для выполнения пакетов, см. на домашней странице [Как автоматизировать выполнение пакетов с помощью агента SQL Server (видеоматериал SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141771)в библиотеке MSDN.  
  
##  <a name="trouble"></a> Устранение неполадок  
 Возможна ситуация, когда шаг задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не сможет запустить пакет даже в случае успешного выполнения пакета в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или из командной строки. У этой проблемы есть несколько распространенных причин и несколько рекомендуемых решений. Для получения дополнительных сведений см. следующие ресурсы.  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] , [Пакет служб SSIS не выполняется при вызове пакета из шага задания агента SQL Server](http://support.microsoft.com/kb/918760)  
  
-   Видеоролик [Устранение неполадок. Выполнение пакетов с помощью агента SQL Server (видеоматериал SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141772)в библиотеке MSDN.  
  
 После того как шаг задания агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] успешно запустил пакет, выполнение пакета может завершиться ошибкой или пакет может быть выполнен успешно, но с непредвиденными результатами. Для устранения таких неполадок можно использовать следующие средства.  
  
-   Для пакетов, сохраненных в базе данных MSDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , хранилище пакетов служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] или в папке на локальном компьютере, можно использовать **Средство просмотра журнала** , а также любые журналы и отладочные файлы дампа, созданные во время выполнения пакета.  
  
     **Для использования средства просмотра журналов выполните следующие действия.**  
  
    1.  В обозревателе объектов щелкните правой кнопкой мыши задание агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и выберите **Просмотр журнала**.  
  
    2.  Найдите выполнение задания в поле **Сведения о файле журнала** с сообщением **Не удалось выполнить задание** в столбце **Сообщение** .  
  
    3.  Разверните узел задания и щелкните шаг задания для просмотра сведений сообщения в области под полем **Сведения о файле журнала** .  
  
-   Для пакетов, сохраненных в базе данных SSISDB, можно использовать **Средство просмотра журнала** , а также любые журналы и отладочные файлы дампа, созданные во время выполнения пакета. Кроме того, можно использовать отчеты для сервера служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
     **Для поиска сведений в отчетах по выполнению пакета, связанного с выполнением задания, выполните следующие действия.**  
  
    1.  Выполните описанные выше шаги, чтобы просмотреть сведения из сообщения для шага задания.  
  
    2.  Найдите идентификатор выполнения, указанный в сообщении.  
  
    3.  Разверните узел каталога служб Integration Services в обозревателе объектов.  
  
    4.  Щелкните правой кнопкой мыши «SSISDB», затем выберите «Отчеты», «Стандартные отчеты», «Все выполнения».  
  
    5.  В отчете **Все выполнения** найдите идентификатор выполнения в столбце **Идентификатор** . Щелкните **Общие сведения**, **Все сообщения**или **Производительность выполнения** , чтобы просмотреть сведения об этом выполнении пакета.  
  
         Дополнительные сведения об отчетах «Общие сведения», «Все сообщения» и «Производительность выполнения» см. в разделе [Reports for the Integration Services Server](../reports-for-the-integration-services-server.md).  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
-   Статья базы знаний [Пакет служб SSIS не выполняется при вызове пакета из шага задания агента SQL Server](http://support.microsoft.com/kb/918760)на веб-сайте [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
-   Видеоролик [Устранение неполадок. Выполнение пакетов с помощью агента SQL Server (видеоматериал SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141772)в библиотеке MSDN.  
  
-   Видеоролик [Как автоматизировать выполнение пакета с помощью агента SQL Server (видеоматериал SQL Server)](http://go.microsoft.com/fwlink/?LinkId=141771)в библиотеке MSDN.  
  
-   Техническая статья [Checking SQL Server Agent jobs using Windows PowerShell (на английском языке)](http://go.microsoft.com/fwlink/?LinkId=165675)на сайте mssqltips.com  
  
-   Техническая статья [Auto alert for SQL Agent jobs when they are enabled or disabled (на английском языке)](http://go.microsoft.com/fwlink/?LinkId=165676)на сайте mssqltips.com  
  
-   Запись в блоге [Настройка заданий агента SQL Server для записи в журнал событий Windows](http://go.microsoft.com/fwlink/?LinkId=220745)на сайте mssqltips.com.  
  
  
