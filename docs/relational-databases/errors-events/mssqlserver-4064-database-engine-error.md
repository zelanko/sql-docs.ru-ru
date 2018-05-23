---
title: MSSQLSERVER_4064 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 4064 (Database Engine error)
ms.assetid: 32112b90-0a2f-4834-a027-756811732be7
caps.latest.revision: 19
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c58d5a054999da21c3b2850e529a067df0edfb22
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
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
  
