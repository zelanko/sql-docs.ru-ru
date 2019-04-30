---
title: Свойства сервера (страница "Выполнение") | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.execution.f1
ms.assetid: 53b77db1-b013-4dac-82dd-30c0de276639
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9e2d871426345627f88992d4941068681b82cdf0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63157656"
---
# <a name="server-properties-execution-page"></a>Свойства сервера (страница «Выполнение»)
  Используйте данную страницу для установки значения времени ожидания для выполнения отчета. Это значение применяется ко всем отчетам, обрабатываемым текущим экземпляром сервера отчетов. Для отдельных отчетов это значение можно заменить. Указанное значение должно охватывать все операции по обработке отчета, выполняемые на сервере отчетов, с учетом обработки запросов, выполняемой на сервере базы данных в то время, когда сервер отчетов получает данные, используемые в отчете.  
  
 Чтобы открыть эту страницу, в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к экземпляру сервера отчетов, щелкните его правой кнопкой мыши и выберите пункт **Свойства**. Нажмите кнопку **Выполнение** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры  
 **Не задавать время ожидания для выполнения отчета**  
 Допускать неограниченное время на сервере отчетов для завершения обработки отчета.  
  
 **Ограничить выполнение отчета следующим количество секунд**  
 Установить ограничение по продолжительности выполнения отчета. Этот период времени начинается во время запрашивания отчета. Если этот период времени заканчивается до полной обработки отчета, то сервер отчетов отменяет процесс и все связанные с ним запросы к внешним источникам данных.  
  
## <a name="see-also"></a>См. также  
 [Установка свойств сервера отчетов (среда Management Studio)](set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Установка свойств обработки отчетов](../report-server/set-report-processing-properties.md)   
 [Задание значений времени ожидания при обработке отчетов и общих наборов данных (SSRS)](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)   
 [Справка F1 по использованию сервера отчетов среде Management Studio](report-server-in-management-studio-f1-help.md)  
  
  
