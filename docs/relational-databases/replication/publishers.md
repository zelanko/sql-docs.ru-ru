---
description: Издатели
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
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 6aa802cc14b494a3892fea71d2ddbc99f42c8749
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97479835"
---
# <a name="publishers"></a>Издатели
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Можно разрешить другим издателям использовать этот распространитель. Учтите, что разрешение для издателя использовать данный сервер в качестве своего удаленного распространителя не превращает данный сервер в издатель. Необходимо подключиться к издателю, настроить его для публикации и выбрать этот сервер в качестве распространителя. Возможна настройка издателя и выбор распространителя с помощью мастера создания публикаций.  
  
 Серверы, выбранные в качестве издателей, будут использовать базу данных распространителя, указанную на странице **База данных распространителя** данного мастера. Если нужно использовать другую базу данных распространителя, не включайте издатель сейчас. Вместо этого используйте для добавления издателей диалоговое окно **Свойства распространителя** после завершения работы мастера настройки распространения.  
  
## <a name="options"></a>Параметры  
 **Издатели**  
 Выберите серверы, которым разрешено использование данного распространителя. Нажмите кнопку свойств ( **...** ) рядом с издателем для просмотра и задания дополнительных свойств.  
  
 **Добавление**  
 Если нужный сервер не представлен в списке, нажмите кнопку **Добавить**, чтобы добавить издателей [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Oracle к списку доступных издателей.  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)  
  
  
