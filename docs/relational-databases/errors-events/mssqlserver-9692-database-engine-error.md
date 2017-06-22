---
title: "MSSQLSERVER_9692 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: 15
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 970733fb1f494b201e0bffa3f88aa27de4465cbf
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9692|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB2_CANT_LISTEN_PORT_IN_USE|  
|Текст сообщения|Транспортному протоколу %S_MSG не удается прослушать порт %d, поскольку он занят другим процессом.|  
  
## <a name="explanation"></a>Объяснение  
Указанный TCP-порт используется другим приложением или компьютером.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните команду **netstat -aon**, чтобы выяснить, какая программа использует порт. Закройте это приложение или укажите другой порт для компонента Service Broker.  
  

