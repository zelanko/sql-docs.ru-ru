---
title: Издатели | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.enablepublishers.f1
ms.assetid: 116cd6a5-32ac-4273-81a2-d184408e0f07
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 416a4dd7b2c4d68860263b7417d2c48ddffd644b
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769759"
---
# <a name="publishers"></a>Издатели
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Можно разрешить другим издателям использовать этот распространитель. Учтите, что разрешение для издателя использовать данный сервер в качестве своего удаленного распространителя не превращает данный сервер в издатель. Необходимо подключиться к издателю, настроить его для публикации и выбрать этот сервер в качестве распространителя. Возможна настройка издателя и выбор распространителя с помощью мастера создания публикаций.  
  
 Серверы, выбранные в качестве издателей, будут использовать базу данных распространителя, указанную на странице **База данных распространителя** данного мастера. Если нужно использовать другую базу данных распространителя, не включайте издатель сейчас. Вместо этого используйте для добавления издателей диалоговое окно **Свойства распространителя** после завершения работы мастера настройки распространения.  
  
## <a name="options"></a>Параметры  
 **Издатели**  
 Выберите серверы, которым разрешено использование данного распространителя. Нажмите кнопку свойств ( **...** ) рядом с издателем для просмотра и задания дополнительных свойств.  
  
 **Добавить**  
 Если нужный сервер не представлен в списке, нажмите кнопку **Добавить** , чтобы добавить издателей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Oracle к списку доступных издателей.  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)  
  
  
