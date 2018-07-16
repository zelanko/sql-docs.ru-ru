---
title: Предложение WITH CHECK OPTION не поддерживается в представлениях, содержащих предложение TOP в режиме совместимости 90 и выше | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- TOP clause
- WITH CHECK OPTION clause
ms.assetid: 1b9581d0-bad9-43e0-b8fc-f32d8a8a04ca
caps.latest.revision: 14
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c8c64ce7395b5ecbb33530672d93817f7938db6d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37244002"
---
# <a name="with-check-option-is-not-supported-in-views-that-contain-top-in-90-or-later-compatibility-modes"></a>Предложение WITH CHECK OPTION не поддерживается в представлениях, содержащих предложение TOP, в режиме совместимости 90 и выше
  Помощник по обновлению обнаружил представление, в котором присутствует предложение WITH CHECK OPTION и предложение TOP в инструкции SELECT представления или в представлении, на которое оно ссылается. В режиме совместимости 80 и ниже представления, определенные таким образом, ошибочно позволяют изменять данные через представление и могут выдавать неточные результаты. В режиме совместимости 90 и выше данные не могут вставляться или обновляться через представления с предложением WITH CHECK OPTION, если в этом представлении или представлении, на которое оно ссылается, присутствует предложение TOP.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 При обновлении пользовательские базы данных сохраняют свой режим совместимости. Прежде чем устанавливать режим совместимости базы данных в значение 100 и выше, следует внести изменения в представления, использующие одновременно инструкцию WITH CHECK OPTION и предложение TOP, если необходимо выполнять изменение данных через представление. Дополнительные сведения см. в разделе [sp_dbcmptlevel &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dbcmptlevel-transact-sql).  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
