---
title: Средство полнотекстового поиска (Майкрософт) для SQL Server не будет загружать сторонние компоненты без знака по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fe7f1359b55f2a488a58c37b9f3045a31dbc0778
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095158"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>По умолчанию средство полнотекстового поиска (Майкрософт) для SQL Server не загружает компоненты сторонних производителей, не имеющие подписи
  По умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] средство полнотекстового поиска для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не будет загружать компоненты, которые не подписаны. [!INCLUDE[msCoName](../../includes/msconame-md.md)]  
  
## <a name="component"></a>Компонент  
 Компонент Full-text Search  
  
## <a name="description"></a>Description  
 Сторонний фильтр, например фильтр в формате PDF, установленный на сервере, не будет загружен средством [!INCLUDE[msCoName](../../includes/msconame-md.md)] полнотекстового [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поиска по умолчанию после обновления.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы загрузить фильтр стороннего производителя, необходимо задать *load_os_resource* и отключить *verify_signature* на этом экземпляре.  
  
## <a name="see-also"></a>См. также:  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
