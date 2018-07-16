---
title: Конфигурация сервера — параметры сортировки | Документация Майкрософт
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
- collation configuration, SQL Server
- collation configuration, Setup
- collation configuration
ms.assetid: e3986870-5be4-458b-b671-5ff12a27b022
caps.latest.revision: 19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: abd57940e3caf8af66cb58fdeceebc802e877f6e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37290180"
---
# <a name="server-configuration---collation"></a>Настройка сервера — параметры сортировки
  На странице «Конфигурация сервера — Параметры сортировки» мастера установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно изменить параметры сортировки, используемые компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] и службами [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Это позволят согласовать параметры сортировки для различных установок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или на разных компьютерах.  
  
## <a name="options"></a>Параметры  
 Настроить для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет две группы параметров сортировки: параметры сортировки Windows и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметры сортировки. Параметры сортировки для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] и служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]могут быть индивидуальными или одинаковыми.  
  
 По умолчанию для англоязычных локалей систем выбираются параметры сортировки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В локализованных версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] параметры сортировки по умолчанию определяются локалью системы Windows для компьютера.  
  
 Параметры по умолчанию следует изменять только в том случае, если настройки параметров сортировки для этого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должны соответствовать настройкам параметров сортировки другого экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или если они должны соответствовать локали системы Windows другого компьютера.  
  
 **Примечание.** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] используют только параметры сортировки Windows. Если планируется установить службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], выберите параметры сортировки Windows во время установки служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , чтобы обеспечить согласованность результатов между [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].  
  
 Дополнительные сведения см. в разделе [Настройка параметров сортировки в программе установки](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
## <a name="best-practices"></a>Рекомендации  
 Дополнительные сведения о таблице языков системы Windows и соответствующих им параметрах сортировки по умолчанию, используемых программой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , см. в разделе [Настройка параметров сортировки в программе установки](http://go.microsoft.com/fwlink/?LinkId=190977).  
  
 По возможности используйте единые параметры сортировки для всей организации. В этом случае не нужно будет явно устанавливать параметры сортировки для каждой базы данных, столбца, выражения или идентификатора. При работе с объектами, имеющими разные параметры сортировки и кодовые страницы, создание запросов должно производиться с учетом правил очередности параметров сортировки. Дополнительные сведения см. в разделе электронной документации [Очередность параметров сортировки (Transact-SQL)](/sql/t-sql/statements/collation-precedence-transact-sql).  
  
 При выборе параметров сортировки для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует придерживаться следующих рекомендаций.  
  
-   Выберите параметры сортировки BINARY2, если допустима двоичная сортировка, основанная на элементах кода.  
  
-   Выберите параметры сортировки Windows для достижения согласованности при сравнении разных типов данных.  
  
-   Используйте новые параметры сортировки уровня 100 для лучшей поддержки лингвистической сортировки. Дополнительные сведения см. в статье [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md).  
  
-   Если планируется перенос базы данных на обновленный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выберите параметры сортировки, которые соответствуют существующим параметрам сортировки базы данных.  
  
  
