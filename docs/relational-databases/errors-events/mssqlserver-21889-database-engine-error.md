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
ms.openlocfilehash: 6ff8af9c4abe6f2784f153f8d8346b2609d3197b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780517"
---
# <a name="mssqlserver_21889"></a>MSSQLSERVER_21889
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
