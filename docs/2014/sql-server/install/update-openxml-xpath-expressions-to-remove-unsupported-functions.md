---
title: Обновление выражений OPENXML XPath для удаления неподдерживаемых функций | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- OPENXML queries
ms.assetid: b459abaf-8787-4b65-9231-ae30e5469fd0
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 2c64408d6d705654014b6d071012001374a5f486
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85041768"
---
# <a name="update-openxml-xpath-expressions-to-remove-unsupported-functions"></a>Обновите выражения XPath OPENXML, удалив неподдерживаемые функции
  Помощник по обновлению обнаружил использование функциональности XPath. Работу некоторых приложений могут затронуть изменения в функциональности XPath для компонентов OPENXML после обновления.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 MSXML 3.0 является теперь базовым обработчиком выражений XPath, используемых в запросах OPENXML. MSXML 3.0 имеет ядро, более строго соответствующее спецификации XPath 1.0, где была отменена поддержка следующих функций:  
  
-   format-number();  
  
-   formatNumber();  
  
-   current();  
  
-   element-available();  
  
-   function-available();  
  
-   system-property().  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Вместо функций format-number() и formatNumber() можно использовать [!INCLUDE[tsql](../../includes/tsql-md.md)]. Для других неподдерживаемых функций, перечисленных ранее, прямой альтернативы нет.  
  
## <a name="see-also"></a>См. также:  
 [Проблемы обновления ядро СУБД](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Советник по переходу SQL Server 2014 &#91;New&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
