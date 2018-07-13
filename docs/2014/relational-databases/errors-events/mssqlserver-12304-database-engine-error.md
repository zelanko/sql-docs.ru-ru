---
title: MSSQLSERVER_12304 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
caps.latest.revision: 4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f38066cfe673c68bb77cd0a5f83fa39b988fc4b5
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37421943"
---
# <a name="mssqlserver12304"></a>MSSQLSERVER_12304
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|12304|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Текст сообщения|Использование табличного типа, оптимизированного для памяти, который использует свойство IDENTITY не поддерживается с любым из его столбцов при использовании типа вне контекста изначально компилированной хранимой процедуры.|  
  
## <a name="user-action"></a>Действие пользователя  
 Не используйте тип памяти, оптимизированный для памяти, который использует свойство IDENTITY с любым из его столбцов.  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
