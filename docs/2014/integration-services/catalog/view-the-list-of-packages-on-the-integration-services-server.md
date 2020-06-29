---
title: Просмотр списка пакетов на сервере служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 47b30f9ea0b2abae73f9260b873b7c8436c423eb
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439011"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Просмотр списка пакетов на хранимом сервере служб Integration Services
  Список хранимых на сервере [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] пакетов вы можете просмотреть одним из двух способов.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] доступ  
 Чтобы просмотреть список пакетов, сохраненных на сервере, создайте запрос к представлению [catalog.packages (SSISDB Database)](/sql/integration-services/system-views/catalog-packages-ssisdb-database).  
  
 В [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
 Для просмотра пакетов, хранящихся на сервере, с помощью обозревателя объектов в среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]выполните следующие действия.  
  
### <a name="to-view-packages-using-ssmanstudiofull"></a>Просмотр пакетов с помощью [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]установите соединение с сервером служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Другими словами, подключитесь к экземпляру компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] , размещающего базу данных служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] .  
  
2.  В обозревателе объектов разверните дерево для отображения узла **Каталоги служб Integration Services** .  
  
3.  Для отображения узла **SSISDB** разверните узел **Каталоги служб Integration Services** .  
  
4.  Разверните узел **SSISDB** для отображения списка из одной или более папок. Каждая папка содержит один или более проектов в папке **Проекты** , а каждый проект содержит один или более пакетов в папке **Пакеты** .  
  
  
