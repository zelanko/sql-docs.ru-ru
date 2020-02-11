---
title: MSSQLSERVER_7911 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7911 (Database Engine error)
ms.assetid: dd8390f3-0f77-4fb2-ba94-631a56e42bc6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dbb5a12fdcb3c326957d719882feec4fe948190c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761849"
---
# <a name="mssqlserver_7911"></a>MSSQLSERVER_7911
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|7911|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_PAGE_DEALLOCATED|  
|Текст сообщения|Исправление: отменено выделение страницы P_ID объекту с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID, идентификатором единицы распределения A_ID (тип TYPE).|  
  
## <a name="explanation"></a>Объяснение  
 Это информационное сообщение инструкции REPAIR, указывающее, что страница была освобождена из карты распределения индекса (IAM)-страницы.  
  
## <a name="user-action"></a>Действие пользователя  
 None  
  
  
