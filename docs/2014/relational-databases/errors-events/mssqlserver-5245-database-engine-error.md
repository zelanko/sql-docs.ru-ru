---
title: MSSQLSERVER_ 5245 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 64a63825586a603e2938cd57d98d38d555420dd6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087609"
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
|Текст сообщения|Объект с идентификатором O_ID (объект "NAME"): команде DBCC не удалось заблокировать этот объект из-за превышения времени ожидания запроса на блокировку. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
 Истекло время ожидания командой DBCC блокировки таблицы для заданного объекта.  
  
## <a name="user-action"></a>Действие пользователя  
 Повторно выполните команду DBCC.  
  
  