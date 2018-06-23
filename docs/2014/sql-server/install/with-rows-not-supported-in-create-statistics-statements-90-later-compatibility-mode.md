---
title: СО СТРОКАМИ не поддерживается в инструкциях CREATE STATISTICS в режиме совместимости 90 и выше | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
caps.latest.revision: 21
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9d509352d99cab9359e7ea222f5fb2d5d7e28075
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180174"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Параметр WITH ROWS не поддерживается в инструкциях CREATE STATISTICS в режиме совместимости 90 и выше
  Параметр WITH ROWS в инструкциях CREATE STATISTICS не поддерживается, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в режиме совместимости 90 и более.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Изменение инструкции CREATE STATISTICS, содержащие WITH ROWS, указав WITH SAMPLE *номер* СТРОК, или указав другие параметры, соответствующие документированному синтаксису. Дополнительные сведения см. в разделе «CREATE STATISTICS (Transact-SQL)» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
