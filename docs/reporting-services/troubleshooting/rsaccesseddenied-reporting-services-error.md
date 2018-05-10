---
title: rsAccessedDenied — ошибка служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: troubleshooting
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- rsAccessDenied error
ms.assetid: 2f76b1bf-96a2-4755-b76b-84e933220efc
caps.latest.revision: 21
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: d17bc3aeb2413ce7dd69d0afd263e3c9f6db0ae8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="rsaccesseddenied---reporting-services-error"></a>rsAccessedDenied - Ошибка службы Reporting Services
  Ошибка службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **rsAccessedDenied** происходит, когда у пользователя нет разрешения на выполнение действия. Например, у них нет назначения роли, которая позволяет им открывать отчет или они открыли свой браузер без необходимых разрешений.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Собственный режим | Режим интеграции с SharePoint|  
  
-   Если ошибка произошла во время доступа к серверу отчетов напрямую при помощи URL-адреса, то это исключение соответствует ошибке HTTP 401.  
  
-   Если ошибка произошла во время работы с диспетчером отчетов или другой программой, то ошибка появится на странице ошибок.  
  
-   Если ошибка произошла во время запланированной операции, подписки или доставки, то сведения о ней появятся только в файле журнала сервера отчетов.  
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|**Название продукта**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|**Идентификатор события**|rsAccessedDenied|  
|**Источник события**|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings|  
|**Компонент**|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|**Текст сообщения**|Предоставленные пользователю 'mydomain\myAccount' разрешения недостаточны для выполнения данной операции. (rsAccessDenied) (ReportingServicesLibrary)|  
  
## <a name="user-action"></a>Действие пользователя  
 Разрешения на доступ к содержимому и операциям сервера отчетов назначаются при помощи ролей. В новой установке только у локальных администраторов есть доступ к серверу отчетов. Чтобы предоставить доступ другим пользователям, локальному администратору необходимо создать назначение ролей, описывающее учетную запись пользователя или группы домена, одну или несколько ролей, определяющих, какие задачи пользователь сможет выполнять, и область видимости (обычно корневую папку или корневой узел в иерархии папок сервера отчетов). Назначения ролей можно создать при помощи диспетчера отчетов. Дополнительные сведения см. по ключевому слову «назначения ролей» в электронной документации по SQL Server.  
  
 Данная ошибка вызывается также локальным администрирование сервера отчетов. Дополнительные сведения см. в разделе [Настройка сервера отчетов, работающего в основном режиме, для локального администрирования (службы SSRS)](../../reporting-services/report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Назначения ролей](../../reporting-services/security/role-assignments.md)   
 [Предоставление разрешений на сервер отчетов в собственном режиме](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)   
 [Роли и разрешения (службы Reporting Services)](../../reporting-services/security/roles-and-permissions-reporting-services.md)  
  
  
