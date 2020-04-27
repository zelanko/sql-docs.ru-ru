---
title: Изменения в поведении флагов трассировки | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- trace flags [SQL Server], behavior changes
ms.assetid: d739df96-2659-4383-8e10-194657632526
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 447e6d4d35fa77f71f1a7a1b90a5a782e0ccebcc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096623"
---
# <a name="changes-to-behavior-of-trace-flags"></a>Изменения в поведении флагов трассировки
  Глобальные флаги трассировки, установленные сеансом, немедленно учитываются в других сеансах. Некоторые флаги трассировки [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] отсутствуют в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Рекомендуется отключить все флаги трассировки перед началом обновления. Флаги трассировки, которые изменяют режимы доступности базы данных или [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] восстановления, могут препятствовать успешному [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]обновлению экземпляра. Включить эти флаги трассировки можно будет после проверки того, что они необходимы и по-прежнему допустимы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Если необходимо повторно включить флаги трассировки, то нужно выполнить дополнительную проверку экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] поддерживает флаги трассировки на глобальном уровне и уровне сеанса. В [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] флаги трассировки могут быть объявлены как локальные либо глобальные при помощи дополнительного аргумента (-1) команды DBCC TRACEON. Если этот аргумент не указан, по умолчанию флаги объявляются как локальные.  
  
 Кроме того, в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] флаг трассировки, установленный в сеансе А, не будет автоматически воздействовать на уже существующий сеанс Б. Вместо этого данный флаг трассировки вступит в силу только после первой установки любого флага трассировки в сеансе Б. Такое поведение является недетерминированным в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] и детерминированным в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версиях, в которых глобальные флаги трассировки, установленные в сеансе А, немедленно устанавливаются во всех параллельных сеансах.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
