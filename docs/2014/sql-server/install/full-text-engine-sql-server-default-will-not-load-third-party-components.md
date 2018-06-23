---
title: Microsoft полнотекстового поиска для SQL Server не будет загружать неподписанные компоненты сторонних разработчиков по умолчанию | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Full-Text Engine for SQL service
- MSFTESQL service
ms.assetid: 029f9895-7232-4149-9362-3ab1a4133d21
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c66544657e97ed8efcf2ed0dc46dfe21702787a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102349"
---
# <a name="the-microsoft-full-text-engine-for-sql-server-will-not-load-unsigned-third-party-components-by-default"></a>По умолчанию средство полнотекстового поиска (Майкрософт) для SQL Server не загружает компоненты сторонних производителей, не имеющие подписи
  По умолчанию [!INCLUDE[msCoName](../../includes/msconame-md.md)] средство полнотекстового поиска для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не загружает компоненты, которые не были подписаны [!INCLUDE[msCoName](../../includes/msconame-md.md)].  
  
## <a name="component"></a>Компонент  
 Компонент Full-text Search  
  
## <a name="description"></a>Описание  
 Фильтр сторонних разработчиков, например фильтр PDF, установленного на сервере не будет загружен по [!INCLUDE[msCoName](../../includes/msconame-md.md)] средство полнотекстового поиска для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию после обновления.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы загрузить фильтр стороннего, необходимо задать *load_os_resource* и отключить функцию *verify_signature* на этом экземпляре.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  