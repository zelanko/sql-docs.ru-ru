---
title: Следующая позиция выборки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fetching rows
- OLE DB rowsets, fetching
- next fetch position
- rowsets [OLE DB], fetching
ms.assetid: 9ef74b3f-c9c0-492f-9b93-d65738a61abd
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c47f1a8692cf7d2e3fb4f00c64770b3b0c69e5a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63183638"
---
# <a name="next-fetch-position"></a>Следующая позиция выборки
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] OLE DB для собственного клиента поставщика отслеживает следующую позицию выборки таким образом, последовательность вызовов **GetNextRows** метода (без пропускает, изменения направления или промежуточных вызовов  **FindNextRow**, **Seek**, или **свойство RestartPosition** методы) считывает набор строк целиком без пропусков или повторение любую строку. Позиция следующей выборки меняется с помощью вызова методов **IRowset::GetNextRows**, **IRowset::RestartPosition** или **IRowsetIndex::Seek** либо вызовом **FindNextRow** со значением *pBookmark*, равным NULL. Вызов **FindNextRow** со значением *pBookmark*, отличным от NULL, не влияет на позицию следующей выборки.  
  
## <a name="see-also"></a>См. также  
 [Выборка строк](fetching-rows.md)  
  
  
