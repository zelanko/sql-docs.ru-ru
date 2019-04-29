---
title: События, регистрируемые службами Integration Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- service [Integration Services], events
- events [Integration Services], service
- Integration Services service, events
ms.assetid: d4122dcf-f16f-47a0-93a2-ffa3d0d4f9cf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: dedffe0f30c62399e4d694f7ee1bf5247222e87d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889281"
---
# <a name="events-logged-by-the-integration-services-service"></a>Cобытия, зарегистрированные службами Integration Services
  Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] регистрирует различные сообщения в журнале событий приложений Windows. Служба записывает эти события в журнал при своем запуске, остановке и при возникновении некоторых проблем.  
  
 В этом разделе представлены сведения о самых распространенных сообщениях о событиях, которые регистрирует служба в журнале событий приложений. Служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] регистрирует все сообщения, описанные в этом разделе, вместе с источником событий SQLISService.  
  
 Дополнительные сведения о службе [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] см. в разделе [Службы Integration Services (службы SSIS)](integration-services-service-ssis-service.md).  
  
## <a name="messages-about-the-status-of-the-service"></a>Сообщения о состоянии службы  
 При выборе установки служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] служба [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] устанавливается и запускается, а тип ее запуска устанавливается в автоматический.  
  
|Идентификатор события|Символическое имя|Text|Примечания|  
|--------------|-------------------|----------|-----------|  
|256|DTS_MSG_SERVER_STARTING|Запуск службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] .|Служба запускается.|  
|257|DTS_MSG_SERVER_STARTED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] Служба   запущена.|Служба запущена.|  
|260|DTS_MSG_SERVER_START_FAILED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] .%nОшибка: %1|Не удалось запустить службу. Невозможность запуска может быть вызвана поврежденной установкой или недопустимой учетной записью службы.|  
|258|DTS_MSG_SERVER_STOPPING|Остановка службы [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] .%n%nПри выходе остановить все выполняющиеся пакеты: %1|Служба остановлена, а при соответствующей настройке она остановит все выполняющиеся пакеты. В файле конфигурации можно указать значения true или false, определяющие, будет ли служба останавливать все выполняющиеся пакеты при собственной остановке. Сообщение для этого события содержит значение соответствующего параметра.|  
|259|DTS_MSG_SERVER_STOPPED|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] остановлена.%nВерсия сервера %1|Служба остановлена.|  
  
## <a name="messages-about-the-configuration-file"></a>Сообщения о файле конфигурации  
 Параметры службы [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] хранятся в XML-файле, который можно изменять. Дополнительные сведения см. в разделе [Настройка служб Integration Services (службы SSIS)](../configuring-the-integration-services-service-ssis-service.md).  
  
|Идентификатор события|Символическое имя|Text|Примечания|  
|--------------|-------------------|----------|-----------|  
|274|DTS_MSG_SERVER_MISSING_CONFIG_REG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] : %nпараметр реестра, определяющий файл конфигурации, не существует. %nпопытка загрузки файла конфигурации по умолчанию.|Не существует записи реестра, содержащей путь к файлу конфигурации, или этот путь пустой.|  
|272|DTS_MSG_SERVER_MISSING_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] не существует.%nПроизводится загрузка с установками по умолчанию.|В заданном расположении отсутствует файл конфигурации.|  
|273|DTS_MSG_SERVER_BAD_CONFIG|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] .%nОшибка чтения файла конфигурации: %1%n%nПроизводится загрузка сервера с установками по умолчанию.|Не удалось считать файл конфигурации, или он недопустим. Эта ошибка может быть результатом ошибки синтаксиса XML в файле.|  
  
## <a name="other-messages"></a>Другие сообщения  
  
|Идентификатор события|Символическое имя|Text|Примечания|  
|--------------|-------------------|----------|-----------|  
|336|DTS_MSG_SERVER_STOPPING_PACKAGE|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssIS](../../includes/ssis-md.md)] : остановка выполняющегося пакета.%nИдентификатор экземпляра пакета: %1%nИдентификатор пакета: %2%nИмя пакета: %3%nОписание пакета: %4%nПакет запущен: %5.|Служба пытается остановить выполнение пакета. В среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]можно вести наблюдение и останавливать выполнение пакетов. Сведения об управлении пакетами в среде [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] см. в разделе [Управление пакетами (службы SSIS)](package-management-ssis-service.md).|  
  
## <a name="related-tasks"></a>Связанные задачи  
 Сведения о просмотре записей журнала см. в разделе [Просмотр записей журнала в окне "Регистрация событий"](../view-log-entries-in-the-log-events-window.md).  
  
## <a name="see-also"></a>См. также  
 [Регистрация событий в пакете служб Integration Services](../performance/events-logged-by-an-integration-services-package.md)  
  
  
