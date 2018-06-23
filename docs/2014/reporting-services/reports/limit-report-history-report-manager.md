---
title: Ограничение размеров журнала отчета (диспетчер отчетов) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- viewing report history
- report history [Reporting Services], viewing history
- report history [Reporting Services], configuring history
- historical data [Reporting Services]
- displaying report history
ms.assetid: 8e255792-d9ef-496f-a26c-9e969c1209a0
caps.latest.revision: 35
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 91bb20ac70caf7d7d3e863c975415205badbc063
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098579"
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
  
4.  Выберите параметры отчета и нажмите кнопку **Применить**. Подробные сведения о каждом параметре см. в разделе [Страница "Свойства параметров моментального снимка" (диспетчер отчетов)](../snapshot-options-properties-page-report-manager.md).  
  
## <a name="see-also"></a>См. также  
 [Добавить моментальный снимок к журналу отчета &#40;диспетчера отчетов&#41;](../report-server/add-a-snapshot-to-report-history-report-manager.md)   
 [Диспетчер отчетов (службы SSRS в собственном режиме)](../report-manager-ssrs-native-mode.md)  
  
  