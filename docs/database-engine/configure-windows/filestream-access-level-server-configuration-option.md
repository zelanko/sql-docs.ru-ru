---
title: "Параметр конфигурации сервера \"filestream access level\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], access level
- filestream access level
ms.assetid: b88f6ff2-795e-4730-bfb8-dbc6a958f2ad
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 625dcd6009f4cfe37ac1e4e0d1d2db26ea9e1e66
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="filestream-access-level-server-configuration-option"></a>Параметр конфигурации сервера «уровень доступа файлового потока»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Параметр файлового потока filestream_access_level используется для изменения уровня доступа к данным типа FILESTREAM для данного экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]  
>  Чтобы этот параметр вступил в силу, необходимо включить настройки администрирования Windows для FILESTREAM. Эти параметры можно включить при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
|Значение|Определение|  
|-----------|----------------|  
|0|Отключает поддержку FILESTREAM для данного экземпляра.|  
|1|Включает FILESTREAM для доступа с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|2|Включает FILESTREAM для доступа с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] и потокового доступа Win32.|  
  
## <a name="see-also"></a>См. также:  
 [Настройка компонента Database Engine — Filestream](http://msdn.microsoft.com/library/641a10a1-ae52-4d26-8f1c-a032a4aeff02)   
 [Включение и настройка FILESTREAM](../../relational-databases/blob/enable-and-configure-filestream.md)  
  
  

