---
title: "Свойства сервера (страница \"Безопасность\") — службы Reporting Services | Документация Майкрософт"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8da36c90d2eb22600ad6560a37367e68de933971
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="server-properties-security-page---reporting-services"></a>Свойства сервера (страница «Безопасность») — службы Reporting Services
  Страница [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] в [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] используется для отключения функций, которые могут нарушить безопасность сервера отчетов. Отключение этих функций ограничивает некоторые возможности, но повышает общую безопасность сервера отчетов, устраняя определенные угрозы.  
  
 Чтобы открыть эту страницу:
 1) Запустите среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].
 2) Подключитесь к экземпляру сервера отчетов.
 3) Щелкните правой кнопкой мыши имя сервера отчетов и выберите пункт **Свойства**. 
 4) Нажмите кнопку **Безопасность** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры  
 **Использовать встроенную безопасность Windows для источников данных для отчетов**  
 Указывает, можно ли установить соединение с источником данных отчета с помощью токена безопасности Windows для пользователя, запрашивающего отчет.  
  
 Если отключить эту функцию, функция встроенной безопасности Windows на страницах свойств источника данных отчета станет недоступной. Если источники данных отчета настроены для применения встроенной безопасности Windows, и эта функция отключается, сервер отчетов немедленно обновит все свойства соединения с источниками данных, чтобы запрашивать учетные данные.  
  
 **Разрешить автоматизированные отчеты**  
 Указывает, могут ли пользователи выполнять нерегламентированные запросы из отчета построителя отчетов, в котором автоматически формируются новые отчеты, когда пользователь щелкает интересующие его данные.  
  
 Этот параметр определяет, какое значение присваивается свойству **EnableLoadReportDefinition** сервера отчетов — **True** или **False**. Если отключить этот параметр, свойству присваивается значение **False** , и сервер отчетов не будет формировать отчеты с дополнительной информацией, создаваемые во время просмотра данных. Все вызовы метода **LoadReportDefinition** будут блокированы.  
  
 Отключение этого параметра снижает угрозу атаки вида «отказ в обслуживании», которая перегружает сервер отчетов запросами **LoadReportDefinition** .  
  
## <a name="see-also"></a>См. также  
 [Настройка свойств сервера отчетов &#40; Среда Management Studio &#41;](../../reporting-services/tools/set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](../../reporting-services/tools/connect-to-a-report-server-in-management-studio.md)   
 [Укажите учетные данные и сведения о соединении для источников данных отчета](../../reporting-services/report-data/specify-credential-and-connection-information-for-report-data-sources.md)   
 [Сервер отчетов в Справка F1 среды Management Studio](../../reporting-services/tools/report-server-in-management-studio-f1-help.md)  
  
  

