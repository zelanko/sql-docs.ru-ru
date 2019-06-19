---
title: MSSQLSERVER_11409 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8dcb8bba87d83f4127bc7358c45b5f5a7664d46b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048317"
---
# <a name="mssqlserver11409"></a>MSSQLSERVER_11409
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|11409|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|ALTERCOL_COLSET_DROP|  
|Текст сообщения|Не удалось удалить набор столбцов "%.*ls" в таблице "%.\*ls", поскольку таблица содержит больше 1025 столбцов.|  
  
## <a name="explanation"></a>Объяснение  
Таблицы могут содержать максимум 1024 столбца, которые не определены как разреженные или вычисляемые. Если наличие разреженных столбцов становится причиной превышения 1024 столбцов в таблице, для таблицы должен быть определен набор столбцов. В указанной таблице больше 1024 столбцов и предпринята попытка удалить набор столбцов.  
  
## <a name="user-action"></a>Действие пользователя  
Текущий состав столбцов в таблице таков, что требует сохранения набора столбцов.  
  
Чтобы удалить набор столбцов, сначала удаляйте из таблицы столбцы, пока их количество не станет меньше или равно 1024 столбцам. После этого можно удалить набор столбцов.  
  
