---
title: Просмотр списка пакетов на сервере служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68c9fca56732dd0757d7c602152b523132d5eafc
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/26/2019
ms.locfileid: "71294883"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Просмотр списка пакетов на хранимом сервере служб Integration Services

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
  
  
