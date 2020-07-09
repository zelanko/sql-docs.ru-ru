---
title: MSSQLSERVER_7920 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7920 (Database Engine error)
ms.assetid: d16290ea-3875-4148-8d53-057bfee00438
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b974fda9619cd3819e79dc608d671c58e95419aa
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85726391"
---
# <a name="mssqlserver_7920"></a>MSSQLSERVER_7920
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7920|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_SUMMARY_ENTRIES|  
|Текст сообщения|Обработанные записи ENTRY_COUNT в системном каталоге для базы данных с идентификатором D_ID.|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение, возвращаемое всеми командами DBCC CHECK, кроме DBCC CHECKALLOC. Возвращаемое значение представляет собой общее количество проверенных наборов строк.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
