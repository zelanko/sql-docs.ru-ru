---
title: MSSQLSERVER_10737 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: df8a4de014552d3aca00b3eb244f7ff8df56756b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84969754"
---
# <a name="mssqlserver_10737"></a>MSSQLSERVER_10737
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|10737|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Текст сообщения|Если в предложении DATA_COMPRESSION инструкции ALTER TABLE REBUILD или ALTER INDEX REBUILD указана секция, то должно быть задано предложение PARTITION=ALL. Предложение PARTITION=ALL используется для подтверждения того, что должны быть перестроены все секции таблицы или индекса, даже если в предложении DATA_COMPRESSION указано только подмножество.|  
  
## <a name="user-action"></a>Действие пользователя  
 Добавьте предложение PARTITION=ALL к инструкции ALTER INDEX или ALTER TABLE. Или, чтобы перестроить определенную секцию, используйте перестроение секции = \<partition-number-expr> with (DATA_COMPRESSION = {on | OFF}).  
  
  
