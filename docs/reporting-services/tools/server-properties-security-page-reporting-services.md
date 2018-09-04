---
title: Свойства сервера (страница "Безопасность") — службы Reporting Services | Документация Майкрософт
ms.custom: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: tools
ms.reviewer: ''
ms.suite: reporting-services
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 11
author: markingmyname
ms.author: maghan
manager: kfile
ms.date: 06/10/2016
ms.openlocfilehash: f364d7239f5960df764500d8600d653e378ff470
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40410377"
---
# <a name="server-properties-security-page---reporting-services"></a>Свойства сервера (страница «Безопасность») — службы Reporting Services

  Страница [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] в [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] используется для отключения функций, которые могут нарушить безопасность сервера отчетов. Отключение этих функций ограничивает некоторые возможности, но повышает общую безопасность сервера отчетов, устраняя определенные угрозы.  
  
 Чтобы открыть эту страницу:
 1) Запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2) Подключитесь к экземпляру сервера отчетов.
 3) Щелкните правой кнопкой мыши имя сервера отчетов и выберите пункт **Свойства**.
 4) Нажмите кнопку **Безопасность** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры

### <a name="enable-windows-integrated-security-for-report-data-sources"></a>Использовать встроенную безопасность Windows для источников данных в отчетах

 Указывает, установлено ли соединение с источником данных отчета с помощью токена безопасности Windows для пользователя, запрашивающего отчет.  
  
 Если отключить эту функцию, функция встроенной безопасности Windows на страницах свойств источника данных отчета станет недоступной. Если источники данных отчета настроены для применения встроенной безопасности Windows, и эта функция отключается, сервер отчетов немедленно обновит все свойства соединения с источниками данных, чтобы запрашивать учетные данные.  
  
### <a name="enable-ad-hoc-reporting"></a>Разрешить автоматизированные отчеты

 Указывает, могут ли пользователи выполнять нерегламентированные запросы из отчета построителя отчетов, в котором автоматически формируются новые отчеты, когда пользователь щелкает интересующие его данные.  
  
 Этот параметр определяет, какое значение присваивается свойству **EnableLoadReportDefinition** сервера отчетов — **True** или **False**. Если отключить этот параметр, свойству присваивается значение **False**, и сервер отчетов не будет формировать отчеты с дополнительной информацией, создаваемые во время просмотра данных. Любые вызовы метода **LoadReportDefinition** блокируются.  
  
 Отключение этого параметра снижает угрозу атаки вида «отказ в обслуживании», которая перегружает сервер отчетов запросами **LoadReportDefinition** .  
  
## <a name="see-also"></a>См. также:

 [Установка свойств сервера отчетов (Management Studio) ](../../reporting-services/tools/set-report-server-properties-management-studio.md) [Подключение к серверу отчетов в Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md) [Задание учетных данных и сведений о соединении для источников данных в отчетах](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md) [Справка F1 по серверу отчетов в Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)