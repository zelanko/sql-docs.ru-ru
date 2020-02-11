---
title: Обновление приведет к тому, что полнотекстовый поиск будет использовать по умолчанию, а не глобальные, разделители слов и фильтры на уровне экземпляра | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- filters [Full-Text Search]
- word breakers [Full-Text Search]
ms.assetid: 93ee8fcb-d11c-49fa-8fac-51ed31a8f008
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9c81892d6b83cef87a27a836d9691779a841104a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095063"
---
# <a name="upgrading-will-cause-full-text-search-to-use-instance-level-not-global-word-breakers-and-filters-by-default"></a>После обновления компонент Full-Text Search будет по умолчанию использовать средства разбиения по словам и фильтры не глобального уровня, а уровня экземпляра
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обеспечивает регистрацию новых средств разбиения по словам и фильтров на уровне экземпляра.  
  
## <a name="component"></a>Компонент  
 Компонент Full-text Search  
  
## <a name="description"></a>Description  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] позволяет регистрацию новых средств разбиения по словам и фильтров на уровне экземпляра. Регистрация на уровне экземпляра обеспечивает функциональную изоляцию и изоляцию безопасности между экземплярами.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 После обновления используйте процедуру `sp_fulltext_service` для определения свойств службы и аргумент `load_os_resources`, разрешающий загрузку компонентов. Необходимо выполнить следующую команду:  
  
 `sp_fulltext_service 'load_os_resources', 1`  
  
## <a name="see-also"></a>См. также:  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
