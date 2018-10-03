---
title: rsServerConfigurationError — ошибка служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6118c1f6be29dd47f2df49371274bbfb93100f5e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064734"
---
# <a name="rsserverconfigurationerror---reporting-services-error"></a>rsServerConfigurationError - Ошибка службы Reporting Services
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|rsServerConfiguration|  
|Источник события|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|Компонент|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Текст сообщения|Сервер отчетов обнаружил ошибку конфигурации.|  
  
## <a name="explanation"></a>Объяснение  
 Это общая ошибка, возникающая в том случае, когда сервер отчетов или средство разработки отчетов имеет недопустимые параметры конфигурации. Эта ошибка обычно сопровождается вторым сообщением, в котором содержится действительная причина первой ошибки.  
  
 В следующем списке приведены основные возможные причины.  
  
-   Не удалось найти или считать файл RSReportServer.config или RSReportDesigner.config.  
  
-   XML-элементы в одном из файлов конфигурации отсутствуют или являются недопустимыми.  
  
-   Значения одного или нескольких XML-элементов отсутствуют или являются недопустимыми.  
  
-   Параметры реестра являются недопустимыми.  
  
## <a name="user-action"></a>Действие пользователя  
 Если эта ошибка возникла после того, как файл конфигурации был изменен вручную, удалите внесенные изменения, вернув прежние значения, либо, при наличии резервной копии, восстановите предыдущую версию файла.  
  
 Чтобы просмотреть дополнительные сведения об ошибке, сопровождающий `rsServerConfiguration` ошибки, просмотрите файлы сервера отчетов трассировки журналов, расположенные в \Microsoft SQL Server\MSRS12.\< instancename > \Reporting Services\LogFiles. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также  
 [Файлы конфигурации служб Reporting Services](../report-server/reporting-services-configuration-files.md)   
 [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
