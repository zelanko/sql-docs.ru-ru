---
title: MSSQLSERVER_9692 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 661d7ab65afca258424af300debde328b8f01fee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62761701"
---
# <a name="mssqlserver_9692"></a>MSSQLSERVER_9692
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9692|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB2_CANT_LISTEN_PORT_IN_USE|  
|Текст сообщения|Транспортному протоколу %S_MSG не удается прослушать порт %d, поскольку он занят другим процессом.|  
  
## <a name="explanation"></a>Объяснение  
 Указанный TCP-порт используется другим приложением или компьютером.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните `netstat -aon` команду, чтобы определить, какая программа использует порт. Закройте это приложение или укажите другой порт для компонента Service Broker.  
  
  
