---
title: Свойства расписания (страница "Отчеты") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 635a5428685feff5887b0800388a41f95a108c1a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209234"
---
# <a name="schedule-properties-reports-page"></a>Свойства расписания (страница отчетов)
  Эта страница используется для просмотра списка всех отчетов, использующих общее расписание. Расписания могут использоваться для обновления моментальных снимков отчетов, формирования журнала отчета, запуска подписки или истечения срока действия кэшированной копии отчета. Сведения об использовании расписания можно найти в свойствах и сведениях о подписке на отчет.  
  
 Несмотря на то, что на данной странице отображаются все отчеты, в которых используется общее расписание, здесь не указывается, сколько раз общее расписание используется в рамках отдельного отчета. Например, предположим, что есть 20 различных подписчиков отчета «Продажи компании» (Company Sales), использующих для запуска обработки подписки одно и то же общее расписание. В этом случае в упомянутом списке отчет «Продажи компании» (Company Sales) будет указан лишь один раз, несмотря на то, что в отчете имеется 20 ссылок на общее расписание.  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], подключиться к серверу отчетов, откройте **Общие расписания** папку, щелкните правой кнопкой мыши общее расписание, выберите **свойства**, а затем нажмите кнопку **отчеты** .  
  
> [!NOTE]  
>  Эта функция поддерживается не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о функциях, поддерживаемых выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые выпусками SQL Server 2012](http://go.microsoft.com/fwlink/?linkid=232473) (http://go.microsoft.com/fwlink/?linkid=232473).  
  
## <a name="options"></a>Параметры  
 **Папка**  
 Позволяет задать путь к отчету.  
  
 **Отчет**  
 Позволяет задать имя отчета, использующего расписание.  
  
## <a name="see-also"></a>См. также  
 [Создание, изменение и удаление расписаний](../subscriptions/create-modify-and-delete-schedules.md)   
 [Расписания](../subscriptions/schedules.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Настройка общих свойств отчета &#40;диспетчера отчетов&#41;](../configure-general-properties-for-a-report-report-manager.md)  
  
  
