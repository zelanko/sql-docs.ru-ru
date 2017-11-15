---
title: "MSSQLSERVER_9692 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
caps.latest.revision: "15"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 2c7e9da124ed3ec2fb1a0725f2f2c3050cd3484f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
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
  
