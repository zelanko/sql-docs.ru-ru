---
title: Роли и разрешения (службы Reporting Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- access controls [Reporting Services]
- permissions [Reporting Services], about permissions
- security [Reporting Services], identity and access control
- authentication [Reporting Services]
- permissions [Reporting Services]
- security [Reporting Services], role-based
- identity [Reporting Services]
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: ab60b588b276fd95e253d3ccf3fdeaf8ac71d409
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56010976"
---
# <a name="roles-and-permissions-reporting-services"></a>Роли и разрешения (службы Reporting Services)
  В службах Reporting Services реализована подсистема проверки подлинности и основанная на ролях модель авторизации. Модели авторизации и проверки подлинности зависят от режима работы сервера отчетов — собственный режим или режим SharePoint. Если сервер отчетов является частью развертывания SharePoint, доступ к серверу отчетов определяется разрешениями SharePoint.  
  
## <a name="identity-and-access-control-for-native-mode"></a>Управление доступом и удостоверениями в собственном режиме  
 Применяемые по умолчанию средства проверки подлинности основаны на средствах проверки подлинности и встроенной безопасности Windows. Настройки проверки подлинности можно изменить так, чтобы сервер отчетов отвечал на различные запросы по проверке подлинности, или даже заменить применяемые по умолчанию средства безопасности нестандартным модулем проверки подлинности, предоставленным пользователем.  
  
 Авторизация базируется на ролях, назначаемых участнику. Каждая роль состоит из набора взаимосвязанных задач, которые, в свою очередь, состоят из взаимосвязанных операций. Так, задание **Управление отчетами** предполагает предоставление доступа к следующим операциям сервера отчетов: просмотр отчетов, добавление отчета, обновление отчета, удаление отчета, планирование отчета и обновление свойств отчета.  
  
## <a name="identity-and-access-control-for-sharepoint-mode"></a>Управление удостоверениями и доступом в режиме интеграции с SharePoint  
 В режиме интеграции с SharePoint проверка подлинности и авторизация осуществляется на сайте SharePoint до того, как запросы попадают на сервер отчетов. В зависимости от конфигурации средств проверки подлинности запросы с сайта SharePoint включают токен безопасности или имя доверенного пользователя. Разрешения, предоставляемые пользователям и группам пользователей SharePoint, включают авторизованный доступ к элементам сервера отчетов, размещенным в библиотеках SharePoint.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Предоставление разрешений на сервер отчетов в собственном режиме](granting-permissions-on-a-native-mode-report-server.md)  
 Описывает модель авторизации, основанную на ролях, которая предоставляет доступ к содержимому и операциям сервера отчетов.  
  
 [Предоставление разрешений для элементов сервера отчетов на сайте SharePoint](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 Объясняет, как использовать для управления доступом к серверу отчетов группы SharePoint, уровни разрешений и разрешения.  
  
## <a name="see-also"></a>См. также  
 [Проверка подлинности с использованием сервера отчетов](authentication-with-the-report-server.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](granting-permissions-on-a-native-mode-report-server.md)  
  
  
