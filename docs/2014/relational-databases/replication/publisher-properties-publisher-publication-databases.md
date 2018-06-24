---
title: Свойства издателя — страница "Базы данных публикации" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 20
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 894d55e77baa9fc0d86e83fe442f2639ea45c559
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195769"
---
# <a name="publisher-properties---publisher-publication-databases"></a>Свойства издателя — издатель, базы данных публикации
  Страница **Базы данных публикации** диалогового окна **Свойства издателя** позволяет пользователю в предопределенной роли сервера **sysadmin** включить базы данных для репликации. Включение базы данных не приводит к публикации базы данных, но позволяет любому пользователю в предопределенной роли базы данных **db_owner** создать одну или несколько публикаций этой базы данных.  
  
## <a name="options"></a>Параметры  
 **Транзакционная**  
 Установите этот флажок, чтобы пользователи в предопределенной роли базы данных **db_owner** могли создавать публикации моментальных снимков или публикации транзакций в базе данных.  
  
 **Объединить**  
 Установите этот флажок, чтобы пользователи в предопределенной роли базы данных **db_owner** могли создавать публикации слиянием в базе данных.  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам (репликация)](properties-reference-replication.md)  
  
  