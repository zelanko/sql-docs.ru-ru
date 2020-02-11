---
title: Недопустимое имя именованного канала может препятствовать обновлению | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- invalid named pipes [SQL Server]
- named pipes
ms.assetid: 58c2199c-4fdf-4d43-ac1c-842703344b75
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dddd5da66f09226579a6366baa1a16a6ab00d6bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66094184"
---
# <a name="invalid-named-pipe-name-can-block-upgrade"></a>Неверное имя именованного канала может помешать обновлению
  Обновление завершается ошибкой, если протокол именованных каналов настроен неправильно.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Во время обновления программа установки запускает [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] экземпляр с поддержкой общей памяти, именованным каналом, который принимает только локальные соединения. Если имя канала, указанное на сервере, не является пустым, оно должно начинаться с строки "\\\\.\pipe\\", которая должна быть допустимой. Если задано недопустимое имя канала, компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не запустится и установка завершится ошибкой.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Используйте ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] служебную программу Network** для указания допустимого имени канала, а затем запустите программу установки.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
