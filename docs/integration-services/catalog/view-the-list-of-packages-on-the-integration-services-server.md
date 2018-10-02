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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 895833726af07b7b650ab26c033eb1ee8018b499
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47682332"
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
  
  
