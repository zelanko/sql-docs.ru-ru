---
title: "Ограничивающие журнал отчета (диспетчер отчетов) | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e1925f7527202ea251a6949a18e2f03af4f5952
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="limit-report-history-report-manager"></a>Ограничение размеров журнала отчета (диспетчер отчетов)
  Журнал отчета — это коллекция моментальных снимков отчета, созданных на протяжении определенного времени. Можно создавать журнал отчета по запросу или определить в расписании, насколько часто должен создаваться моментальный снимок и добавляться к журналу.  
  
 Журнал отчета хранится в базе данных сервера отчетов. Если моментальные снимки отчета содержат большое количество данных, можно ограничить объема журнала отчета, чтобы свести к минимуму влияние сохранения моментального снимка на размер базы данных.  
  
### <a name="to-configure-report-history-for-a-report-server"></a>Настройка журнала отчетов на сервере отчетов  
  
1.  В диспетчере отчетов щелкните **Параметры веб-сайта** на главной панели инструментов.  
  
2.  Для сохранения всех без исключения моментальных снимков журнала отчетов выберите **Хранить в журнале отчета неограниченное количество моментальных снимков** . Кроме того, чтобы задать максимальное число моментальных снимков, которые могут храниться для каждого отчета, выберите **Ограничить количество копий журнала отчета** .  
  
3.  Нажмите кнопку **Применить**.  
  
### <a name="to-configure-report-history-for-a-specific-report"></a>Настройка журнала для определенного отчета  
  
1.  В диспетчере отчетов перейдите к отчету, журнал которого нужно настроить, и щелкните отчет, чтобы открыть его.  
  
2.  Перейдите на вкладку **Свойства** .  
  
3.  Перейдите на вкладку **Журнал** .  
  
4.  Выберите параметры отчета и нажмите кнопку **Применить**. Дополнительные сведения о каждом параметре см. в разделе [Страница "Свойства параметров моментального снимка" (диспетчер отчетов)](http://msdn.microsoft.com/library/f6641f59-5267-4f57-8957-63b93d1a9679).  
  
## <a name="see-also"></a>См. также:  
 [Добавление моментального снимка к журналу отчета (диспетчер отчетов)](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](http://msdn.microsoft.com/library/80949f9d-58f5-48e3-9342-9e9bf4e57896)  
  
  
