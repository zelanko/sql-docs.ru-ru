---
title: Были удалены процедуры помощника Web Assistant хранимых | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 958f5d4c-d9c1-4b38-83c3-ebac60e2a9b6
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78711e950eb825ee15e130408f60875972c3f900
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36099714"
---
# <a name="web-assistant-stored-procedures-have-been-removed"></a>Удалены хранимые процедуры помощника Web Assistant
  Помощник по обновлению обнаружил использование хранимых процедур помощника Web Assistant.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Хранимые процедуры помощника Web Assistant **sp_makewebtask**, **sp_dropwebtask**, **sp_runwebtask**и **sp_enumcodepages** отсутствуют.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Вместо нее рекомендуется пользоваться представлением [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
  