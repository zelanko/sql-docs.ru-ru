---
title: MSSQLSERVER_4064 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1f391f46a59ad523eabab803bf1faa3090465d25
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028748"
---
# <a name="mssqlserver4064"></a>MSSQLSERVER_4064
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|4064|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DB_UFAIL_FATAL|  
|Текст сообщения|Невозможно открыть пользовательскую базу данных по умолчанию. Ошибка входа.|  
  
## <a name="explanation"></a>Объяснение  
Имени входа SQL Server не удалось выполнить соединение из-за проблемы с базой данных по умолчанию. Либо указана недопустимая база данных, либо у имени входа нет разрешения CONNECT для этой базы данных.  
  
## <a name="user-action"></a>Действие пользователя  
При помощи инструкции ALTER LOGIN измените базу данных по умолчанию для этого имени входа. Предоставьте имени входа разрешение CONNECT.  
  
