---
title: MSSQLSERVER_3417 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a217a84e7c76d54c64aca4191737aa9166464e3c
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34319335"
---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3417|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_BADMASTER|  
|Текст сообщения|Невозможно восстановить базу данных master. Не удалось запустить SQL Server. Восстановите базу данных master из полной резервной копии, исправьте ее или перестройте. Дополнительные сведения о перестроении базы данных master см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server не может запустить базу данных **master**. Если базы данных **master** или **tempdb** не могут быть переведены в оперативный режим, то SQL Server запустить нельзя. Эта ошибка обычно предшествует другим ошибкам. Чтобы найти источник ошибки, просмотрите журнал ошибок.  
  
## <a name="user-action"></a>Действие пользователя  
Восстановите базу данных из резервной копии или исправьте ее.  
  
