---
title: Публикация отчетов на сервере отчетов | Документы Майкрософт
ms.custom: ''
ms.date: 06/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: reports
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
caps.latest.revision: 47
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 9a69b67fcbc9d047526ff0c30883731543a826a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="publishing-reports-to-a-report-server"></a>Публикация отчетов на сервере отчетов
  После создания и проверки отчета или набора отчетов можно воспользоваться функциями развертывания в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] для публикации отчетов на сервере отчетов. Можно опубликовать отдельные отчеты или проект "Сервер отчетов", включающий несколько отчетов и источников данных. Публикация проекта сервера отчетов — это самый простой способ публикации нескольких отчетов. [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] использует термин *развернуть*вместо термина *опубликовать*. Два этих термина взаимозаменяемы.  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] предусматривает конфигурации проекта для управления публикацией отчета. Конфигурация определяет местоположение сервера отчетов, версию служб SQL Server Reporting Services, установленных на сервере отчетов, перезапись источников данных, опубликованных на сервере отчетов, и т. д. Например, конфигурацию "Отладка" можно опубликовать на сервере, отличном от сервера, на котором находится конфигурация "Выпуск". Помимо использования конфигураций, имеющихся в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] , можно создавать дополнительные конфигурации.  
 
## <a name="requirements-to-publish"></a>Требования для публикации
Разрешение определяется параметрами безопасности на основе ролей, заданными администратором сервера отчетов. Разрешения на операции публикации обычно предоставляются через роль **Издатель**.  
  
## <a name="project-configurations"></a>Конфигурации проекта  
 Среда создания отчетов может иметь несколько серверов отчетов и разные установленные версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Можно создать несколько конфигураций и использовать одну из них в зависимости от сценария развертывания. Конфигурации проекта включают свойства для построения отчетов, например папку, в которой временно сохраняются отчеты о сборке и способах решения проблем сборки. Конфигурации также имеют свойства, используемые для обозначения местоположения и версии сервера отчетов, папок на сервере отчетов.  
  
 По умолчанию среда [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] предоставляет три конфигурации проекта: **DebugLocal**, **Debug**и **Release**. Конфигурация по умолчанию — DebugLocal. Как правило, конфигурация DebugLocal служит для просмотра отчетов в локальном окне просмотра, конфигурация Debug — для публикации отчетов на тестовом сервере, а конфигурация Release — для публикации отчетов на рабочем сервере. Раскрывающийся список конфигураций решения на стандартной панели инструментов отображает активную конфигурацию. Для использования другой конфигурации выберите ее из списка.  
  
 ![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png) 
  
 Дополнительные сведения см. в следующих разделах:
 + [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md)
 + [Развертывание и поддержка версий в SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)
 + [Задание свойств развертывания для проектов Reporting Services в SSDT](../../reporting-services/tools/set-deployment-properties-reporting-services.md)
  
## <a name="to-publish-all-reports-in-a-project"></a>Публикация всех отчетов в проекте  
  
В меню **Сборка** выберите пункт **Развернуть \<имя проекта отчета>**. Или в обозревателе решений щелкните правой кнопкой мыши проект отчета и выберите команду **Развернуть**. Можно просмотреть состояние процесса публикации в окне вывода.  
  
При развертывании проекта «Сервер отчетов» будут развернуты и общие источники данных проекта отчета. Все отчеты разворачиваются с использованием одной конфигурации проекта: на одном сервере отчетов, в одной папке сервера и т. д. Публикацию отчетов на разных серверах необходимо либо выполнять последовательно, либо включить в проект «Сервер отчетов» только необходимые отчеты. Решение может включать несколько проектов сервера отчетов, а использование нескольких проектов поможет облегчить процесс управления развертыванием отчетов, так как дает возможность использовать разные конфигурации для развертывания разных проектов. 
  
## <a name="to-publish-a-single-report"></a>Публикация одного отчета  
  
В обозревателе решений щелкните правой кнопкой мыши отчет, а затем выберите пункт **Развернуть**. Можно просмотреть состояние процесса публикации в окне вывода.  
  
 При публикации отчета необходимо также выполнить развертывание общих источников данных, которые в нем используются.   
 Если не нужно публиковать все отчеты в проекте, то можно выбрать публикацию одного отчета. Для этого выберите конфигурацию, в которой разворачивается отчет (например, конфигурацию Release), правой кнопкой мыши щелкните отчет и выберите пункт **Развернуть**.  
  
 Если отчет использует общий источник данных, то необходимо также развернуть и его, иначе развернутый отчет не будет работать. Щелкните правой кнопкой мыши общий источник данных и выберите пункт **Развернуть**.  
  
 Необходимо указать URL-адрес целевого сервера на сервере отчетов и, возможно, изменить папки по умолчанию, в которых буду разворачиваться отчеты и общие источники данных.  

  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [Управление содержимым сервера отчетов (службы Reporting Services в основном режиме)](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [Обновление отчетов](../../reporting-services/install-windows/upgrade-reports.md)  
  
  
