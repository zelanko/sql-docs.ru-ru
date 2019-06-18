---
title: MSSQLSERVER_7916 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7916 (Database Engine error)
ms.assetid: 9bac3536-de14-4e98-84c2-bde9a59ba0d1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0eda0980b3b8ffbc748f15933ea397ae3d0b71e8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62913418"
---
# <a name="mssqlserver7916"></a>MSSQLSERVER_7916
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7916|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_RECORD_DELETED|  
|Текст сообщения|Исправление: Удалена запись для объекта с Идентификатором O_ID, Идентификатором индекса I_ID, Идентификатором секции PN_ID, Идентификатором единицы распределения A_ID (тип TYPE), на странице P_ID, область памяти S_ID. Индексы будут перестроены.|  
  
## <a name="explanation"></a>Объяснение  
 Данное информационное сообщение отправлено функцией REPAIR и означает, что указанная запись была удалена со страницы.  
  
## <a name="user-action"></a>Действие пользователя  
 None  
  
  
