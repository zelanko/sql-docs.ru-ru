---
title: "просмотреть события службы Integration Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "события [службы Integration Services]"
  - "служба [службы Integration Services], события"
  - "Службы Integration Services, события"
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
caps.latest.revision: 21
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 21
---
# просмотреть события службы Integration Services
  Для просмотра событий в службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предусмотрены два средства.  
  
-   Диалоговое окно **Средство просмотра журнала** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Диалоговое окно **Средство просмотра журнала** имеет возможности экспорта, фильтрации, а также поиска по журналу. Дополнительные сведения о параметрах в окне **Средство просмотра журнала** см. в разделе [Справка средства просмотра журнала F1](../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
-   Средство просмотра событий Windows.  
  
 Описание событий, записываемых в журнал службой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], см. в разделе [События, зарегистрированные службами Integration Services](../../integration-services/service/events-logged-by-the-integration-services-service.md).  
  
### Просмотр событий службы, относящихся к службам Integration Services, в среде SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  В меню **Файл** выберите пункт **Подключить к обозревателю объектов**.  
  
3.  В диалоговом окне **Соединение с сервером** , выберите тип сервера служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выберите или укажите нахождение сервера для соединения, затем нажмите **Подключить**.  
  
4.  Находясь в обозревателе объектов, щелкните правой кнопкой мыши службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], затем выберите пункт **Просмотр журналов**.  
  
5.  Для просмотра событий служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выберите **Службы SQL Server Integration Services**. Параметр **События NT** автоматически включается и отключается параметром **Службы SQL Server Integration Services** .  
  
### Просмотр событий службы, относящихся к службам Integration Services, в программе просмотра событий  
  
1.  При использовании классического вида **панели управления**щелкните **Администрирование**; если используется вид по категориям, щелкните **Производительность и обслуживание** , а затем **Администрирование**.  
  
2.  Щелкните **Просмотр событий**.  
  
3.  В диалоговом окне **Просмотр событий** выберите **Приложение**.  
  
4.  Найдите в столбце **Источник** оснастки **Приложение** запись со значением **SQLISService**, щелкните ее правой кнопкой мыши и выберите **Свойства**.  
  
5.  При необходимости щелкните стрелку вверх или вниз для просмотра предыдущего или следующего события.  
  
6.  При необходимости щелкните значок «Копировать в буфер обмена» для копирования сведений о событии.  
  
7.  Выберите отображение данных о событии при помощи байтов или слов.  
  
8.  Нажмите кнопку **ОК**.  
  
9. В меню **Консоль** выберите **Выход** для закрытия диалогового окна **Просмотр событий** .  
  
## См. также  
 [Управление службой Integration Services](../../integration-services/service/manage-the-integration-services-service.md)   
 [Добавление журнала для счетчиков производительности потока данных](../../integration-services/performance/add-a-log-for-data-flow-performance-counters.md)  
  
  