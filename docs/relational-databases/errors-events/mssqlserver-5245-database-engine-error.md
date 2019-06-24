---
title: MSSQLSERVER_ 5245 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5245 (Database Engine error)
ms.assetid: 6005c9ec-ccdd-4def-9eb4-37cdb599ddb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a5a1c3882a310a5fb0debb52ccfc7c0e7cdd35de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63456595"
---
# <a name="mssqlserver5245"></a>MSSQLSERVER_5245
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5245|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_TABLE_LOCK_TIMEOUT_EXCEEDED|  
|Текст сообщения|Объект с идентификатором O_ID (объект "имя_объекта"): команде DBCC не удалось заблокировать этот объект из-за превышения времени ожидания запроса на блокировку. Этот объект пропущен и останется необработанным.|  
  
## <a name="explanation"></a>Объяснение  
Истекло время ожидания командой DBCC блокировки таблицы для заданного объекта.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно выполните команду DBCC.  
  
