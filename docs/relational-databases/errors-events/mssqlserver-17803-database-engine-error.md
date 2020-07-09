---
title: MSSQLSERVER_17803 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac4c4c08c13a700e795ddad0901c0c43829d623f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780741"
---
# <a name="mssqlserver_17803"></a>MSSQLSERVER_17803
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|17803|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_NOMEMORY|  
|Текст сообщения|Во время установления соединения произошла ошибка выделения памяти. Сократите необязательный расход памяти или увеличьте объем системной памяти. Соединение было закрыто.%.*ls|  
  
## <a name="explanation"></a>Объяснение  
Серверу не хватает памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину нехватки памяти на сервере. Возможно, окажутся полезными общие шаги по устранению неполадок с памятью.  
  
