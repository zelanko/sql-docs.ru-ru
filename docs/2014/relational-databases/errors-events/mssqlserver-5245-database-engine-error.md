---
title: MSSQLSERVER_ 5245 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 30b37236b321fc90372914f2af48a652d41fbe03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62913602"
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5245|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Текст сообщения|Объект с Идентификатором O_ID (объект «NAME»): DBCC не удалось получить блокировку для этого объекта, из-за превышения времени ожидания блокировки. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
 Истекло время ожидания командой DBCC блокировки таблицы для заданного объекта.  
  
## <a name="user-action"></a>Действие пользователя  
 Повторно выполните команду DBCC.  
  
  
