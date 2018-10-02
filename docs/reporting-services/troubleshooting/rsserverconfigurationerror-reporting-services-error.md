---
title: rsServerConfigurationError — ошибка служб Reporting Services | Документы Майкрософт
ms.date: 03/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: troubleshooting
ms.topic: conceptual
helpviewer_keywords:
- rsServerConfigurationError
ms.assetid: 0913afc2-34b4-4713-b570-cfd5718975ac
author: markingmyname
ms.author: maghan
ms.openlocfilehash: a03e276df871e7949ac01b7e0f1698dafcb36bf2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793091"
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
  
 Дополнительные сведения об ошибке, связанные с ошибкой **rsServerConfiguration**, см. в файлах журналов трассировки сервера отчетов, которые находятся в папке \Microsoft SQL Server\MSRS12.\<имя_экземпляра>\Reporting Services\LogFiles. Дополнительные сведения см. в разделе [Файлы и источники журналов служб Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
## <a name="internal-only"></a>Только для внутреннего использования  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб Reporting Services](../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Изменение файла конфигурации служб Reporting Services (RSreportserver.config)](../../reporting-services/report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)  
  
  
