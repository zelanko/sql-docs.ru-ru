---
title: Свойства расписания (страница "Отчеты") | Документы Майкрософт
ms.custom: ''
ms.date: 06/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 46bdc17a5cc7f6933b423c27e1397c7d22286bf2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="schedule-properties-reports-page"></a>Свойства расписания (страница отчетов)
  Страница свойств расписания служб [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] используется для просмотра списка всех отчетов, использующих общее расписание. Расписания могут использоваться для обновления моментальных снимков отчетов, формирования журнала отчета, запуска подписки или истечения срока действия кэшированной копии отчета. Сведения об использовании расписания можно найти в свойствах и сведениях о подписке на отчет.  
  
 Несмотря на то, что на данной странице отображаются все отчеты, в которых используется общее расписание, здесь не указывается, сколько раз общее расписание используется в рамках отдельного отчета. Например, предположим, что есть 20 различных подписчиков отчета «Продажи компании» (Company Sales), использующих для запуска обработки подписки одно и то же общее расписание. В этом случае в упомянутом списке отчет «Продажи компании» (Company Sales) будет указан лишь один раз, несмотря на то, что в отчете имеется 20 ссылок на общее расписание.  
  
 Открытие страницы расписания:
 1. Запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2. Подключитесь к серверу отчетов.
 3. Откройте папку **Общие расписания** .
 4. Щелкните общее расписание правой кнопкой мыши и выберите пункт **Свойства**.
 5. Выберите **Отчеты**.  
  
  Общими расписаниями также можно управлять из области **Параметры сайта** на веб-портале [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] .
  
> [!NOTE]  
>  Эта функция поддерживается не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Возможности, поддерживаемые различными выпусками SQL Server 2016](~/sql-server/editions-and-supported-features-for-sql-server-2016.md).  
  
## <a name="options"></a>Параметры  
 **Папка**  
 Позволяет задать путь к отчету.  
  
 **Отчет**  
 Позволяет задать имя отчета, использующего расписание.  
  
## <a name="see-also"></a>См. также:  
 [Создание, изменение и удаление расписаний](../../reporting-services/subscriptions/create-modify-and-delete-schedules.md)   
 [Расписания](../../reporting-services/subscriptions/schedules.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)   
 [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Настройка общих свойств отчета (диспетчер отчетов)](http://msdn.microsoft.com/en-us/10b941b2-28e6-4408-9ee4-acebc63c8496)  
  
  

