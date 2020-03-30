---
title: Удаление модуля подготовки отчетов | Документы Майкрософт
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 0ee3563074e2379061006b72f55dab99f80094cd
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "63193455"
---
# <a name="removing-a-rendering-extension"></a>Удаление модуля подготовки отчетов
  Чтобы удалить модуль подготовки отчетов [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], просто удалите элемент **Extension** для модуля подготовки отчетов из файла rsreportserver.config, находящегося в папке **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<Имя экземпляра>\Reporting Services\ReportServer**. Если созданы записи для конструктора отчетов, а также для сервера отчетов, удалите элемент **Extension** из [файла конфигурации RSReportDesigner](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md). После удаления сведений о конфигурации модуль подготовки отчетов становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также:  
 [Файлы конфигурации служб Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [Реализация модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [Рекомендации по обеспечению безопасности для модулей](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [Развертывание модуля подготовки отчетов](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
