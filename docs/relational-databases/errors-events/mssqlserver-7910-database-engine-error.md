---
title: MSSQLSERVER_7910 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2eee9101e3d9d0684b1e2f7cbc28f99777823f33
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85793142"
---
# <a name="mssqlserver_7910"></a>MSSQLSERVER_7910
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7910|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_PAGE_ALLOCATED|  
|Текст сообщения|Исправление: страница P_ID выделена объекту с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID, идентификатором единицы распределения A_ID (тип TYPE).|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение инструкции REPAIR, указывающее, что страница была размещена в карте распределения индекса (IAM)-страницы.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  
