---
title: MSSQLSERVER_21889 | Документация Майкрософт
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
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 13c7ae116929c0178e9a9b2e0f381574a5cbfd75
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36094772"
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21889|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21889|  
|Текст сообщения|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] «%s» не является издателем репликации. Запустите хранимую процедуру `sp_adddistributor` на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] «%s» с распространителем «%s», чтобы разрешить размещение на данном экземпляре базы данных публикации «%s». Убедитесь, что указаны те же имя входа и пароль, что и на исходном издателе.|  
  
## <a name="explanation"></a>Объяснение  
 Для размещения базы данных издателя экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть издателем репликации. `sp_validate_redirected_publisher` вызывает `sp_helpdistributor` на удаленном сервере, чтобы определить, является ли сервер издателем репликации. Эта ошибка возвращается, если при выполнении хранимой процедуры `sp_helpdistributor` целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не является издателем репликации.  
  
## <a name="user-action"></a>Действие пользователя  
 Выполните `sp_adddistributor` на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором расположена база данных издателя. При запуске `sp_adddistributor` правильно укажите распространителя. Используйте то же значение для *@password* параметра, используемого при `sp_adddistributor` изначально была запущена на распространителе.  
  
  