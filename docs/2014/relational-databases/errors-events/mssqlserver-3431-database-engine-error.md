---
title: MSSQLSERVER_3431 | Документация Майкрософт
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
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
caps.latest.revision: 18
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 6bfb835be51887db92b19a13779407fb152f6fab
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109955"
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
  
  