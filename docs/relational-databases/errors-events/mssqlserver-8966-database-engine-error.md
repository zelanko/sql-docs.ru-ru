---
title: "MSSQLSERVER_8966 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: "17"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 58a27246467a9f2ab626f8de626cbcec527743f5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8966|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC3_FAILED_TO_READ_AND_LATCH_PAGE|  
|Текст сообщения|Невозможно прочитать страницу P_ID и заблокировать ее кратковременной блокировкой типа TYPE. Ошибка операции OPERATION.|  
  
## <a name="explanation"></a>Объяснение  
Чтение страницы окончилось неудачей или нельзя было установить кратковременную блокировку на PFS- или GAM-странице. В журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может быть добавлено сообщение об истечении времени ожидания кратковременной блокировки или другие сопутствующие сообщения.  
  
## <a name="user-action"></a>Действие пользователя  
Ознакомьтесь с сопровождающими сообщениями в журнале регистрации ошибок SQL и устраните эти ошибки.  
  
