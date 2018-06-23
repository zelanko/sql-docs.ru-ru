---
title: MSSQLSERVER_41302 | Документация Майкрософт
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
- 41302 (Database Engine error)
ms.assetid: 01e75618-afec-4232-ba68-93ab7bc31003
caps.latest.revision: 7
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0a04955a6aa51872362485965fc7f0bd385680bd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101758"
---
# <a name="mssqlserver41302"></a>MSSQLSERVER_41302
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41302|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|WRITE_WRITE_CONFLICT|  
|Текст сообщения|Текущая транзакция попыталась обновить запись, которая была изменена после начала этой транзакции. Транзакция была прервана.|  
  
## <a name="explanation"></a>Объяснение  
 В ходе транзакции произошел конфликт двойной записи, поэтому выполнение инструкции прервано.  
  
## <a name="user-action"></a>Действие пользователя  
 Повторите операцию позже в другой транзакции. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  