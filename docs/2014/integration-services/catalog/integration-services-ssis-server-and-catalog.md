---
title: Службы Integration Services (SSIS) сервера | Документы Microsoft
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packages [Integration Services], managing
- managing packages [Integration Services]
ms.assetid: 6d667bba-7c25-492a-8f4d-70ebaca28f40
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 69598f8ca412e32a76ea841f9a234d01c6847718
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194084"
---
# <a name="integration-services-ssis-server"></a>Службы Integration Services (SSIS Server)
  После разработки и тестирования пакетов в [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]вы можете выполнить развертывание проектов, содержащих пакеты, на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
 Сервер служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] представляет собой экземпляр [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], на котором размещена база данных `SSISDB`. В базе данных хранятся следующие объекты: пакеты, проекты, параметры, разрешения, свойства сервера и журнал операций.  
  
 База данных `SSISDB` предоставляет сведения об объектах в общих представлениях, к которым вы можете выполнить запрос. База данных также содержит хранимые процедуры, которые вы можете вызвать для управления объектами.  
  
 Прежде чем развертывать проекты на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], необходимо создать каталог `SSISDB`.  
  
 Общие сведения о функциональных возможностях каталога SSISDB см. в разделе [Каталог служб SSIS](ssis-catalog.md).  
  
## <a name="high-availability"></a>Высокий уровень доступности  
 Как и другие пользовательские базы данных `SSISDB` поддерживает зеркальное отображение базы данных и репликация базы данных. Дополнительные сведения о зеркальном отображении и репликации см. в разделе [Зеркальное отображение базы данных (SQL Server)](../../database-engine/database-mirroring/database-mirroring-sql-server.md).  
  
 Также вы можете обеспечить высокий уровень доступности SSISDB и содержимого с помощью служб SSIS и групп доступности AlwaysOn. Дополнительные сведения см. в записи блога Метта Мэйсона (Matt Masson) [Службы SSIS с AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873)на сайте blogs.msdn.com.  
  
##  <a name="ssms"></a> Сервер служб Integration Services в среде SQL Server Management Studio  
 При подключении к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], на котором размещена база данных `SSISDB`, в обозревателе объектов отображаются следующие объекты:  
  
-   **База данных SSISDB**  
  
     `SSISDB` Базы данных отображается в узле **баз данных** в обозревателе объектов. Вы можете создавать запросы к представлениям и вызывать хранимые процедуры для управления сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] и объектами, которые хранятся на нем.  
  
-   **Каталоги служб Integration Services**  
  
     В узле **Каталоги служб Integration Services** есть папки для проектов и сред [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [Создание каталога служб SSIS](../create-the-ssis-catalog.md)  
  
-   [Просмотр списка пакетов на сервере служб Integration Services](view-the-list-of-packages-on-the-integration-services-server.md)  
  
-   [Развертывание проектов на сервере служб Integration Services](../deploy-projects-to-integration-services-server.md)  
  
-   [Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio](../run-a-package-on-the-ssis-server-using-sql-server-management-studio.md)  
  
## <a name="related-content"></a>См. также  
 Запись в блоге [Службы SSIS с AlwaysOn](http://go.microsoft.com/fwlink/?LinkId=255873)на blogs.msdn.com.  
  
  