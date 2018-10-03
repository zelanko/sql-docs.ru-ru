---
title: Удаление модуля подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4e9abf2254d9c9710e68df9b488321b4ae4c1b16
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132964"
---
# <a name="removing-a-rendering-extension"></a>Удаление модуля подготовки отчетов
  Чтобы удалить [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модуль подготовки отчетов, просто удалите `Extension` элемент для модуля подготовки из файла rsreportserver.config, расположенного в **%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\< Имя экземпляра > \Reporting Services\ReportServer** папки. Если выполнены записи для конструктора отчетов, а также сервер отчетов, удалите `Extension` элемент из [файл конфигурации RSReportDesigner](../../report-server/rsreportdesigner-configuration-file.md) также. После удаления сведений о конфигурации модуль подготовки отчетов становится недоступным компоненту.  
  
## <a name="see-also"></a>См. также  
 [Файлы конфигурации служб Reporting Services](../../report-server/reporting-services-configuration-files.md)   
 [Реализация модуля подготовки отчетов](implementing-a-rendering-extension.md)   
 [Общие сведения о модулях подготовки отчетов](rendering-extensions-overview.md)   
 [Реализация интерфейса IRenderingExtension](implementing-the-irenderingextension-interface.md)   
 [Рекомендации по обеспечению безопасности для модулей](../security-considerations-for-extensions.md)   
 [Развертывание модуля подготовки отчетов](deploying-a-rendering-extension.md)  
  
  
