---
title: Удалите вызовы нерекомендуемой команды DBCC CONCURRENCYVIOLATION | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2cc9f6ff-de36-4e94-bd04-59f5c45c4911
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 0110d4bc138ad0da953eb83d3c81ec265d2fd3ba
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66093205"
---
# <a name="remove-calls-to-the-deprecated-dbcc-concurrencyviolation-command"></a>Удаление вызовов устаревшей команды DBCC CONCURRENCYVIOLATION
  Помощник по обновлению обнаружил использование команды DBCC CONCURRENCYVIOLATION. Эта команда больше не доступна. При выполнении данной команды возвращается ошибка 2526.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Описание  
 Регулятор рабочей нагрузки не входит ни в одну из последних версий выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В связи с этим данная команда была удалена.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Внесите изменения в приложения и скрипты, удалив ссылки на эту устаревшую команду.  
  
## <a name="external-resources"></a>Внешние ресурсы  
  
