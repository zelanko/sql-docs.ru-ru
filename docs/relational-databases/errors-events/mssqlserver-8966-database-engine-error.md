---
title: "MSSQLSERVER_8966 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4c93290eaf142f7048458d9e4a18d12bc70e028b
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver8966"></a>MSSQLSERVER_8966
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  

