---
title: Диалоговое окно имени для входа Reporting Services (SSRS) | Документы Майкрософт
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: reference
f1_keywords:
- sql13.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 25d2741a8449875852c733aa763322011834a6b1
ms.sourcegitcommit: dda9a1a7682ade466b8d4f0ca56f3a9ecc1ef44e
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65581280"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Диалоговое окно «Имя входа служб Reporting Services» (службы SSRS)
  В диалоговом окне **Имя входа служб Reporting Services** задаются учетные данные для публикации отчетов на сервере отчетов.  
  
-   **Примечание.** Если это первая публикация отчета на сервере отчетов после установки свойства развертывания проекта **TargetServerURL** , убедитесь, что указанное имя сервера совпадает с **server** , а не с **reports**. Например, `https://localhost/reportserver`, а не с `https://localhost/reports`. Указание каталога `reports` на локальном сервере вместо каталога `reportserver` косвенно вызывает открытие этого диалогового окна. Дополнительные сведения о настройке параметра **TargetServerURL** см. в разделе [Задание свойств развертывания (службы Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Параметры  
 **Server**  
 Отображает имя сервера отчетов. Например, `https://localhost/reportserver`. Для серверов отчетов, использующих порт, отличный от порта по умолчанию 80, включается номер порта. Например, `https://localhost:81/reportserver`.  
  
 **User name**  
 Введите имя пользователя для входа в данную веб-службу.  
  
 **Пароль**  
 Введите пароль для входа в данную веб-службу.  
  
## <a name="see-also"></a>См. также:  
 [Подключения к данным, источники данных и строки подключения &#40;построитель отчетов и службы SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)   
 [Задание учетных данных и сведениях о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Справка F1 конструктора отчетов](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
