---
title: 'Счетчики производительности для объектов производительности ReportServer: Service и reportserversharepoint: Service | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
caps.latest.revision: 23
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c0573346427258d9b79188852c8d6e13af1cb8d1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37238394"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>Счетчики производительности для объектов производительности ReportServer:Service и ReportServerSharePoint:Service
  В данном разделе описаны счетчики производительности для следующих объектов производительности [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]:  
  
-   `ReportServer:Service`  
  
-   `ReportServerSharePoint:Service`  
  
> [!NOTE]  
>  Эти объекты производительности служат для наблюдения за событиями на локальном сервере отчетов. При запуске сервера отчетов в масштабном развертывании счетчики относятся к текущему серверу, а не к масштабному развертыванию в целом.  
  
 Объекты производительности доступны в системном мониторе Windows (**Perfmon.exe**). Дополнительные сведения см. в документации по Windows. [Профилирование среды выполнения](http://msdn.microsoft.com/library/w4bz2147.aspx) (http://msdn.microsoft.com/library/w4bz2147.aspx).  
  
 В этом разделе:  
  
-   [Счетчики производительности ReportServer:Service (сервер отчетов в собственном режиме)](#bkmk_ReportServer)  
  
-   [ReportServerSharePoint:Service (сервер отчетов в режиме SharePoint)](#bkmk_ReportServerSharePoint)  
  
-   [Использование командлетов PowerShell для возврата списков](#bkmk_powershell)  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint | В собственном режиме.  
  
##  <a name="bkmk_ReportServer"></a> Счетчики производительности ReportServer:Service (сервер отчетов в собственном режиме)  
 Объект производительности `ReportServer:Service` включает коллекцию счетчиков для отслеживания связанных с HTTP и памятью событий для экземпляра сервера отчетов. Этот объект производительности отображается однократно для каждого [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] экземпляра на компьютере, а также можно добавлять или удалять счетчики объекта производительности для каждого экземпляра. Счетчики для экземпляра по умолчанию отображаются в формате `ReportServer:Service`. Счетчики для именованных экземпляров отображаются в формате `ReportServer$<` *имя_экземпляра*`>:Service`.  
  
 `ReportServer:Service` Объект появился в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], и он предоставляет часть счетчиков, которые были включены с помощью Internet Information Services (IIS) и [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] в предыдущих версиях [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Эти новые счетчики являются уникальными для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Они отслеживают связанные с HTTP события для сервера отчетов, такие как запросы, соединения и попытки входа. Кроме того, этот объект производительности включает счетчики для отслеживания событий управления памятью.  
  
 В следующей таблице перечислены счетчики, включенные в `ReportServer:Service` объект производительности.  
  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий скрипт Windows PowerShell вернет список счетчиков производительности для CounterSetName  
  
```  
(get-counter -listset "ReportServer:Service").paths  
```  
  
|Счетчик|Описание|  
|-------------|-----------------|  
|`Active connections`|Количество активных в текущий момент соединений на сервере.|  
|`Bytes Received Total`|Число байт, полученных сервером. Этот счетчик ведет подсчет общего приблизительного числа байтов, полученных как диспетчером отчетов, так и сервером отчетов.|  
|`Bytes Received/sec`|Число байтов, полученных сервером за одну секунду. Этот счетчик обновляется только при завершении передачи. Это означает, что значение счетчика остается равным 0, а затем значение растет после завершения передачи.|  
|`Bytes Sent Total`|Число байтов, отправленных сервером. Этот счетчик ведет подсчет общего приблизительного числа байтов, оправленных как диспетчером отчетов, так и сервером отчетов.|  
|`Bytes Sent/sec`|Число байтов, отправленных сервером за секунду. Этот счетчик обновляется только при завершении передачи. Это означает, что значение счетчика остается равным 0, а затем значение растет после завершения передачи.|  
|`Errors Total`|Общее число ошибок, возникших во время выполнения HTTP-запросов. Эти ошибки включают 400-е и 500-е коды состояния HTTP.|  
|`Errors/sec`|Общее число ошибок, возникших во время выполнения HTTP-запросов за одну секунду. Эти ошибки включают 400-е и 500-е коды состояния HTTP.|  
|`Logon Attempts Total`|Число попыток входа, выполненных из типов проверки подлинности RSWindows. Типы проверок подлинности RSWindows включают RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos и RSWindowsBasic. Нулевое значение (0) отвечает за нестандартную проверку подлинности.|  
|`Logon Attempts/sec`|Число попыток входа.|  
|`Logon Successes Total`|Число успешных входов для типов проверки подлинности RSWindows. Типы проверок подлинности RSWindows включают RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos и RSWindowsBasic. Нулевое значение (0) отвечает за нестандартную проверку подлинности.|  
|`Logon Successes/sec`|Число успешных входов.|  
|`Memory Pressure State`|Одно из следующих чисел от 1 до 5, указывающее текущее состояние памяти на сервере.<br /><br /> 1: нет нагрузки<br /><br /> 2: низкая нагрузка<br /><br /> 3: средняя нагрузка<br /><br /> 4: высокая нагрузка<br /><br /> 5: чрезмерная нагрузка|  
|`Memory Shrink Amount`|Число байтов, запрошенных сервером для сжатия используемой памяти.|  
|`Memory Shrink Notifications/sec`|Число уведомлений, сформированных сервером в последнюю секунду для сжатия используемой памяти. Это число указывает, как часто сервер испытывает недостаток памяти.|  
|`Requests Disconnected`|Число отсоединений запросов, возникших из-за сбоя в канале связи.|  
|`Requests Executing`|Количество запросов, обрабатываемых в настоящий момент.|  
|`Requests Not Authorized`|Число запросов, завершенных с кодом состояния HTTP 401.|  
|`Requests Rejected`|Общее число запросов, не обработанных из-за недостаточных ресурсов сервера. Этот счетчик отражает число запросов, возвращенных с кодом состояния HTTP 503, указывающим на то, что сервер слишком загружен.|  
|`Requests Total`|Общее число запросов, полученных службой сервера отчетов с момента запуска. Этот счетчик ведет подсчет запросов, отправленных диспетчеру отчетов, а также запросов, отправленных диспетчером отчетов серверу отчетов.|  
|`Requests/sec`|Количество обрабатываемых за секунду запросов. Это значение отражает текущую пропускную способность приложения.|  
|`Tasks Queued`|Число задач, ожидающих доступности потока для обработки. Каждый запрос, выполненный к серверу отчетов, соответствует одной или нескольким задачам. Этот счетчик представляет только число задач, готовых к обработке; он не включает число выполняющихся в настоящее время задач.|  
  
##  <a name="bkmk_ReportServerSharePoint"></a> ReportServerSharePoint:Service (сервер отчетов в режиме SharePoint)  
 `ReportServerSharePoint:Service` Объект был добавлен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий скрипт Windows PowerShell вернет список счетчиков производительности для CounterSetName  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
|Счетчик|  
|-------------|  
|`Memory Pressure State`|  
|`Memory Shrink Amount`|  
|`Memory Shrink Notifications/Sec`|  
  
##  <a name="bkmk_powershell"></a> Использование командлетов PowerShell для возврата списков  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий скрипт Windows PowerShell вернет список счетчиков производительности для CounterSetName "ReportServerSharePoint:Service":  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за производительностью сервера отчетов](monitoring-report-server-performance.md)   
 [Счетчики производительности для MSRS 2014 Web Service и объекты производительности компонента MSRS 2014 Windows Service &#40;собственный режим&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)   
 [Счетчики производительности для MSRS 2014 Web Service SharePoint Mode и MSRS 2014 Windows Service SharePoint режим, объекты производительности &#40;режиме интеграции с SharePoint&#41;]... / performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
  
  
