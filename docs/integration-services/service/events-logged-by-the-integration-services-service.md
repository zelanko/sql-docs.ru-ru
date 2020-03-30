---
title: События, регистрируемые службами Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], events
- events [Integration Services], service
- Integration Services service, events
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8b2f033557c566050dffbd82bc64df84feabb7b6
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71296931"
---
# <a name="events-logged-by-the-integration-services-service"></a>Cобытия, зарегистрированные службами Integration Services

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] регистрирует различные сообщения в журнале событий приложений Windows. Служба записывает эти события в журнал при своем запуске, остановке и при возникновении некоторых проблем.  
  
 В этом разделе представлены сведения о самых распространенных сообщениях о событиях, которые регистрирует служба в журнале событий приложений. Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] регистрирует все сообщения, описанные в этом разделе, вместе с источником событий SQLISService.  
  
 Дополнительные сведения о службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Службы Integration Services (службы SSIS)](../../integration-services/service/integration-services-service-ssis-service.md).  
  
## <a name="service-status-messages"></a>Сообщения о состоянии службы
 При выборе установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливается и запускается, а тип ее запуска устанавливается в автоматический.  
  
|Идентификатор события|Символическое имя|текст|Примечания|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|Запуск службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)].|Служба запускается.|  
|257|DTS_MSG_SERVER_STARTED|Служба [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] запущена.|Служба запущена.|  
|260|DTS_MSG_SERVER_START_FAILED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Не удалось запустить службу.%nОшибка: %1|Не удалось запустить службу. Невозможность запуска может быть вызвана поврежденной установкой или недопустимой учетной записью службы.|  
|258|DTS_MSG_SERVER_STOPPING|Остановка службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)].%n%nПри выходе остановить все выполняющиеся пакеты: %1|Служба остановлена, а при соответствующей настройке она остановит все выполняющиеся пакеты. В файле конфигурации можно указать значения true или false, определяющие, будет ли служба останавливать все выполняющиеся пакеты при собственной остановке. Сообщение для этого события содержит значение соответствующего параметра.|  
|259|DTS_MSG_SERVER_STOPPED|Служба [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] остановлена.%nВерсия сервера %1|Служба остановлена.|  
  
## <a name="settings-file-messages"></a>Сообщения в файле параметров  
 Параметры службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] хранятся в XML-файле, который можно изменять. Дополнительные сведения см. в разделе [Службы Integration Services (SSIS)](../../integration-services/service/integration-services-service-ssis-service.md).  
  
|Идентификатор события|Символическое имя|текст|Примечания|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|Служба [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]: %nПараметр реестра, определяющий файл конфигурации, не существует. %nпопытка загрузки файла конфигурации по умолчанию.|Не существует записи реестра, содержащей путь к файлу конфигурации, или этот путь пустой.|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|Файл конфигурации службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] не существует.%nПроизводится загрузка с установками по умолчанию.|В заданном расположении отсутствует файл конфигурации.|  
|273|DTS_MSG_SERVER_BAD_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]Неверный файл конфигурации службы.%nОшибка чтения файла конфигурации: %1%n%nПроизводится загрузка сервера с установками по умолчанию.|Не удалось считать файл конфигурации, или он недопустим. Эта ошибка может быть результатом ошибки синтаксиса XML в файле.|  
  
## <a name="other-messages"></a>Другие сообщения  
  
|Идентификатор события|Символическое имя|текст|Примечания|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)]: остановка выполняющегося пакета.%nИдентификатор экземпляра пакета: %1%nИдентификатор пакета: %2%nИмя пакета: %3%nОписание пакета: %4%nПакет|Служба пытается остановить выполнение пакета. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]можно вести наблюдение и останавливать выполнение пакетов. Сведения об управлении пакетами в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] см. в разделе [Управление пакетами (службы SSIS)](../../integration-services/service/package-management-ssis-service.md).|  

## <a name="view-events"></a>Просмотр событий
  Для просмотра событий в службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] предусмотрены два средства.  
  
-   Диалоговое окно **Средство просмотра журнала** в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Диалоговое окно **Средство просмотра журнала** имеет возможности экспорта, фильтрации, а также поиска по журналу. Дополнительные сведения о параметрах в окне **Средство просмотра журнала**см. в разделе [Справка средства просмотра журнала F1](../../relational-databases/logs/log-file-viewer-f1-help.md).  
  
-   Средство просмотра событий Windows.  
  
 Описание событий, записываемых в журнал службой [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , см. в разделе [События, зарегистрированные службами Integration Services](../../integration-services/service/events-logged-by-the-integration-services-service.md).  
  
### <a name="to-view-service-events-for-integration-services-in-sql-server-management-studio"></a>Просмотр событий службы, относящихся к службам Integration Services, в среде SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
2.  В меню **Файл** выберите пункт **Подключить к обозревателю объектов**.  
  
3.  В диалоговом окне **Соединение с сервером** , выберите тип сервера служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , выберите или укажите нахождение сервера для соединения, затем нажмите **Подключить**.  
  
4.  Находясь в обозревателе объектов, щелкните правой кнопкой мыши службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , затем выберите пункт **Просмотр журналов**.  
  
5.  Для просмотра событий служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] выберите **Службы SQL Server Integration Services**. Параметр **События NT** автоматически включается и отключается параметром **Службы SQL Server Integration Services** .  
  
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
 
## <a name="related-tasks"></a>Связанные задачи  
 Сведения о просмотре записей журнала см. в разделе [Регистрация событий в пакете служб Integration Services](../../integration-services/performance/events-logged-by-an-integration-services-package.md)  
