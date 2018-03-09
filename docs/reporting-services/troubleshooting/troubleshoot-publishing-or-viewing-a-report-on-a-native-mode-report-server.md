---
title: "Устранение неполадок с публикацией и просмотром отчетов на сервере отчетов, работающем в собственном режиме | Документы Майкрософт"
ms.custom: 
ms.date: 02/28/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.service: 
ms.component: troubleshooting
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7720a1-d178-45bb-8d6f-63e208cae7fe
caps.latest.revision: "6"
author: markingmyname
ms.author: maghan
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 2e25f72eddf16b1cbb868f0e944a803df0f40340
ms.sourcegitcommit: 7e117bca721d008ab106bbfede72f649d3634993
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2018
---
# <a name="troubleshoot-publishing-or-viewing-a-report-on-a-native-mode-report-server"></a>Устранение неполадок с публикацией и просмотром отчетов на сервере отчетов, работающем в основном режиме
  
  
  
При публикации или передаче отчета на сервер отчетов, настроенный в собственном режиме, могут встретиться проблемы, характерные для просмотра отчетов на сервере отчетов. Этот раздел помогает устранять эти проблемы.   
  
## <a name="why-am-i-being-prompted-for-credentials-when-i-publish-a-report"></a>Почему при публикации отчета выдается приглашение к вводу учетных данных?  
Для развертывания отчета на сервере отчетов необходимо указать адрес сервера. Может открыться диалоговое окно Вход в службы Reporting Services с приглашением к вводу учетных данных.   
  
Неверно указано имя сервера отчетов  
  
  
Одной из распространенных ошибок при развертывании отчета на сервере отчетов, работающем в собственном режиме, является указание имени папки отчетов вместо имени сервера отчетов.   
  
Убедитесь, что в качестве URL-адреса сервера отчетов действительно указан адрес сервера отчетов (например, `http://localhost/reportserver`), а не адрес виртуального каталога диспетчера отчетов (например, `http://localhost/reports`). Если для сервера отчетов задан номер порта, отличный от применяемого по умолчанию (80), такой порт необходимо указать в адресе сервера отчетов (например, `http://localhost:81/reportserver`).   
  
 ## <a name="nothing-happens-when-i-toggle-items-in-my-published-report"></a>Ничего не происходит при переключении элементов в опубликованном отчете  
  При просмотре отчета в локальном окне предварительного просмотра можно переключать элементы в отчете, отображать и скрывать эти элементы. А при просмотре того же отчета после его публикации на сервере отчетов переключаемые элементы больше не работают.   
  
\<Имя сервера отчетов> содержит символ подчеркивания (_)  
  
Если отчет выполняется без ошибок, но не работают переключаемые элементы (например, при щелчке значка развертывания (+) ничего не происходит), проверьте имя компьютера, на котором установлен сервер отчетов. Если имя компьютера содержит символ подчеркивания, переключаемые элементы работать не будут. Это известная проблема и решить ее невозможно.   
  
Для выполнения отчетов с переключаемыми элементами следует использовать компьютер, в имени которого отсутствуют символы подчеркивания.  
  
## <a name="images-and-charts-do-not-load-when-i-use-run-as-and-a-browser-to-run-my-report"></a>Не загружаются изображения и диаграммы для выполнения отчета режима Run As и браузера  
При выполнении диспетчера отчетов в другом контексте безопасности в отчете могут быть не видны все его элементы.   
  
### <a name="insufficient-permissions-on-internet-temporary-file-folders"></a>Недостаточно разрешений в папках временных файлов Интернета  
  
В некоторых условиях при использовании диспетчера отчетов для просмотра опубликованных отчетов, которые включают диаграммы или изображения, эти элементы могут быть не видны. Например, при использовании команды Windows **Запуск от имени** для просмотра отчета с использованием другого контекста безопасности у вас могут отсутствовать разрешения в папке, в которой сервер отчетов кэширует диаграммы и изображения как временные файлы Интернета.   
  
Проверьте наличие разрешения на доступ к папкам, которые содержат кэшированные файлы.   
    
## <a name="see-also"></a>См. также:  
[Поддержка браузера для служб Reporting Services и Power View](../../reporting-services/browser-support-for-reporting-services-and-power-view.md)  
[Справочник по ошибкам и событиям (службы Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
[Устранение неполадок с извлечением данных с помощью отчетов служб Reporting Services](../../reporting-services/troubleshooting/troubleshoot-data-retrieval-issues-with-reporting-services-reports.md)  
[Устранение неполадок, связанных с подписками и доставкой служб Reporting Services](../../reporting-services/troubleshooting/troubleshoot-reporting-services-subscriptions-and-delivery.md)  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]

