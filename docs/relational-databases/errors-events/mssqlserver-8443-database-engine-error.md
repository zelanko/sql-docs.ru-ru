---
title: "MSSQLSERVER_8443 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: "16"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ff486acfff1f68078e702ec792ecfc09aba006d5
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8443|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB_DIALOG_WO_CONV_GROUP|  
|Текст сообщения|Диалог с идентификатором "%.*ls" и инициатором %d указывает на несуществующую группу сообщений "%.\*ls". Запустите DBCC CHECKDB для анализа и восстановления базы данных.|  
  
## <a name="explanation"></a>Объяснение  
Для группы сообщений слой метаданных возвратил значение NULL. База данных каким-то образом повреждена. Одним из возможных источников повреждений является ошибка жесткого диска.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите DBCC CHECKDB в режиме исправлений для восстановления базы данных до согласованного состояния. При восстановлении согласованности возможно удаление сообщений. Изучите журналы ошибок системы, чтобы понять, не возникла ли эта ошибка в результате другой неисправности в системе.  
  
