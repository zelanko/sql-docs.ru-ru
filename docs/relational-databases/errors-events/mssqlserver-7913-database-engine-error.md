---
title: MSSQLSERVER_7913 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7913 (Database Engine error)
ms.assetid: 9d8ad456-b1a2-4f79-a252-657fbec9ad9b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 286fcd755e970c197785ab1d3ab342013e5dfb86
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85791061"
---
# <a name="mssqlserver_7913"></a>MSSQLSERVER_7913
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7913|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_EXTENT_DEALLOCATED|  
|Текст сообщения|Исправление: выделение экстента P_ID отменено для объекта с идентификатором O_ID, индекса с идентификатором I_ID, секции с идентификатором PN_ID, единицы размещения с идентификатором A_ID (тип TYPE).|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение функции REPAIR, которое означает, что указанный объект был удален из экстента.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
