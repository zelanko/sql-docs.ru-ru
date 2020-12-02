---
description: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
title: LOCALDB_ERROR_INSTANCE_ALREADY_SHARED | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: 35b4d6fa-ebb9-49d3-aaab-d4e37b6f3760
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 4e4b290daa5dee2fb2a7cc5d3d608b81a7eae438
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506272"
---
# <a name="localdb_error_instance_already_shared"></a>LOCALDB_ERROR_INSTANCE_ALREADY_SHARED
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Сведения  
  
| attribute | Значение |
| --------- | ----- |
|Название продукта|SQL Server|  
|Идентификатор события|284|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Указанный экземпляр локальной базы данных уже используется совместно.|  
  
## <a name="explanation"></a>Объяснение  
 Указанный экземпляр локальной базы данных уже используется совместно под другим общим именем.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключить включенный совместный доступ к экземпляру, прежде чем снова предоставлять его в совместный доступ под другим общим именем.  
  
  
