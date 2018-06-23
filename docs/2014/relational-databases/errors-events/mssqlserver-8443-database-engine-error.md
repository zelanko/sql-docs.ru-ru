---
title: MSSQLSERVER_8443 | Документация Майкрософт
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
- 8443 (Database Engine error)
ms.assetid: a3541b9c-b1a8-4280-add1-275f08696b62
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d6e7ccc935f09bf69e848ead0a906365eeb5fe2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191960"
---
# <a name="mssqlserver8443"></a>MSSQLSERVER_8443
    
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
  
  