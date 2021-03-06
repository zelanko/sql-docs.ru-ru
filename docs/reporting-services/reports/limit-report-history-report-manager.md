---
title: Ограничение журнала отчета — Reporting Services | Документация Майкрософт
description: Узнайте, как настроить журнал отчетов на сервере отчетов. Также узнайте, как настроить журнал для определенного отчета.
ms.date: 06/26/2019
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reports
ms.topic: conceptual
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d01a008e00d2effccb109555799bbe6d55baf1e3
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97466575"
---
# <a name="limit-report-history---reporting-services"></a>Ограничение журнала отчета — Reporting Services
  Журнал отчета — это коллекция моментальных снимков отчета, созданных на протяжении определенного времени. Можно создавать журнал отчета по запросу или определить в расписании, насколько часто должен создаваться моментальный снимок и добавляться к журналу.  
  
 Журнал отчета хранится в базе данных сервера отчетов. Если моментальные снимки отчета содержат большой объем данных, вы можете ограничить журнал отчета, чтобы хранение снимков меньше влияло на размер базы данных.  

::: moniker range="=sql-server-2016"
  
## <a name="to-configure-report-history-for-a-report-server"></a>Настройка журнала отчетов на сервере отчетов  
  
1.  В диспетчере отчетов щелкните **Параметры веб-сайта** на главной панели инструментов.  
  
2.  Для сохранения всех без исключения моментальных снимков журнала отчетов выберите **Хранить в журнале отчета неограниченное количество моментальных снимков** . Кроме того, чтобы задать максимальное число моментальных снимков, которые могут храниться для каждого отчета, выберите **Ограничить количество копий журнала отчета** .  
  
3.  Нажмите кнопку **Применить**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>Настройка журнала для определенного отчета  
  
1.  В диспетчере отчетов перейдите к отчету, журнал которого нужно настроить, и щелкните отчет, чтобы открыть его.  
  
2.  Щелкните вкладку **Свойства**.  
  
3.  Перейдите на вкладку **Журнал** .  
  
4.  Выберите параметры отчета и нажмите кнопку **Применить**. Подробные сведения о каждом параметре см. в разделе [Страница "Свойства параметров моментального снимка" (диспетчер отчетов)](/previous-versions/sql/sql-server-2016/ms189952(v=sql.130)).  
  
## <a name="see-also"></a>См. также:  
 [Добавление моментального снимка к журналу отчета (диспетчер отчетов)](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Диспетчер отчетов (службы SSRS в собственном режиме)](../web-portal-ssrs-native-mode.md)  

::: moniker-end

::: moniker range=">=sql-server-2017"

## <a name="to-configure-report-history-for-a-report-server"></a>Настройка журнала отчетов на сервере отчетов  
  
1.  На главной панели инструментов веб-портала щелкните **Параметры сайта**.  
  
2.  Для сохранения всех без исключения моментальных снимков журнала отчетов выберите **Хранить в журнале отчета неограниченное количество моментальных снимков** . Кроме того, чтобы задать максимальное число моментальных снимков, которые могут храниться для каждого отчета, выберите **Ограничить количество копий журнала отчета** .  
  
3.  Нажмите кнопку **Применить**.  
  
## <a name="to-configure-report-history-for-a-specific-report"></a>Настройка журнала для определенного отчета  
  
1.  Перейдите на веб-портале к отчету, журнал которого нужно настроить, и щелкните отчет, чтобы открыть его.  
  
2.  Щелкните вкладку **Свойства**.  
  
3.  Перейдите на вкладку **Журнал** .  
  
4.  Выберите параметры отчета и нажмите кнопку **Применить**. Сведения о каждом параметре см. в разделе [Страница свойств "Параметры моментальных снимков"](/previous-versions/sql/sql-server-2016/ms189952(v=sql.130)).  
  
## <a name="see-also"></a>См. также:  
 [Добавление моментального снимка в журнал отчета](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   

::: moniker-end
