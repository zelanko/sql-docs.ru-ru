---
title: "Службы Integration Services (SSIS) сервера и каталога | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 939f31adf1ab0a975bd4339dabab310ef9025049
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="integration-services-ssis-server-and-catalog"></a>Службы Integration Services (SSIS) сервера и каталога
  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]вы можете выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Сервер служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляет собой экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , на котором размещена база данных **SSISDB** . В базе данных хранятся следующие объекты: пакеты, проекты, параметры, разрешения, свойства сервера и журнал операций.  
  
 База данных **SSISDB** предоставляет сведения об объектах в общих представлениях, к которым вы можете выполнить запрос. База данных также содержит хранимые процедуры, которые вы можете вызвать для управления объектами.  
  
 Прежде чем развертывать проекты на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , необходимо создать каталог **SSISDB** .  
  
 Общие сведения о функциональных возможностях каталога SSISDB. в разделе [каталога служб SSIS](../../integration-services/service/ssis-catalog.md).  
  
## <a name="high-availability"></a>Высокий уровень доступности  
 Как и другие пользовательские базы данных, база данных **SSISDB** поддерживает зеркальное отображение базы данных и репликацию. Дополнительные сведения о зеркальном отображении и репликации см. в разделе [зеркального отображения базы данных &#40; SQL Server &#41; ](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Можно также предоставить высокий уровень доступности SSISDB и ее содержимое, делая использование служб SSIS и групп доступности AlwaysOn. Дополнительные сведения см. в разделе записи блога, Matt Masson [служб SSIS с Always On](http://go.microsoft.com/fwlink/?LinkId=255873), на сайте blogs.msdn.com.  
  
##  <a name="ssms"></a> Сервер служб Integration Services в среде SQL Server Management Studio  
 При подключении к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , на котором размещена база данных **SSISDB** , в обозревателе объектов отображаются следующие объекты:  
  
-   **База данных SSISDB**  
  
     База данных **SSISDB** появляется в узле **Базы данных** в обозревателе объектов. Вы можете создавать запросы к представлениям и вызывать хранимые процедуры для управления сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и объектами, которые хранятся на нем.  
  
-   **Каталоги служб Integration Services**  
  
     В узле **Каталоги служб Integration Services** есть папки для проектов и сред [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Связанные задачи  
  
-   [Просмотр списка пакетов на сервере служб Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Развертывание служб Integration Services (SSIS) проектов и пакетов](../../integration-services/packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
-   [Запуск пакетов служб Integration Services (SSIS)](../../integration-services/packages/run-integration-services-ssis-packages.md)  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [служб SSIS с Always On](http://go.microsoft.com/fwlink/?LinkId=255873), на сайте blogs.msdn.com.  
  
  
