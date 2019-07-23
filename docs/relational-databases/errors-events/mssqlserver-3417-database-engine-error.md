---
title: MSSQLSERVER_3417 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1a9c91c785854b796351d7e3dfce12eacf044827
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68132414"
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
  
