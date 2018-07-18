---
title: MSSQLSERVER_3431 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
caps.latest.revision: 18
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 02724ea8bf358294af5e5dcd6c8f549d80010391
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37426463"
---
# <a name="mssqlserver3431"></a>MSSQLSERVER_3431
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3431|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|UNRESOLVED_XACT|  
|Текст сообщения|Не удалось восстановить базу данных «%.*ls» (идентификатор базы данных — %d) из-за неразрешенных результатов транзакций. Были подготовлены транзакции координатора распределенных транзакций Майкрософт (MS DTC), но координатору MS DTC не удалось выполнить разрешение. Для разрешения транзакций исправьте MS DTC, выполните восстановление из полной резервной копии или исправьте базу данных.|  
  
## <a name="explanation"></a>Объяснение  
 На момент закрытия базы данных одна или несколько распределенных транзакций, использующих координатор распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC), не были завершены. Восстановление этой базы данных завершилось неуспешно, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось завершить или произвести откат транзакции, не имея дополнительной информации от MS DTC.  
  
## <a name="user-action"></a>Действие пользователя  
 Для восстановления этой базы данных сначала необходимо устранить неполадку с MS DTC. Для поиска проблемы, связанной с MS DTC, просмотрите журналы событий Windows. Если решить проблему с MS DTC и исправить базу данных невозможно, восстановите базу данных из резервной копии.  
  
  
