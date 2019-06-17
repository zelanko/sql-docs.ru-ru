---
title: Удаление модуля подготовки отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62988064"
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
  
  
