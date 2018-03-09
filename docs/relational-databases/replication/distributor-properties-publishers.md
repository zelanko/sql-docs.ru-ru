---
title: "Свойства распространителя, страница \"Издатели\" | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.configdistwizard.distproperties.publishers.f1
helpviewer_keywords: Distributor Properties dialog box
ms.assetid: 31c81898-11ca-4d2f-afea-2fbc71e19ce4
caps.latest.revision: "21"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c917bfd8dc3094c5cea0a75027f3ebe9065d68bb
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="distributor-properties-publishers"></a>Свойства распространителя, страница «Издатели»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Страница **Издатели** диалогового окна **Свойства распространителя** позволяет включить использование издателями данного распространителя. Также можно устанавливать свойства, связанные с этими издателями. Учтите, что разрешение для издателя использовать данный сервер в качестве своего удаленного распространителя не превращает данный сервер в издатель. Необходимо подключиться к издателю, настроить его для публикации и выбрать этот сервер в качестве распространителя. Возможна настройка издателя и выбор распространителя с помощью мастера создания публикаций.  
  
## <a name="options"></a>Параметры  
 **Издатели**  
 Выберите серверы, которым разрешено использование данного распространителя. Нажмите кнопку свойств ( **(...)** ) рядом с издателем для просмотра и установки дополнительных свойств.  
  
 **Добавить**  
 Если нужный сервер не представлен в списке, нажмите кнопку **Добавить** , чтобы добавить издателей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Oracle к списку доступных издателей. Если добавляемый сервер будет первым использовать данного распространителя в качестве удаленного распространителя, то будет выдано приглашение к вводу пароля административного соединения.  
  
 **Пароль административного соединения**  
 Используется для задания или обновления пароля для соединения, создаваемого репликацией между издателем и удаленным распространителем с использованием имени входа **distributor_admin** :  
  
-   Если распространитель выступает только в качестве локального распространителя, то данный пароль формируется случайным образом и настраивается автоматически.  
  
-   Если у распространителя уже есть удаленный издатель, то пароль был первоначально введен на этой странице или на странице **Пароль распространителя** мастера настройки распространения.  
  
-   При включении первого удаленного издателя для данного распространителя будет выдано приглашение к вводу пароля.  
  
 Дополнительные сведения о безопасности распространителей см. в разделе [Защита распространителя](../../relational-databases/replication/security/secure-the-distributor.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
