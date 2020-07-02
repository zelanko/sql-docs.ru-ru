---
title: LOCALDB_ERROR_INSUFFICIENT_BUFFER | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: ff67bda8-7e5c-4b06-8d7b-9985b6059a98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b21d9137483b7d7b76c6e91f0fd44363bf58f7c
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85641796"
---
# <a name="localdb_error_insufficient_buffer"></a>LOCALDB_ERROR_INSUFFICIENT_BUFFER
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|276|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Буфер, переданный методу API экземпляра локальной базы данных, имеет недостаточный размер.|  
  
## <a name="explanation"></a>Объяснение  
 Размер входного буфера является недостаточным, а усечение не было запрошено.  
  
## <a name="user-action"></a>Действие пользователя  
 Предоставьте буфер указанного размера.  
  
  
