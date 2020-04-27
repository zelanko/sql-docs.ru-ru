---
title: Диалоговое окно имени для входа Reporting Services (SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.reportservicelogin.f1
ms.assetid: 2037d797-0b61-44c7-931f-6c689c3fc733
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 232ee51614a668b07263c3e3a4182f23652135bf
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66099873"
---
# <a name="reporting-services-login-dialog-box-ssrs"></a>Диалоговое окно «Имя входа служб Reporting Services» (службы SSRS)
  В диалоговом окне **Имя входа служб Reporting Services** задаются учетные данные для публикации отчетов на сервере отчетов.  
  
-   **Примечание** . Если вы впервые опубликовали отчет на сервере отчетов, с момента **установки свойства Deployment** для проекта, убедитесь, что указанное имя сервера имеет вид `http://localhost/reportserver`, а не `http://localhost/reports`. Указание каталога `reports` на локальном сервере вместо каталога `reportserver` косвенно вызывает открытие этого диалогового окна. Дополнительные сведения о настройке параметра **TargetServerURL** см. в разделе [Задание свойств развертывания (службы Reporting Services)](set-deployment-properties-reporting-services.md).  
  
## <a name="options"></a>Параметры  
 **Server**  
 Отображает имя сервера отчетов. Например, `http://localhost/reportserver`. Для серверов отчетов, использующих порт, отличный от порта по умолчанию 80, включается номер порта. Например, `http://localhost:81/reportserver`.  
  
 **User name**  
 Введите имя пользователя для входа в данную веб-службу.  
  
 **Пароль**  
 Введите пароль для входа в данную веб-службу.  
  
## <a name="see-also"></a>См. также  
 [Подключения к данным, источники данных и строки подключения в Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Указание учетных данных и сведений о соединении для источников данных отчета](../report-data/specify-credential-and-connection-information-for-report-data-sources.md) [конструктор отчетов Справка F1](report-designer-f1-help.md)  
  
  
