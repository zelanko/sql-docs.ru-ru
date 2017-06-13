---
title: "Отладка кода модулей доставки | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: d3e683887f02436ad948b6a6aedb64ef749a7547
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="debugging-delivery-extension-code"></a>Отладка кода модулей доставки
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Предоставляет несколько средств отладки, которые могут помочь при анализе кода в модуле доставки и поиск ошибок в коде. Какое средство будет наилучшим, зависит от того, что нужно выполнить. В этом примере используется [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-delivery-extension-code"></a>Отладка кода в модуле доставки  
  
1.  Запустите [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] и откройте проект модуля доставки.  
  
2.  Выполните построение проекта и разверните сборку модуля доставки и сопровождающего ее PDB-файла на сервере отчетов и в диспетчере отчетов. Дополнительные сведения о развертывании см. в разделе [развертывание модуля доставки](../../../reporting-services/extensions/delivery-extension/deploying-a-delivery-extension.md).  
  
3.  Если создан пользовательский интерфейс подписки, расширяющий диспетчер отчетов, откройте обозреватель Internet Explorer и перейдите к диспетчеру отчетов, оставив код модуля доставки открытым в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Если для диспетчера отчетов не развернут пользовательский интерфейс подписки, просто откройте клиентское приложение, из которого можно вызывать модуль доставки по API-интерфейсу SOAP.  
  
4.  Перейдите в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] к проекту модуля доставки и задайте в коде несколько точек останова.  
  
5.  Оставив активным окно проекта расширения в доставки выберите **присоединиться к процессу** на **отладки** меню.  
  
     **Присоединиться к процессу** откроется диалоговое окно.  
  
6.  В списке процессов выберите процесс aspnet_wp.exe (или w3wp.exe, если ваше приложение развернуто под IIS 6.0) и нажмите кнопку **присоединение**.  
  
7.  Определите новую подписку с помощью модуля доставки. Для этого обычно используется диспетчер отчетов или API-интерфейс SOAP. Будет запущен отладчик и начнется выполнение кода с учетом заданных точек останова.  
  
8.  Пошаговое выполнение кода с помощью **F11** ключа. Дополнительные сведения об использовании среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для отладки см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека служб Reporting Services расширения](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
