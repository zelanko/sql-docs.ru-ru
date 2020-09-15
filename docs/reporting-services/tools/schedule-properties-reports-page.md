---
title: Свойства расписания (страница "Отчеты") | Документы Майкрософт
description: Узнайте больше о странице свойств расписания Reporting Services в SQL Server Management Studio, где перечислены все отчеты для определенного общего расписания.
ms.date: 06/30/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 556fc5e4c785345ede475dcadb2c5673489a279f
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87939419"
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
>  Эта функция поддерживается не во всех выпусках [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Список функций, поддерживаемых различными выпусками [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в статье [Выпуски и поддерживаемые функции SQL Server 2017](../../sql-server/editions-and-components-of-sql-server-2017.md).  
  
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
 [Настройка общих свойств отчета (диспетчер отчетов)](https://docs.microsoft.com/sql/reporting-services/reports/configure-execution-properties-for-a-report-report-manager)  
  
  

