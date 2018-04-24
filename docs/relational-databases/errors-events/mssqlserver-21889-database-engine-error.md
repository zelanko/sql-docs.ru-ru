---
title: MSSQLSERVER_21889 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
caps.latest.revision: 6
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 425179a083707bb2504e9dc789c0a69aee3399d6
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver21889"></a>MSSQLSERVER_21889
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21889|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21889|  
|Текст сообщения|Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] «%s» не является издателем репликации. Запустите хранимую процедуру **sp_adddistributor** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] '%s' с распространителем '%s', чтобы разрешить размещение базы данных публикации '%s' на этом экземпляре. Убедитесь, что указаны те же имя входа и пароль, что и на исходном издателе.|  
  
## <a name="explanation"></a>Объяснение  
Для размещения базы данных издателя экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен быть издателем репликации. **sp_validate_redirected_publisher** вызывает **sp_helpdistributor** на удаленном сервере, чтобы определить, является ли сервер издателем репликации. Эта ошибка возвращается в том случае, когда хранимая процедура **sp_helpdistributor** сообщает, что целевой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не является издателем репликации.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните **sp_adddistributor** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], на котором расположена база данных издателя. При запуске **sp_adddistributor** правильно укажите распространителя. Используйте то же значение параметра *@password*, которое применялось при начальном запуске хранимой процедуры **sp_adddistributor** на распространителе.  
  
