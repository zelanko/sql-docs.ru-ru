---
title: WITH ROWS не поддерживается в инструкциях CREATE STATISTICS в режиме совместимости 90 или более поздней версии | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- WITH ROWS in CREATE STATISTICS statement
ms.assetid: 197b2ecf-a1a3-4a3a-a523-a0ee919c1dde
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e48602f61c09a8de76e2894a4fa808b2f39f4cbe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66090973"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Параметр WITH ROWS не поддерживается в инструкциях CREATE STATISTICS в режиме совместимости 90 и выше
  Параметр WITH ROWS в инструкциях CREATE STATISTICS не поддерживается, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в режиме совместимости 90 и более.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Изменение инструкции CREATE STATISTICS, содержащие параметр WITH ROWS, указав WITH SAMPLE *номер* СТРОК, или указав другие параметры, соответствующие документированному синтаксису. Дополнительные сведения см. в разделе «CREATE STATISTICS (Transact-SQL)» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
