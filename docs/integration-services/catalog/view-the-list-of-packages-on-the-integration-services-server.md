---
title: "Просмотр списка пакетов на сервере служб Integration Services | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: service
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6b33dde95ed3ae99e27affa1ab1efdfbd29bfe6e
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Просмотр списка пакетов на хранимом сервере служб Integration Services
  Список хранимых на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетов вы можете просмотреть одним из двух способов.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] доступ  
 Чтобы просмотреть список пакетов, сохраненных на сервере, создайте запрос к представлению [catalog.packages (SSISDB Database)](../../integration-services/system-views/catalog-packages-ssisdb-database.md).  
  
 In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
 Для просмотра пакетов, хранящихся на сервере, с помощью обозревателя объектов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]выполните следующие действия.  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>Просмотр пакетов с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Другими словами, подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , размещающего базу данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Для отображения узла **SSISDB** разверните узел **Каталоги служб Integration Services** .  
  
4.  Разверните узел **SSISDB** для отображения списка из одной или более папок. Каждая папка содержит один или более проектов в папке **Проекты** , а каждый проект содержит один или более пакетов в папке **Пакеты** .  
  
  
