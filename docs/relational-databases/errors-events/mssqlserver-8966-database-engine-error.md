---
title: MSSQLSERVER_8966 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8966 (Database Engine error)
ms.assetid: 6b1150fd-9dfd-4df9-8f08-8eca237667db
caps.latest.revision: 17
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2098a91fc02f808750161dffafad84fb56c98fc5
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
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
  
