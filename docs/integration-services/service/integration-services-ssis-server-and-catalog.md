---
title: "Служб Integration Services (SSIS) сервера и каталога | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "пакеты [службы Integration Services], управление"
  - "управление пакетами [службы Integration Services]"
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 38
---
# Служб Integration Services (SSIS) сервера и каталога
  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]вы можете выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Сервер является экземпляром [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] на котором размещена **SSISDB** базы данных. В базе данных хранятся следующие объекты: пакеты, проекты, параметры, разрешения, свойства сервера и журнал операций.  
  
 База данных **SSISDB** предоставляет сведения об объектах в общих представлениях, к которым вы можете выполнить запрос. База данных также содержит хранимые процедуры, которые вы можете вызвать для управления объектами.  
  
 Прежде чем развертывать проекты на [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] сервере, необходимо создать **SSISDB** каталога.  
  
 В разделе Общие сведения о функциональных возможностях каталога SSISDB [каталог служб SSIS](../../integration-services/service/ssis-catalog.md).  
  
## Высокий уровень доступности  
 Как и другие пользовательские базы данных, база данных **SSISDB** поддерживает зеркальное отображение базы данных и репликацию. Дополнительные сведения о зеркальном отображении и репликации см. в разделе [зеркального отображения базы данных & #40; SQL Server & #41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Можно также предоставить высокий уровень доступности SSISDB и ее содержимое, сделав использование служб SSIS и групп доступности AlwaysOn. Дополнительные сведения см. в разделе записи блога, Matt Masson [служб SSIS с Always On](http://go.microsoft.com/fwlink/?LinkId=255873), на сайте blogs.msdn.com.  
  
##  <a name="ssms"></a> Сервер служб Integration Services в среде SQL Server Management Studio  
 При подключении к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] на котором размещена **SSISDB** базы данных, отображаются следующие объекты в обозревателе объектов:  
  
-   **База данных SSISDB**  
  
     База данных **SSISDB** появляется в узле **Базы данных** в обозревателе объектов. Вы можете создавать запросы к представлениям и вызывать хранимые процедуры для управления сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и объектами, которые хранятся на нем.  
  
-   **Каталоги служб Integration Services**  
  
     В узле **Каталоги служб Integration Services** есть папки для проектов и сред [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## Связанные задачи  
  
-   [Создание каталога служб SSIS](../../integration-services/service/create-the-ssis-catalog.md)  
  
-   [Просмотр списка пакетов на хранимом сервере служб Integration Services](../../integration-services/service/view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Развертывание проектов на сервере служб Integration Services](../../integration-services/packages/deploy-projects-to-integration-services-server.md)  
  
-   [Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio](../../integration-services/packages/run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## См. также  
 Запись в блоге [служб SSIS с Always On](http://go.microsoft.com/fwlink/?LinkId=255873), на сайте blogs.msdn.com.  
  
  