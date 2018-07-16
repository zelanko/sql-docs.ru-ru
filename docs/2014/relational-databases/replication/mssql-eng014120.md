---
title: MSSQL_ENG014120 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014120 error
ms.assetid: 6b169a3b-30da-4981-b998-b52d61811572
caps.latest.revision: 13
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb15b59a86b60d12d65716341062d6c670ad4a5f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299904"
---
# <a name="mssqleng014120"></a>MSSQL_ENG014120
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|14120|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удается удалить базу данных "%s" распространителя. Эта база данных распространителя связана с издателем.|  
  
## <a name="explanation"></a>Объяснение  
 В базе данных распространителя хранятся метаданные и данные журнала для всех типов репликации и транзакций, относящихся к репликации транзакций. Эта ошибка возникает при попытке удалить базу данных распространителя, связанную с одним или несколькими издателями.  
  
## <a name="user-action"></a>Действие пользователя  
 Для удаления базы данных распространителя следует вначале удалить связь между распространителем и издателем. Дополнительные сведения см. в статье [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Справочник по ошибкам и событиям (репликация)](errors-and-events-reference-replication.md)   
 [Настройка распространения](configure-distribution.md)  
  
  
