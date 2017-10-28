---
title: "Указать настройки сведений об устройстве в URL-адрес | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 09e1655e7945a459cf9d606d24cf7479ee4fc568
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="specify-device-information-settings-in-a-url"></a>Указание настройки сведений об устройстве в URL-адресе
  Настройки сведений об устройстве передаются в модуль подготовки отчетов. Если для подготовки отчета к просмотру используются методы веб-службы сервера отчетов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , то в качестве входного параметра передается XML-элемент **DeviceInfo** . Дочерние элементы для элемента **DeviceInfo** зависят от настроек сведений об устройстве различных модулей подготовки отчетов. Настройки сведений об устройстве можно включить в URL-адрес с помощью строки параметров *rc:tag=value* , где параметр *tag* представляет имя элемента с настройками сведений об устройстве, к которому выполняется доступ. Дополнительную информацию о настройках сведений в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]см. в разделе [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Пример  
 В следующем примере с помощью параметра сведений об устройстве *OutputFormat* для модуля подготовки изображений для указанного отчета задается формат JPEG (для удобочитаемости добавлены разрывы строк).  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>См. также  
 [Доступ к URL-адрес &#40; Службы SSRS &#41;](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа URL-адрес](../reporting-services/url-access-parameter-reference.md)  
  
  

