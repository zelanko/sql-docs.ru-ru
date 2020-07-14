---
title: MSSQLSERVER_17132 | Документация Майкрософт
description: Компьютер SQL Server не смог обработать пакет входа клиента. См. объяснение ошибки и возможные способы ее устранения.
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17132 (Database Engine error)
ms.assetid: d1d198bd-6730-4394-bd5f-28f320c01a38
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4767ba217eab0d8cdbc6a9dc80f751868322f21f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780849"
---
# <a name="mssqlserver_17132"></a>MSSQLSERVER_17132
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|17132|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|INIT_NODESSPACE|  
|Текст сообщения|Не удалось запустить сервер из-за нехватки памяти для дескриптора. Отмените необязательные операции с памятью или увеличьте объем системной памяти.|  
  
## <a name="explanation"></a>Объяснение  
Не удалось выделить достаточный объем памяти для хранения внутреннего дескриптора сервера.  
  
## <a name="user-action"></a>Действие пользователя  
Увеличьте объем памяти на компьютере. Возможно, окажутся полезными общие шаги по устранению неполадок с памятью.  
  
