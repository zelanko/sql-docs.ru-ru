---
title: MSSQLSERVER_21862 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 70e85924e75469ff37e7b4c9fb7a8305ad386602
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37427953"
---
# <a name="mssqlserver21862"></a>MSSQLSERVER_21862
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|21862|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21862|  
|Текст сообщения|Столбцы FILESTREAM нельзя опубликовать в публикации с использованием метода синхронизации «database snapshot» или «database snapshot character».|  
  
## <a name="explanation"></a>Объяснение  
 Данные FILESTREAM недоступны через моментальный снимок базы данных, поэтому агент моментальных снимков не сможет прочитать данные FILESTREAM, если в качестве метода синхронизации публикации указан параметр *database snapshot* или *database_snapshot_character*.  
  
## <a name="user-action"></a>Действие пользователя  
 Измените метод синхронизации публикации на любой другой, кроме *database snapshot* или *database_snapshot_character*, либо просто исключите столбец FILESTREAM из публикации.  
  
  
