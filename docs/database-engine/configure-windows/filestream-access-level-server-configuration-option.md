---
title: Параметр конфигурации сервера "filestream access level" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 81d5627c46f12a033de5dab881f2c6de7f99e2f4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66785327"
---
# <a name="filestream-access-level-server-configuration-option"></a>Параметр конфигурации сервера «уровень доступа файлового потока»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр файлового потока filestream_access_level используется для изменения уровня доступа к данным типа FILESTREAM для данного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы этот параметр вступил в силу, необходимо включить настройки администрирования Windows для FILESTREAM. Эти параметры можно включить при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Значение|Определение|  
|-----------|----------------|  
|0|Отключает поддержку FILESTREAM для данного экземпляра.|  
|1|Включает FILESTREAM для доступа с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|2|Включает FILESTREAM для доступа с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] и потокового доступа Win32.|  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента Database Engine — Filestream](https://msdn.microsoft.com/library/641a10a1-ae52-4d26-8f1c-a032a4aeff02)   
 [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  
