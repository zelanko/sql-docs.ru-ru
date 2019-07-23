---
title: Сервер и каталог служб Integration Services (SSIS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 4b0911b650d164e1ae53281b70d6822353b1f2cb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070680"
---
# <a name="integration-services-ssis-server-and-catalog"></a>Сервер и каталог служб Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]вы можете выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Сервер служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляет собой экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , на котором размещена база данных **SSISDB** . В базе данных хранятся следующие объекты: пакеты, проекты, параметры, разрешения, свойства сервера и журнал операций.  
  
 База данных **SSISDB** предоставляет сведения об объектах в общих представлениях, к которым вы можете выполнить запрос. База данных также содержит хранимые процедуры, которые вы можете вызвать для управления объектами.  
  
 Прежде чем развертывать проекты на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимо создать каталог **SSISDB** .  
  
 Общие сведения о функциональных возможностях каталога SSISDB см. в разделе [Каталог служб SSIS](../../integration-services/catalog/ssis-catalog.md).  
  
## <a name="high-availability"></a>Высокий уровень доступности  
 Как и другие пользовательские базы данных, база данных **SSISDB** поддерживает зеркальное отображение базы данных и репликацию. Дополнительные сведения о зеркальном отображении и репликации см. в разделе [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Также вы можете обеспечить высокий уровень доступности SSISDB и содержимого с помощью служб SSIS и групп доступности AlwaysOn. Дополнительные сведения см. в статье [Always On для каталога служб SSIS (SSISDB)](ssis-catalog.md#always-on-for-ssis-catalog-ssisdb). Также см. запись в блоге Мэтта Мэссона (Matt Masson) [Службы SSIS с AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873) на сайте blogs.msdn.com.  
  
##  <a name="ssms"></a> Сервер служб Integration Services в среде SQL Server Management Studio  
 При подключении к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , на котором размещена база данных **SSISDB** , в обозревателе объектов отображаются следующие объекты:  
  
-   **База данных SSISDB**  
  
     База данных **SSISDB** появляется в узле **Базы данных** в обозревателе объектов. Вы можете создавать запросы к представлениям и вызывать хранимые процедуры для управления сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и объектами, которые хранятся на нем.  
  
-   **Каталоги служб Integration Services**  
  
     В узле **Каталоги служб Integration Services** есть папки для проектов и сред [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Просмотр списка пакетов на сервере служб Integration Services](../../integration-services/catalog/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Развертывание проектов и пакетов служб Integration Services (SSIS)](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Запуск пакетов служб Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Службы SSIS с AlwaysOn](https://go.microsoft.com/fwlink/?LinkId=255873) на сайте blogs.msdn.com.  
  
  
