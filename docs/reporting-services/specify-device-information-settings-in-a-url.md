---
title: Указание параметров сведений об устройстве в URL-адресе | Документы Майкрософт
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
author: markingmyname
ms.author: maghan
ms.openlocfilehash: b51b0d3e90252ef2b901de4ef48e443ef36079c0
ms.sourcegitcommit: 9ece10c2970a4f0812647149d3de2c6b75713e14
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51813325"
---
# <a name="specify-device-information-settings-in-a-url"></a>Указание настройки сведений об устройстве в URL-адресе
  Настройки сведений об устройстве передаются в модуль подготовки отчетов. Если для подготовки отчета к просмотру используются методы веб-службы сервера отчетов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , то в качестве входного параметра передается XML-элемент **DeviceInfo** . Дочерние элементы для элемента **DeviceInfo** зависят от настроек сведений об устройстве различных модулей подготовки отчетов. Настройки сведений об устройстве можно включить в URL-адрес с помощью строки параметров *rc:tag=value* , где параметр *tag* представляет имя элемента с настройками сведений об устройстве, к которому выполняется доступ. Дополнительную информацию о настройках сведений в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]см. в разделе [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md).  
  
## <a name="example"></a>Пример  
 В следующем примере с помощью параметра сведений об устройстве *OutputFormat* для модуля подготовки изображений для указанного отчета задается формат JPEG (для удобочитаемости добавлены разрывы строк).  
  
```  
https://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>См. также:  
 [Доступ по URL-адресу (службы SSRS)](../reporting-services/url-access-ssrs.md)   
 [Ссылка на параметр доступа по URL-адресу](../reporting-services/url-access-parameter-reference.md)  
  
  
