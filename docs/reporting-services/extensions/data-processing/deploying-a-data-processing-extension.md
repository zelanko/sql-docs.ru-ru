---
title: Развертывание модуля обработки данных | Документы Майкрософт
description: Узнайте, как настроить обнаружение модуля обработки данных Reporting Services для сервера отчетов и конструктора отчетов.
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 073ff624016cc671883fea551ad4ebd392b54ea6
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529655"
---
# <a name="deploying-a-data-processing-extension"></a>Развертывание модуля обработки данных
  После создания модуля обработки данных для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и компиляции его в библиотеку [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] необходимо сделать модуль доступным для обнаружения сервером отчетов и конструктором отчетов. Для этого нужно просто скопировать модуль в соответствующие каталоги и добавить записи в соответствующие файлы конфигурации служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
## <a name="configuration-file-extension-element"></a>Элемент Extension в файле конфигурации  
 Модули обработки данных, развертываемые на сервере отчетов или в конструкторе отчетов, необходимо вставить в файлы конфигурации в виде элементов **Extension**. Для сервера отчетов используется файл RSReportServer.config, а для конструктора отчетов — файл RSReportDesigner.config.  
  
 В следующей таблице описаны атрибуты элемента **Extension** для модулей обработки данных.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|**Имя**|Уникальное имя модуля, например «SQL» для модуля обработки данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] или «OLEDB» для модуля обработки данных OLE DB. Длина атрибута **Name** не должна превышать 255 символов. Имя должно быть уникальным среди всех элементов, вложенных в элемент **Extension** файла конфигурации.|  
|**Тип**|Список с разделителями-запятыми, содержащий полное пространство имен и имя сборки.|  
|**Visible**|Значение **false** показывает, что модуль обработки данных не должен отображаться в пользовательском интерфейсе. Если атрибут не указан, по умолчанию используется значение **true**.|  
  
 Дополнительные сведения о файлах RSReportServer.config и RSReportDesigner.config см. в разделе [Файлы конфигурации служб Reporting Services](../../../reporting-services/report-server/reporting-services-configuration-files.md).  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Руководство. Развертывание модуля обработки данных на сервере отчетов](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-a-report-server.md)|Описывает развертывание модуля обработки данных на сервере отчетов.|  
|[Руководство. Развертывание модуля обработки данных в конструкторе отчетов](../../../reporting-services/extensions/data-processing/deploying-a-data-processing-extension-to-report-designer.md)|Описывает развертывание модуля обработки данных в конструкторе отчетов.|  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Реализация модуля обработки данных](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
