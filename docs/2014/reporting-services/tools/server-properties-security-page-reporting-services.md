---
title: Свойства сервера (страница "Безопасность") — службы Reporting Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.reportserver.serverproperties.security.f1
ms.assetid: f49aedc6-f145-4df1-8f69-d5d910f492c6
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: 722a2b825b0ec56b7932de29a74faf74627834f0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098812"
---
# <a name="server-properties-security-page---reporting-services"></a>Свойства сервера (страница «Безопасность») — службы Reporting Services
  Эта страница используется для отключения функций, которые могут нарушить безопасность сервера отчетов. Отключение этих функций ограничивает некоторые возможности, но повышает общую безопасность сервера отчетов, устраняя определенные угрозы.  
  
 Чтобы открыть эту страницу, в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру сервера отчетов, щелкните его правой кнопкой мыши и выберите пункт **Свойства**. Нажмите кнопку **Безопасность** , чтобы открыть эту страницу.  
  
## <a name="options"></a>Параметры  
 **Использовать встроенную безопасность Windows для источников данных для отчетов**  
 Указывает, можно ли установить соединение с источником данных отчета с помощью токена безопасности Windows для пользователя, запрашивающего отчет.  
  
 Если отключить эту функцию, функция встроенной безопасности Windows на страницах свойств источника данных отчета станет недоступной. Если источники данных отчета настроены для применения встроенной безопасности Windows, и эта функция отключается, сервер отчетов немедленно обновит все свойства соединения с источниками данных, чтобы запрашивать учетные данные.  
  
 **Разрешить автоматизированные отчеты**  
 Указывает, могут ли пользователи выполнять нерегламентированные запросы из отчета построителя отчетов, в котором автоматически формируются новые отчеты, когда пользователь щелкает интересующие его данные.  
  
 Этот параметр определяет, какое значение присваивается свойству `EnableLoadReportDefinition` сервера отчетов — `True` или `False`. Если этот флажок снят, свойству будет присвоено `False` и сервер не будет формировать отчеты с дополнительной информацией, которые создаются во время просмотра данных отчета. Все вызовы метода `LoadReportDefinition` будут блокированы.  
  
 Отключение этого параметра снижает угрозу, при котором злоумышленник использует атаки отказа в обслуживании, перегружая сервер отчетов с `LoadReportDefinition` запросов.  
  
## <a name="see-also"></a>См. также  
 [Установка свойств сервера отчетов (среда Management Studio)](set-report-server-properties-management-studio.md)   
 [Подключение к серверу отчетов в среде Management Studio](connect-to-a-report-server-in-management-studio.md)   
 [Укажите учетные данные и сведения о соединении для источников данных отчетов] (.. /Report-Data/Specify-Credential-and-Connection-Information-for-Report-Data-Sources.md [отчетов сервера в Справка F1 среды Management Studio](report-server-in-management-studio-f1-help.md)  
  
  