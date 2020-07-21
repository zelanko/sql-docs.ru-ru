---
title: MSSQLSERVER_3431 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 12a17a73d0d2fd604b54043ef1f1202efd5ad8f0
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551619"
---
# <a name="mssqlserver_3431"></a>MSSQLSERVER_3431
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3431|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|UNRESOLVED_XACT|  
|Текст сообщения|Не удалось восстановить базу данных «%.*ls» (идентификатор базы данных — %d) из-за неразрешенных результатов транзакций. Были подготовлены транзакции координатора распределенных транзакций Майкрософт (MS DTC), но координатору MS DTC не удалось выполнить разрешение. Для разрешения транзакций исправьте MS DTC, выполните восстановление из полной резервной копии или исправьте базу данных.|  
  
## <a name="explanation"></a>Объяснение  
 На момент закрытия базы данных одна или несколько распределенных транзакций, использующих координатор распределенных транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] (MS DTC), не были завершены. Восстановление этой базы данных завершилось неуспешно, так как [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не удалось завершить или произвести откат транзакции, не имея дополнительной информации от MS DTC.  
  
## <a name="user-action"></a>Действие пользователя  
 Для восстановления этой базы данных сначала необходимо устранить неполадку с MS DTC. Для поиска проблемы, связанной с MS DTC, просмотрите журналы событий Windows. Если решить проблему с MS DTC и исправить базу данных невозможно, восстановите базу данных из резервной копии.  
  
  
