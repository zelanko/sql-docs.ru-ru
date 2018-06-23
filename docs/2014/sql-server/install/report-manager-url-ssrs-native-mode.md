---
title: URL-адрес диспетчера отчетов (собственный режим SSRS) | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rsconfigtool.reportmanagervirtualdirectory.f1
ms.assetid: 45768952-23a6-45a5-b541-e7bf192b4a78
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1469d877b992638119ad60bafadc1023a4ed5fc7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096988"
---
# <a name="report-manager-url-ssrs-native-mode"></a>URL-адрес диспетчера отчетов (службы Reporting Services в собственном режиме)
  Настроить или изменить URL-адрес для доступа к диспетчеру отчетов можно на странице «URL-адрес диспетчера отчетов». По умолчанию на этой странице наследуется префикс, IP-адрес и порт, соответствующие URL-адресу веб-службы сервера отчетов. Это связано с тем, что диспетчер отчетов предоставляет клиентский доступ к веб-службе, которая запускается под управлением той же службы сервера отчетов. Если нужно изолировать приложения друг от друга и пользоваться диспетчером отчетов для доступа к веб-службе сервера отчетов на другом компьютере, то в файле RSReportServer.config укажите для диспетчера отчетов другой экземпляр. Дополнительные сведения о настройке соединения диспетчера отчетов для удаленного сервера отчетов см. в разделе [диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
 [!INCLUDE[applies](../../includes/applies-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственном режиме.  
  
 Если настройка сервера отчетов выполняется для работы в режиме интеграции с SharePoint, то создавать URL-адрес диспетчера отчетов не нужно. Диспетчер отчетов не поддерживается на сервере отчетов, работающем в режиме интеграции с SharePoint. Если для диспетчера отчетов URL-адрес уже существует, то после настройки конфигурации сервера отчетов для работы в режиме интеграции с SharePoint он становится недоступен.  
  
 Чтобы открыть эту страницу, запустите [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration Manager и нажмите кнопку **URL-адрес диспетчера отчетов** в области навигации. Дополнительные сведения о запуске диспетчера конфигурации см. в разделе [диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
> [!NOTE]  
>  Если диспетчер отчетов не включен, настройка параметров на этой странице будет невозможна. Дополнительные сведения о включении диспетчера отчетов см. в разделе [диспетчер конфигурации служб Reporting Services &#40;собственный режим&#41;](../../../2014/sql-server/install/reporting-services-configuration-manager-native-mode.md).  
  
## <a name="options"></a>Параметры  
 **Виртуальный каталог**  
 Указывает имя виртуального каталога диспетчера отчетов. Каждый экземпляр диспетчера отчетов на одном компьютере может иметь только одно имя виртуального каталога.  
  
 **URL-адреса**  
 Отображает URL-адрес, определенный для текущего экземпляра диспетчера отчетов.  
  
 **Дополнительно**  
 Введите дополнительный URL-адрес для текущего экземпляра диспетчера отчетов.  
  
## <a name="see-also"></a>См. также  
 [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-a-url-ssrs-configuration-manager.md)   
 [URL-адреса в файлах конфигурации &#40;диспетчер конфигурации служб SSRS&#41;](../../reporting-services/install-windows/urls-in-configuration-files-ssrs-configuration-manager.md)   
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](../../reporting-services/install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  