---
title: MSSQLSERVER_9692 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9692 (Database Engine error)
ms.assetid: 02399d6e-ab5e-4f30-8a3e-2bb1e8c135b5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 91d4f578601710861d4517cc8646f4ff0a6afaf8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741542"
---
# <a name="mssqlserver9692"></a>MSSQLSERVER_9692
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  
