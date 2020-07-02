---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 08ea1c27612d0f0b47c545966fac22f1abd95c81
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85641828"
---
# <a name="localdb_error_instance_folder_path_too_long"></a>LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|260|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Длина полного пути к папке экземпляра локальной базы данных превышает MAX_PATH. Экземпляр должен храниться в папке:%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server локальное \\ имя экземпляра дб\инстанцес<\> .|  
  
## <a name="explanation"></a>Объяснение  
 Длина пути к месту хранения экземпляра больше MAX_PATH.  
  
## <a name="user-action"></a>Действие пользователя  
 Создайте новый путь, длина которого меньше MAX_PATH.  
  
  
