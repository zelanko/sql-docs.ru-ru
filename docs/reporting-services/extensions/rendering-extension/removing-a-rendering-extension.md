---
title: "Удаление модуля подготовки отчетов | Документы Microsoft"
ms.custom: 
ms.date: 03/18/2017
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
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ea37cf7ac15504a00aeb0f1379e9d48a71231e1c
ms.contentlocale: ru-ru
ms.lasthandoff: 08/12/2017

---
# <a name="removing-a-rendering-extension"></a>Удаление модуля подготовки отчетов
  Чтобы удалить [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль подготовки отчетов, просто удалите **расширения** элемент для модуля подготовки из файла rsreportserver.config, расположенного в **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Имя экземпляра > \Reporting Services\ReportServer** папки. Если выполнены записи для конструктора отчетов, а также сервер отчетов, удалите **расширения** элемент из [файл конфигурации RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md) также. После удаления сведений о конфигурации модуль подготовки отчетов становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб отчетов](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Реализация модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Вопросы безопасности для расширений](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Развертывание модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
