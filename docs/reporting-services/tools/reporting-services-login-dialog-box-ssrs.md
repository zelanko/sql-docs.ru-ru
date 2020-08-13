---
title: Диалоговое окно "Имя входа служб Reporting Services" | Документация Майкрософт
description: Узнайте, как использовать диалоговое окно "Имя входа служб Reporting Services", чтобы задать учетные данные для публикации отчетов на сервере отчетов.
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
ms.openlocfilehash: 4d3e34d7ff9f92506f1225aea173521ee7d30e79
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86919620"
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
 [Create data connection strings — Report Builder & SSRS](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)  (Создание строк подключения к данным (построитель отчетов и службы SSRS))  
 [Задание учетных данных и сведениях о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Справка F1 по использованию конструктора отчетов](../../reporting-services/tools/report-designer-f1-help.md)  
  
  
