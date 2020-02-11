---
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72fd78120a099da64a175f85fef64286be7aec76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67995873"
---
# <a name="localdb_error_instance_already_shared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|284|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Указанный экземпляр локальной базы данных уже используется совместно.|  
  
## <a name="explanation"></a>Объяснение  
 Указанный экземпляр локальной базы данных уже используется совместно под другим общим именем.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключить включенный совместный доступ к экземпляру, прежде чем снова предоставлять его в совместный доступ под другим общим именем.  
  
  
