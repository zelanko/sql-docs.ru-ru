---
title: Обновление вызовет Full-Text Search для использования уровня экземпляра не глобального уровня, по словам и фильтры по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
caps.latest.revision: 17
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 45ee5f8235aa79773bf3e92156701e47092c61c9
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37311224"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>После обновления компонент Full-Text Search будет по умолчанию использовать средства разбиения по словам и фильтры не глобального уровня, а уровня экземпляра
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает регистрацию новых средств разбиения по словам и фильтров на уровне экземпляра.  
  
## <a name="component"></a>Компонент  
 Компонент Full-text Search  
  
## <a name="description"></a>Описание  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет регистрацию новых средств разбиения по словам и фильтров на уровне экземпляра. Регистрация на уровне экземпляра обеспечивает функциональную изоляцию и изоляцию безопасности между экземплярами.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления используйте процедуру `sp_fulltext_service` для определения свойств службы и аргумент `load_os_resources`, разрешающий загрузку компонентов. Необходимо выполнить следующую команду:  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
