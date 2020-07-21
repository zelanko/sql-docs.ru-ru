---
title: MSSQLSERVER_3417 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7eb6f5cc94cf23355897776965defd7d35dc79b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551579"
---
# <a name="mssqlserver_3417"></a>MSSQLSERVER_3417
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3417|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_BADMASTER|  
|Текст сообщения|Невозможно восстановить базу данных master. Не удалось запустить SQL Server. Восстановите базу данных master из полной резервной копии, исправьте ее или перестройте. Дополнительные сведения о перестроении базы данных master см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
 SQL Server не может запустить базу данных **master**. Если базы данных **master** или **tempdb** не могут быть переведены в оперативный режим, то SQL Server запустить нельзя. Эта ошибка обычно предшествует другим ошибкам. Чтобы найти источник ошибки, просмотрите журнал ошибок.  
  
## <a name="user-action"></a>Действие пользователя  
 Восстановите базу данных из резервной копии или исправьте ее.  
  
  
