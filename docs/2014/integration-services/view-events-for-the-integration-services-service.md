---
title: Просмотреть события службы Integration Services | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- events [Integration Services]
- service [Integration Services], events
- Integration Services service, events
ms.assetid: 37e23946-10d1-4116-8568-8fd24067102e
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 24898f1b581b4a417c1ecb4f44ac5db08f11ce02
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096450"
---
# <a name="view-events-for-the-integration-services-service"></a>просмотреть события службы Integration Services
  Для просмотра событий в службе [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] предусмотрены два средства.  
  
-   Диалоговое окно **Средство просмотра журнала** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Диалоговое окно **Средство просмотра журнала** имеет возможности экспорта, фильтрации, а также поиска по журналу. Дополнительные сведения о параметрах в окне **Средство просмотра журнала**см. в разделе [Справка средства просмотра журнала F1](../relational-databases/logs/log-file-viewer-f1-help.md).  
  
-   Средство просмотра событий Windows.  
  
 Описание событий, записываемых в журнал службой [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , см. в разделе [События, зарегистрированные службами Integration Services](service/events-logged-by-the-integration-services-service.md).  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a>Просмотр событий службы, относящихся к службам Integration Services, в среде SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В меню **Файл** выберите пункт **Подключить к обозревателю объектов**.  
  
3.  В диалоговом окне **Соединение с сервером** , выберите тип сервера служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , выберите или укажите нахождение сервера для соединения, затем нажмите **Подключить**.  
  
4.  Находясь в обозревателе объектов, щелкните правой кнопкой мыши службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , затем выберите пункт **Просмотр журналов**.  
  
5.  Для просмотра событий служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] выберите **Службы SQL Server Integration Services**. Параметр **События NT** автоматически включается и отключается параметром **Службы SQL Server Integration Services** .  
  
### <a name="to-view-service-events-for-integration-services-in-windows-event-viewer"></a>Просмотр событий службы, относящихся к службам Integration Services, в программе просмотра событий  
  
1.  При использовании классического вида **панели управления**щелкните **Администрирование**; если используется вид по категориям, щелкните **Производительность и обслуживание** , а затем **Администрирование**.  
  
2.  Щелкните **Просмотр событий**.  
  
3.  В диалоговом окне **Просмотр событий** выберите **Приложение**.  
  
4.  Найдите в столбце **Источник** оснастки **Приложение** запись со значением **SQLISService**, щелкните ее правой кнопкой мыши и выберите **Свойства**.  
  
5.  При необходимости щелкните стрелку вверх или вниз для просмотра предыдущего или следующего события.  
  
6.  При необходимости щелкните значок «Копировать в буфер обмена» для копирования сведений о событии.  
  
7.  Выберите отображение данных о событии при помощи байтов или слов.  
  
8.  Нажмите кнопку **ОК**.  
  
9. В меню **Консоль** выберите **Выход** для закрытия диалогового окна **Просмотр событий** .  
  
## <a name="see-also"></a>См. также  
 [Управление службой Integration Services](../../2014/integration-services/manage-the-integration-services-service.md)   
 [Добавление журнала для счетчиков производительности потока данных](performance/performance-counters.md)  
  
  