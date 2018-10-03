---
title: Удаление определяемых пользователем ТИПОВ&#39;s с именем зарезервированными типами данных даты и времени | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- time data type [SQL Server], UDTs
- date data type [SQL Server], UDTs
ms.assetid: 48f109af-b1d1-4f03-a7e3-8a0b05ed94e8
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5471788d3e730c9694ea6394b7e3d1fc659eda96
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48078456"
---
# <a name="remove-udt39s-named-after-the-reserved-date-and-time-data-types"></a>Удаление определяемых пользователем ТИПОВ&#39;s с именем зарезервированными типами данных даты и времени
  Помощник по обновлению обнаружил определяемый пользователем тип, имя которого совпадает с именем, зарезервированным для типа данных `date` или `time`.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Имена терминов, используемых для типов данных, не должны использоваться в качестве имен определяемых пользователем типов среды CLR или их псевдонимов.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Удалите определяемый пользователем тип и создайте его повторно с именем, отличным от зарезервированного.  
  
  
