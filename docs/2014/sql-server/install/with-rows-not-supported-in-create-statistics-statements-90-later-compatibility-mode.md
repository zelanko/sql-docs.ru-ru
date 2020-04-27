---
title: Если строки не поддерживаются в инструкциях CREATE STATISTICS в режиме совместимости 90 или более поздней версии | Документация Майкрософт
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66090973"
---
# <a name="with-rows-is-not-supported-in-create-statistics-statements-in-the-compatibility-mode-of-90-or-later"></a>Параметр WITH ROWS не поддерживается в инструкциях CREATE STATISTICS в режиме совместимости 90 и выше
  Параметр WITH ROWS в инструкциях CREATE STATISTICS не поддерживается, если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] работает в режиме совместимости 90 и более.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Измените инструкции CREATE STATISTICS, которые включают в себя строки, указав с помощью строк с ВЫБОРкой *чисел* , или указав другие параметры, которые соответствуют задокументированному синтаксису. Дополнительные сведения см. в разделе «CREATE STATISTICS (Transact-SQL)» электронной документации по SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
