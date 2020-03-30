---
title: MSSQLSERVER_21889 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21889 (Database Engine error)
ms.assetid: ae199540-7986-4cc2-b782-cd22793236d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 177da1486d7cab622bacaea56cd886bd8dc06d06
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "72251489"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21889|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21889|  
|Текст сообщения|Экземпляр SQL Server %s не является издателем репликации. Запустите хранимую процедуру **sp_adddistributor** на экземпляре SQL Server "%s" с распространителем "%s", чтобы разрешить размещение базы данных публикации "%s" на этом экземпляре. Убедитесь, что указаны те же имя входа и пароль, что и на исходном издателе.|  
  
## <a name="explanation"></a>Объяснение  
Для размещения базы данных издателя экземпляр SQL Server должен быть издателем репликации. **sp_validate_redirected_publisher** вызывает **sp_helpdistributor** на удаленном сервере, чтобы определить, является ли сервер издателем репликации. Эта ошибка указывает на то, что целевой экземпляр SQL Server должен быть издателем репликации.  
  
## <a name="user-action"></a>Действие пользователя  
Выполните **sp_adddistributor** на экземпляре SQL Server с размещенной базой данных издателя. При запуске **sp_adddistributor** правильно укажите распространителя. Используйте то же значение параметра *\@password*, которое применялось при начальном запуске хранимой процедуры **sp_adddistributor** на распространителе.  
  
